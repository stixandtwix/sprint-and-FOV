local player = game.Players.LocalPlayer
local camera = game.Workspace.CurrentCamera

local shiftPressed = false

local function onKeyPress(input)
    if input.KeyCode == Enum.KeyCode.LeftShift or input.KeyCode == Enum.KeyCode.RightShift then
        shiftPressed = true
        camera.FieldOfView = camera.FieldOfView * 0.75 -- Reduce camera FOV by 25%
        player.Character.Humanoid.WalkSpeed = player.Character.Humanoid.WalkSpeed * 1.5 -- Boost walkspeed by 50%
    end
end


local function onKeyRelease(input)
    if input.KeyCode == Enum.KeyCode.LeftShift or input.KeyCode == Enum.KeyCode.RightShift then
        shiftPressed = false
        camera.FieldOfView = camera.FieldOfView / 0.75 -- Reset camera FOV to default
        player.Character.Humanoid.WalkSpeed = player.Character.Humanoid.WalkSpeed / 1.5 -- Reset walkspeed to default
    end
end


game:GetService("UserInputService").InputBegan:Connect(onKeyPress)
game:GetService("UserInputService").InputEnded:Connect(onKeyRelease)
