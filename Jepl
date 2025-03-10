-- GUI Setup
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
local FlyButton = Instance.new("TextButton")
local AutoParryButton = Instance.new("TextButton")
local AutoCurveButton = Instance.new("TextButton")
local ManualSpamButton = Instance.new("TextButton")

ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
Frame.Position = UDim2.new(0.8, 0, 0.3, 0)
Frame.Size = UDim2.new(0, 200, 0, 200)

local function createButton(name, text, position)
    local button = Instance.new("TextButton")
    button.Parent = Frame
    button.Text = text
    button.Size = UDim2.new(0, 180, 0, 40)
    button.Position = UDim2.new(0, 10, 0, position)
    button.BackgroundColor3 = Color3.fromRGB(100, 100, 100)
    button.TextColor3 = Color3.fromRGB(255, 255, 255)
    return button
end

FlyButton = createButton("FlyButton", "Hold Jump to Fly", 10)
AutoParryButton = createButton("AutoParry", "Toggle Auto Parry", 60)
AutoCurveButton = createButton("AutoCurve", "Toggle Auto Curve", 110)
ManualSpamButton = createButton("ManualSpam", "Manual Spam", 160)

-- Hold Jump to Fly
local flying = false
local user = game.Players.LocalPlayer
local character = user.Character or user.CharacterAdded:Wait()
local humanoid = character:FindFirstChildOfClass("Humanoid")

local function fly()
    if not flying then
        flying = true
        while flying do
            character.HumanoidRootPart.Velocity = Vector3.new(0, 50, 0)
            wait(0.1)
        end
    end
end

local function stopFly()
    flying = false
end

user.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Keyboard and input.KeyCode == Enum.KeyCode.Space then
        fly()
    end
end)

user.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.Keyboard and input.KeyCode == Enum.KeyCode.Space then
        stopFly()
    end
end)

-- Auto Parry for Blade Ball
local autoParry = false

local function toggleAutoParry()
    autoParry = not autoParry
    AutoParryButton.Text = autoParry and "Auto Parry: ON" or "Auto Parry: OFF"

    while autoParry do
        local bladeBall = game.Workspace:FindFirstChild("BladeBall")
        if bladeBall and (bladeBall.Position - character.HumanoidRootPart.Position).Magnitude < 10 then
            humanoid:Move(Vector3.new(0, 0, -5), true) -- Dodge back
        end
        wait(0.1)
    end
end

AutoParryButton.MouseButton1Click:Connect(toggleAutoParry)

-- Auto Curve Feature
local autoCurve = false

local function toggleAutoCurve()
    autoCurve = not autoCurve
    AutoCurveButton.Text = autoCurve and "Auto Curve: ON" or "Auto Curve: OFF"

    while autoCurve do
        humanoid:Move(Vector3.new(math.random(-3,3), 0, math.random(-3,3)), true)
        wait(0.5)
    end
end

AutoCurveButton.MouseButton1Click:Connect(toggleAutoCurve)

-- Manual Spam Feature
local function manualSpam()
    for i = 1, 5 do
        humanoid:Move(Vector3.new(math.random(-3,3), 0, math.random(-3,3)), true)
        wait(0.1)
    end
end

ManualSpamButton.MouseButton1Click:Connect(manualSpam)

print("Script Loaded Successfully!")
