loadstring([[ 
-- // Rayfield UI Script - Ryu Ishigori Game
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
    Name = "Ryu Ishigori Game | Script",
    LoadingTitle = "Carregando...",
    LoadingSubtitle = "by Grok",
    ConfigurationSaving = {
        Enabled = true,
        FolderName = "RyuIshigoriScript",
        FileName = "Config"
    }
})

-- ==================== ABA BUY ====================
local BuyTab = Window:CreateTab("Buy", 4483362458)

-- Rebirth
BuyTab:CreateToggle({
    Name = "Rebirth",
    CurrentValue = false,
    Flag = "RebirthToggle",
    Callback = function(Value)
        getgenv().AutoRebirth = Value
        while getgenv().AutoRebirth do
            local args = { [1] = "REBIRTH" }
            game:GetService("ReplicatedStorage").RebirthRE:FireServer(unpack(args))
            wait(1)
        end
    end,
})

-- Buy Larp Gain
BuyTab:CreateToggle({
    Name = "Buy Larp Gain",
    CurrentValue = false,
    Flag = "BuyLarpGainToggle",
    Callback = function(Value)
        getgenv().AutoBuyLarpGain = Value
        while getgenv().AutoBuyLarpGain do
            local args = { [1] = "LarpGain", [2] = true }
            game:GetService("ReplicatedStorage").ShopRE:FireServer(unpack(args))
            wait(0.5)
        end
    end,
})

-- Buy Larp Cp (Output)
BuyTab:CreateToggle({
    Name = "Buy Larp Cp",
    CurrentValue = false,
    Flag = "BuyLarpCpToggle",
    Callback = function(Value)
        getgenv().AutoBuyLarpCp = Value
        while getgenv().AutoBuyLarpCp do
            local args = { [1] = "Output", [2] = true }
            game:GetService("ReplicatedStorage").ShopRE:FireServer(unpack(args))
            wait(0.5)
        end
    end,
})

-- ==================== ABA AUTOLARP ====================
local AutoTab = Window:CreateTab("AutoLarp", 4483362458)

-- Auto Larp
AutoTab:CreateToggle({
    Name = "Auto Larp",
    CurrentValue = false,
    Flag = "AutoLarpToggle",
    Callback = function(Value)
        getgenv().AutoLarp = Value
        while getgenv().AutoLarp do
            local args = {
                [1] = CFrame.new(11.184737205505371, 3.9999988079071045, -36.259586334228516) 
                    * CFrame.Angles(-0, -1.4910603761672974, -0)
            }
            game:GetService("ReplicatedStorage").LarpRE:FireServer(unpack(args))
            wait(0.3)
        end
    end,
})

-- Anti AFK
AutoTab:CreateToggle({
    Name = "Anti Afk",
    CurrentValue = true,
    Flag = "AntiAfkToggle",
    Callback = function(Value)
        if Value then
            local vu = game:GetService("VirtualUser")
            game:GetService("Players").LocalPlayer.Idled:Connect(function()
                vu:Button2Down(Vector2.new(0,0), workspace.CurrentCamera.CFrame)
                wait(1)
                vu:Button2Up(Vector2.new(0,0), workspace.CurrentCamera.CFrame)
            end)
            Rayfield:Notify({
                Title = "Anti Afk",
                Content = "Anti Afk ativado! Você não será expulso por inatividade.",
                Duration = 5,
                Image = 4483362458,
            })
        end
    end,
})

Rayfield:Notify({
    Title = "Script Carregado!",
    Content = "Divirta-se no Ryu Ishigori Game",
    Duration = 6,
    Image = 4483362458,
})
]])()
