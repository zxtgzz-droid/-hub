local WindUI = loadstring(game:HttpGet(
"https://raw.githubusercontent.com/Footagesus/WindUI/main/dist/main.lua"
))()

getgenv().AutoSummon = false
getgenv().SummonMode = "Summon 10"

local Remote = game:GetService("ReplicatedStorage")
    :WaitForChild("NetworkingContainer")
    :WaitForChild("DataRemote")

local SummonArgs = {
    ["Summon 1"] = {
        {
            {
                "\226\129\130>"
            }
        }
    },
    ["Summon 10"] = {
        {
            {
                "\226\129\130?"
            }
        }
    }
}

local Window = WindUI:CreateWindow({
    Title = "мсто",
    Icon = "eye",
    Folder = "TTD"
})

local Main = Window:Tab({
    Title = "Main",
    Icon = "gamepad-2"
})

Main:Dropdown({
    Title = "Select Summon",
    Values = {
        "Summon 1",
        "Summon 10"
    },
    Default = "Summon 10",
    Callback = function(v)
        getgenv().SummonMode = v
    end
})

Main:Toggle({
    Title = "Start Auto Summon",
    Default = false,
    Callback = function(v)
        getgenv().AutoSummon = v
    end
})

local Settings = Window:Tab({
    Title = "Settings",
    Icon = "settings"
})

Settings:Button({
    Title = "Destroy UI",
    Callback = function()
        Window:Destroy()
    end
})

task.spawn(function()
    while true do
        if getgenv().AutoSummon then
            pcall(function()
                Remote:FireServer(
                    unpack(
                        SummonArgs[
                            getgenv().SummonMode
                        ]
                    )
                )
            end)
            -- รอให้ animation summon เล่นจบก่อน
            if getgenv().SummonMode == "Summon 10" then
                task.wait(3)
            else
                task.wait(1.5)
            end
        else
            task.wait(0.1)
        end
    end
end)
