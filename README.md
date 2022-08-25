--Hats for the script
--https://www.roblox.com/catalog/4739580137/Oversized-Hammer-of-the-Titans
--https://www.roblox.com/catalog/48474313/Red-Roblox-Cap
--
local Character = game:FindFirstChildOfClass("Players").LocalPlayer["Character"]
Character.Robloxclassicred.Handle.Mesh:Destroy()
for i,v in next, game:GetService("Players").LocalPlayer.Character:GetDescendants() do
 if v:IsA("BasePart") and v.Name ~="HumanoidRootPart" then 
 game:GetService("RunService").Heartbeat:connect(function()
 v.Velocity = Vector3.new(14.5,14.3,14.5)
 end)
 game:GetService("RunService").Heartbeat:connect(function()
 v.Velocity = Vector3.new(-14.3,-14.3,-14.3)
 end)
 end
 end
------

local CountSCIFIMOVIELOL = 1
function SCIFIMOVIELOL(Part0,Part1,Position,Angle)
 local AlignPos = Instance.new('AlignPosition', Part1); AlignPos.Name = "AP"
 AlignPos.ApplyAtCenterOfMass = true;
 AlignPos.MaxForce = 999999999999--67752;
 AlignPos.MaxVelocity = math.huge/9e110;
 AlignPos.ReactionForceEnabled = false;
 AlignPos.Responsiveness = 200;
 AlignPos.RigidityEnabled = true;
 local AlignOri = Instance.new('AlignOrientation', Part1); AlignOri.Name = "AO"
 AlignOri.MaxAngularVelocity = math.huge/9e110;
 AlignOri.MaxTorque = 999999999999
 AlignOri.PrimaryAxisOnly = false;
 AlignOri.ReactionTorqueEnabled = false;
 AlignOri.Responsiveness = 200;
 AlignOri.RigidityEnabled = false;
 local AttachmentA=Instance.new('Attachment',Part1); AttachmentA.Name = "AccessoryWeld"
 local AttachmentB=Instance.new('Attachment',Part0); AttachmentB.Name = "AccessoryWeld"
 AttachmentA.Orientation = Angle or Vector3.new(0,0,0)
 AttachmentA.Position = Position or Vector3.new(0,0,0)
 AlignPos.Attachment1 = AttachmentA;
 AlignPos.Attachment0 = AttachmentB;
 AlignOri.Attachment1 = AttachmentA;
 AlignOri.Attachment0 = AttachmentB;
 CountSCIFIMOVIELOL = CountSCIFIMOVIELOL + 1
 return {AlignPos,AlignOri,AttachmentA,AttachmentB}
end

if _G.netted ~= true then
 _G.netted = true
 coroutine.wrap(function()
  settings().Physics.PhysicsEnvironmentalThrottle = Enum.EnviromentalPhysicsThrottle.Disabled
  settings().Physics.AllowSleep = false
  game:GetService("RunService").RenderStepped:Connect(function()
   game:FindFirstChildOfClass("Players").LocalPlayer.MaximumSimulationRadius=math.pow(math.huge,math.huge)
   sethiddenproperty(game:FindFirstChildOfClass("Players").LocalPlayer,"SimulationRadius",math.huge*math.huge)
  end)
 end)()
end

game:FindFirstChildOfClass("Players").LocalPlayer["Character"].Archivable = true
local hatnameclone = {}
for _,v in next, game:FindFirstChildOfClass("Players").LocalPlayer["Character"]:GetChildren() do
 if v:IsA("Accessory") then
  if hatnameclone[v.Name] then
   if hatnameclone[v.Name] == "s" then
    hatnameclone[v.Name] = {}
   end
   table.insert(hatnameclone[v.Name],v)
  else
   hatnameclone[v.Name] = "s"
  end
 end
end
for _,v in pairs(hatnameclone) do
 if type(v) == "table" then
  local num = 1
  for _,w in pairs(v) do
   w.Name = w.Name..num
   num = num + 1
  end
 end
end
hatnameclone = nil

local DeadChar = game:FindFirstChildOfClass("Players").LocalPlayer.Character

local fldr = Instance.new("Folder",game:FindFirstChildOfClass("Players").LocalPlayer["Character"])
fldr.Name = "DMYF"
local CloneChar = DeadChar:Clone()
local ANIMATIONHERE
if CloneChar:FindFirstChild("Animate") then
 ANIMATIONHERE = CloneChar:FindFirstChild("Animate"):Clone()
 CloneChar:FindFirstChild("Animate"):Destroy()
end
if CloneChar:FindFirstChildOfClass("Folder") then CloneChar:FindFirstChildOfClass("Folder"):Destroy() end
if CloneChar.Torso:FindFirstChild("Neck") then
 local Clonessss = CloneChar.Torso:FindFirstChild("Neck"):Clone()
 Clonessss.Part0 = nil
 Clonessss.Part1 = DeadChar.Head
 Clonessss.Parent = DeadChar.Torso
end
CloneChar.Parent = fldr
CloneChar.HumanoidRootPart.CFrame = DeadChar.HumanoidRootPart.CFrame
CloneChar.Humanoid.BreakJointsOnDeath = false
CloneChar.Name = "non"
CloneChar.Humanoid.DisplayDistanceType = "None"

for _,v in next, DeadChar:GetChildren() do
 if v:IsA("Accessory") then
  local topacc = false
  if v.Handle:FindFirstChildOfClass("Weld") then v.Handle:FindFirstChildOfClass("Weld"):Destroy() end
  v.Handle.Massless = true
  v.Handle.CanCollide = false
  if v.Handle:FindFirstChildOfClass("Attachment") then
   local ath__ = v.Handle:FindFirstChildOfClass("Attachment")
   if ath__.Name == "HatAttachment" or ath__.Name == "HairAttachment" or ath__.Name == "FaceFrontAttachment" or ath__.Name == "FaceCenterAttachment" then
    topacc = ath__.Name
   end
  end
        local bv = Instance.new("BodyVelocity",v.Handle)
  bv.Velocity = Vector3.new(0,0,0)
  coroutine.wrap(function()
   if topacc then
    local allthings = SCIFIMOVIELOL(v.Handle,DeadChar.Torso,Vector3.new(0,1.5,0)+ (DeadChar.Head[topacc].Position + (v.Handle[topacc].Position*-1)),Vector3.new(0,0,0))
    local normaltop = allthings[1].Attachment1
    local alipos = allthings[1]
    local alirot = allthings[2]
    local p0 = v.Handle
    local p1 = DeadChar.Head
    alipos.Parent = CloneChar:FindFirstChild(v.Name).Handle
    alirot.Parent = CloneChar:FindFirstChild(v.Name).Handle
    while true do
     game:GetService("RunService").RenderStepped:wait()
     if HumanDied then break end
     coroutine.wrap(function()
      if alipos.Attachment1 == normaltop then
       p0.CFrame = p0.CFrame:lerp((((DeadChar.Torso.CFrame * CFrame.new(0,1.5,0)) * p1[topacc].CFrame) * p0[topacc].CFrame:inverse()),1)
      else
       v.Handle.CFrame = v.Handle.CFrame:lerp(alipos.Attachment1.Parent.CFrame * CFrame.new(alipos.Attachment1.Position) * CFrame.Angles(math.rad(alipos.Attachment1.Rotation.X),math.rad(alipos.Attachment1.Rotation.Y),math.rad(alipos.Attachment1.Rotation.Z)),1)
      end
     end)()
    end
   else
    SCIFIMOVIELOL(v.Handle,CloneChar[v.Name].Handle,Vector3.new(0,0,0),Vector3.new(0,0,0))
   end
  end)()
    end
end

local a = DeadChar.Torso
local b = DeadChar.HumanoidRootPart
local c = DeadChar.Humanoid
a.Parent = game:FindFirstChildOfClass("Workspace")
c.Parent = game:FindFirstChildOfClass("Workspace")
local told = a:Clone()
local told1 = c:Clone()
b["RootJoint"].Part0 = told
b["RootJoint"].Part1 = DeadChar.Head
a.Name = "torso"
a.Neck:Destroy()
c.Name = "Humanoid"
told.Parent = DeadChar
told1.Parent = DeadChar
DeadChar.PrimaryPart = told
told1.Health = 0
b:Destroy()
a.Parent = DeadChar
c.Parent = DeadChar
told:Destroy()
told1:Destroy()
a.Name = "Torso"

if CloneChar.Head:FindFirstChildOfClass("Decal") then CloneChar.Head:FindFirstChildOfClass("Decal").Transparency = 1 end
if DeadChar:FindFirstChild("Animate") then DeadChar:FindFirstChild("Animate"):Destroy() end

local Collider
function UnCollide()
    if HumanDied then Collider:Disconnect(); return end
    --[[for _,Parts in next, CloneChar:GetChildren() do
        if Parts:IsA("BasePart") then
            Parts.CanCollide = false 
        end 
    end]]
    for _,Parts in next, DeadChar:GetChildren() do
        if Parts:IsA("BasePart") then
        Parts.CanCollide = false
        end 
    end 
end
Collider = game:GetService("RunService").Stepped:Connect(UnCollide)

local resetBindable = Instance.new("BindableEvent")
resetBindable.Event:connect(function()
    game:GetService("StarterGui"):SetCore("ResetButtonCallback", true)
 resetBindable:Clone()
 HumanDied = true
    pcall(function()
  game:FindFirstChildOfClass("Players").LocalPlayer.Character = DeadChar
  DeadChar.Head:Destroy()
  DeadChar:FindFirstChildOfClass("Humanoid"):Destroy()
  game:FindFirstChildOfClass("Players").LocalPlayer.Character = CloneChar
  if DeadChar:FindFirstChildOfClass("Folder") then DeadChar:FindFirstChildOfClass("Folder"):Destroy() end
 end)
end)
game:GetService("StarterGui"):SetCore("ResetButtonCallback", resetBindable)

coroutine.wrap(function()
    while true do
        game:GetService("RunService").RenderStepped:wait()
        if not CloneChar or not CloneChar:FindFirstChild("Head") or not CloneChar:FindFirstChildOfClass("Humanoid") or CloneChar:FindFirstChildOfClass("Humanoid").Health &lt;= 0 and not DeadChar or not DeadChar:FindFirstChild("Head") or not DeadChar:FindFirstChildOfClass("Humanoid") or DeadChar:FindFirstChildOfClass("Humanoid").Health &lt;= 0 then 
            HumanDied = true
            pcall(function()
    game:FindFirstChildOfClass("Players").LocalPlayer.Character = DeadChar
    DeadChar.Head:Destroy()
    DeadChar:FindFirstChildOfClass("Humanoid"):Destroy()
    game:FindFirstChildOfClass("Players").LocalPlayer.Character = CloneChar
    if DeadChar:FindFirstChildOfClass("Folder") then DeadChar:FindFirstChildOfClass("Folder"):Destroy() end
   end)
            if resetBindable then
                game:GetService("StarterGui"):SetCore("ResetButtonCallback", true)
                resetBindable:Destroy()
            end
            break
        end  
    end
end)()


SCIFIMOVIELOL(DeadChar["Head"],CloneChar["Head"])
SCIFIMOVIELOL(DeadChar["Torso"],CloneChar["Torso"])
SCIFIMOVIELOL(DeadChar["Left Arm"],CloneChar["Left Arm"])
SCIFIMOVIELOL(DeadChar["Right Arm"],CloneChar["Right Arm"])
SCIFIMOVIELOL(DeadChar["Left Leg"],CloneChar["Left Leg"])
SCIFIMOVIELOL(DeadChar["Right Leg"],CloneChar["Right Leg"])

for _,v in pairs(DeadChar:GetChildren()) do
 if v:IsA("BasePart") and v.Name ~= "Head" then
  --[[local bv = Instance.new("BodyVelocity",v)
  bv.Velocity = Vector3.new(0,0,0)
  coroutine.wrap(function()
   while true do
    game:GetService("RunService").RenderStepped:wait()
    if HumanDied then break end
    v.CFrame = CloneChar[v.Name].CFrame
   end
  end)()]]
 elseif v:IsA("BasePart") and v.Name == "Head" then
  local bv = Instance.new("BodyVelocity",v)
  bv.Velocity = Vector3.new(0,0,0)
  coroutine.wrap(function()
   while true do
    game:GetService("RunService").RenderStepped:wait()
    if HumanDied then break end
    v.CFrame = DeadChar.Torso.CFrame * CFrame.new(0,1.5,0)
   end
  end)()
 end
end

for _,BodyParts in next, CloneChar:GetDescendants() do
if BodyParts:IsA("BasePart") or BodyParts:IsA("Part") then
BodyParts.Transparency = 1 end end
game:GetService("RunService").RenderStepped:wait()
game:FindFirstChildOfClass("Players").LocalPlayer.Character = CloneChar
game:FindFirstChildOfClass("Workspace"):FindFirstChildOfClass("Camera").CameraSubject = CloneChar.Humanoid

for _,v in next, DeadChar:GetChildren() do
 if v:IsA("Accessory") then
  if v.Handle:FindFirstChildOfClass("Weld") then v.Handle:FindFirstChildOfClass("Weld"):Destroy() end
 end
end

if ANIMATIONHERE then ANIMATIONHERE.Parent = CloneChar end
-------
Character.Humanoid:ChangeState(16)
local function align(i,v)
 local att0 = Instance.new("Attachment", i)
 att0.Position = Vector3.new(0,0,0)
 local att1 = Instance.new("Attachment", v)
 att1.Position = Vector3.new(0,0,0)
 local AP = Instance.new("AlignPosition", i)
 AP.Attachment0 = att0
 AP.Attachment1 = att1
 AP.RigidityEnabled = false
 AP.ReactionForceEnabled = false
 AP.ApplyAtCenterOfMass = true
 AP.MaxForce = 9e9
 AP.MaxVelocity = math.huge
 AP.Responsiveness = 200
 local AO = Instance.new("AlignOrientation", i)
 AO.Attachment0 = att0
 AO.Attachment1 = att1
 AO.ReactionTorqueEnabled = false
 AO.PrimaryAxisOnly = false
 AO.MaxTorque = 9e9
 AO.MaxAngularVelocity = math.huge
 AO.Responsiveness = 200
end

local function alignbroke(i,v)
 local att0 = Instance.new("Attachment", i)
 att0.Position = Vector3.new(0,0,0)
 local att1 = Instance.new("Attachment", v)
 att1.Position = Vector3.new(0,0,0)
 local AP = Instance.new("AlignPosition", i)
 AP.Attachment0 = att0
 AP.Attachment1 = att1
 AP.RigidityEnabled = false
 AP.ReactionForceEnabled = false
 AP.ApplyAtCenterOfMass = true
 AP.MaxForce = 9e9
 AP.MaxVelocity = math.huge
 AP.Responsiveness = 200
 local AO = Instance.new("AlignOrientation", i)
 AO.Attachment0 = att0
 AO.Attachment1 = att1
 AO.ReactionTorqueEnabled = false
 AO.PrimaryAxisOnly = false
 AO.MaxTorque = 9e9
 AO.MaxAngularVelocity = math.huge
 AO.Responsiveness = 200
end

local Hats = {
 Main = Character["MARTILLO"],
}

local Hats2 = {
 MainShit = Character["Robloxclassicred"]
}
local H = Hats.Main.Handle
local HH = Hats2.MainShit.Handle

local plr = game.Players.LocalPlayer
local flingo = game.workspace[plr.Name].Torso
local Debris = game:GetService("Debris")
local char = plr.Character


function insertfling()
    coroutine.resume(coroutine.create(function()
 local a = Instance.new("BodyAngularVelocity")
 a.MaxTorque = Vector3.new(999999999999999999999999999999999999,999999999999999999999999999999999999,999999999999999999999999999999999999)
 a.P = 999999999999999999999999999999999999
 a.AngularVelocity = Vector3.new(999999999,999999999,999999999)
 a.Parent = flingo
 wait(0.15)
 a:Destroy()
    end))
 end
 
 function idlefling()
  local a = Instance.new("BodyAngularVelocity")
  a.MaxTorque = Vector3.new(999999999999999999999999999999999999,999999999999999999999999999999999999,999999999999999999999999999999999999)
  a.P = 999999999999999999999999999999999999
  a.AngularVelocity = Vector3.new(90000,90000,90000)
  a.Parent = flingo
  debris:AddItem(a,0.00000000001)
 end
 
 game.Players.LocalPlayer.Character.Torso.AP.RigidityEnabled = false
 game.Players.LocalPlayer.Character.Torso.AP.MaxForce = 999999999999
 game.Players.LocalPlayer.Character.Torso.AO.RigidityEnabled = false
 game.Players.LocalPlayer.Character.Torso.AO.MaxTorque = 999999999999

 game.Players.LocalPlayer.Character["Right Arm"].AP.RigidityEnabled = false
 game.Players.LocalPlayer.Character["Right Arm"].AP.MaxForce = 999999999999
 game.Players.LocalPlayer.Character["Right Arm"].AO.RigidityEnabled = false
 game.Players.LocalPlayer.Character["Right Arm"].AO.MaxTorque = 999999999999

 game.Players.LocalPlayer.Character["Left Arm"].AP.RigidityEnabled = false
 game.Players.LocalPlayer.Character["Left Arm"].AP.MaxForce = 999999999999
 game.Players.LocalPlayer.Character["Left Arm"].AO.RigidityEnabled = false
 game.Players.LocalPlayer.Character["Left Arm"].AO.MaxTorque = 999999999999
 
 game.Players.LocalPlayer.Character["Right Leg"].AP.RigidityEnabled = false
 game.Players.LocalPlayer.Character["Right Leg"].AP.MaxForce = 999999999999
 game.Players.LocalPlayer.Character["Right Leg"].AO.RigidityEnabled = false
 game.Players.LocalPlayer.Character["Right Leg"].AO.MaxTorque = 999999999999

 game.Players.LocalPlayer.Character["Left Leg"].AP.RigidityEnabled = false
 game.Players.LocalPlayer.Character["Left Leg"].AP.MaxForce = 999999999999
 game.Players.LocalPlayer.Character["Left Leg"].AO.RigidityEnabled = false
 game.Players.LocalPlayer.Character["Left Leg"].AO.MaxTorque = 999999999999
 
 for _,v in pairs(Character:GetDescendants()) do
  if  v:IsA("AlignPosition") and v.Parent.Parent:IsA("Accessory") and v.Parent.Parent.Name ~= "MARTILLO" and v.Parent.Parent.Name ~= "Robloxclassicred" then
   v.Enabled = false
   v.Parent.AccessoryWeld:Destroy()
 end
 
end
----
Player=game.Players.LocalPlayer
Character=Player.Character
hum = Character.Humanoid
LeftArm=Character["Left Arm"]
LeftLeg=Character["Left Leg"]
RightArm=Character["Right Arm"]
RightLeg=Character["Right Leg"]
Root=Character["HumanoidRootPart"]
Head=Character["Head"]
Torso=Character["Torso"]
Neck=Torso["Neck"]
walking = false
attacking = false
tauntdebounce = false
themeallow = true
secondform = false
position = nil
MseGuide = true
equipping = false
settime = 0
sine = 0
ws = 16
change = 1
dgs = 75
RunSrv = game:GetService("RunService")
RenderStepped = game:GetService("RunService").RenderStepped
removeuseless = game:GetService("Debris")
smoothen = game:GetService("TweenService")
cam = workspace.CurrentCamera
local armorparts = {}
local dmt2 = {3183433131,720696725,3420696180,1588071502,779838221,2635411911}
combo1 = true
combo2 = false
combo3 = false
combo4 = false
local bloodfolder = Instance.new("Folder",Torso)
local tauntable = {3493125551,3493128152,3493130715,3493305976,3493316200,3493334982,3493370895,3493372969,3493382339,3493384428}
local killable = {3493244407,3493249574,3493297656,3493301150,3493312467,3493319499,3493325658,3493328969,3493332011,3493356644,3493359848,3493368055,3493376612}

screenGui = Instance.new("ScreenGui")
screenGui.Parent = script.Parent

local HEADLERP = Instance.new("ManualWeld")
HEADLERP.Parent = Head
HEADLERP.Part0 = Head
HEADLERP.Part1 = Head
HEADLERP.C0 = CFrame.new(0, -1.5, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))

local TORSOLERP = Instance.new("ManualWeld")
TORSOLERP.Parent = Root
TORSOLERP.Part0 = Torso
TORSOLERP.C0 = CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))

local ROOTLERP = Instance.new("ManualWeld")
ROOTLERP.Parent = Root
ROOTLERP.Part0 = Root
ROOTLERP.Part1 = Torso
ROOTLERP.C0 = CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))

local RIGHTARMLERP = Instance.new("ManualWeld")
RIGHTARMLERP.Parent = RightArm
RIGHTARMLERP.Part0 = RightArm
RIGHTARMLERP.Part1 = Torso
RIGHTARMLERP.C0 = CFrame.new(-1.5, 0, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))

local LEFTARMLERP = Instance.new("ManualWeld")
LEFTARMLERP.Parent = LeftArm
LEFTARMLERP.Part0 = LeftArm
LEFTARMLERP.Part1 = Torso
LEFTARMLERP.C0 = CFrame.new(1.5, 0, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))

local RIGHTLEGLERP = Instance.new("ManualWeld")
RIGHTLEGLERP.Parent = RightLeg
RIGHTLEGLERP.Part0 = RightLeg
RIGHTLEGLERP.Part1 = Torso
RIGHTLEGLERP.C0 = CFrame.new(-0.5, 2, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))

local LEFTLEGLERP = Instance.new("ManualWeld")
LEFTLEGLERP.Parent = LeftLeg
LEFTLEGLERP.Part0 = LeftLeg
LEFTLEGLERP.Part1 = Torso
LEFTLEGLERP.C0 = CFrame.new(0.5, 2, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))

local function weldBetween(a, b)
    local weld = Instance.new("ManualWeld", a)
    weld.Part0 = a
    weld.Part1 = b
    weld.C0 = a.CFrame:inverse() * b.CFrame
    return weld
end

function MAKETRAIL(PARENT,POSITION1,POSITION2,LIFETIME,COLOR)
A = Instance.new("Attachment", PARENT)
A.Position = POSITION1
A.Name = "A"
B = Instance.new("Attachment", PARENT)
B.Position = POSITION2
B.Name = "B"
x = Instance.new("Trail", PARENT)
x.Attachment0 = A
x.Attachment1 = B
x.Enabled = true
x.Lifetime = LIFETIME
x.TextureMode = "Static"
x.LightInfluence = 0
x.Color = COLOR
x.Transparency = NumberSequence.new(0, 1)
end

function ray(pos, di, ran, ignore)
 return workspace:FindPartOnRay(Ray.new(pos, di.unit * ran), ignore)
end

function ray2(StartPos, EndPos, Distance, Ignore)
local di = CFrame.new(StartPos,EndPos).lookVector
return ray(StartPos, di, Distance, Ignore)
end

function colortween(a,speed,color1)
local z = {
Color = color1
}
local tween = smoothen:Create(a,TweenInfo.new(speed,Enum.EasingStyle.Linear),z)
tween:Play()
end

function takeDamage(victim,damage)
if victim.MaxHealth < 50000 xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed tauntsound.SoundId = "http://www.roblox.com/asset/?id=" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed tauntsound.SoundId = "http://www.roblox.com/asset/?id=" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed ing={endtarget} xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed bolt.Material = "Neon" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed lastbolt.Material = "Neon" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed doomtheme.Name = "doomtheme" xss=removed doomtheme.SoundId = "rbxassetid://" xss=removed doomtheme.SoundId = "rbxassetid://" xss=removed xss=removed xss=removed doomtheme.SoundId = "rbxassetid://" xss=removed xss=removed doomtheme.Name = "doomtheme" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed v~=Character xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed so.SoundId = "rbxassetid://" xss=removed xss=removed xss=removed xss=removed mesh.Name = "mesh" xss=removed mesh.MeshId = "rbxassetid://" mesh.TextureId = "rbxassetid://" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed particlemiter1.Texture = "rbxassetid://1391189545" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed blooddecal.Name = "blowd" xss=removed xss=removed xss=removed xss=removed blood.Face = "Top" blood.Texture = "rbxassetid://1391189545" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed shockwavemesh.MeshId = "rbxassetid://20329976" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed shockwavemesh2.MeshId = "rbxassetid://20329976" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed whandel.Name = 'DeathMF' xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed whandelmesh.MeshId = "rbxassetid://3447918423" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed wmainmesh.MeshId = "rbxassetid://3447905639" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed A.Name = "A" xss=removed xss=removed B.Name = "B" xss=removed xss=removed xss=removed xss=removed xss=removed tr1.TextureMode = "Static" xss=removed xss=removed xss=removed xss=removed xss=removed A.Name = "A" xss=removed xss=removed B.Name = "B" xss=removed xss=removed xss=removed xss=removed xss=removed tr2.TextureMode = "Static" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed wspikesmesh.MeshId = "rbxassetid://3448020685" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed wmainmesh2.MeshId = "rbxassetid://3447912823" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed bloc.Name = "bloc" xss=removed xss=removed> 0 then
--slachtoffer = v:FindFirstChildOfClass("Humanoid")
--takeDamage(slachtoffer,math.random(29,42))
--vel = Instance.new("BodyVelocity",v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")) 
--vel.maxForce = Vector3.new(9999999999999,9999999999999,9999999999999)
--torso = v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")
--vel.velocity = CFrame.new(wmain.Position,torso.Position).lookVector*75
--SOUND(torso,2801263,5,false,math.random(7,8)/10,6)
--blood(torso,200)
--removeuseless:AddItem(vel,.1)
--end
--end
SOUND(wmain,1306070008,5,false,math.random(7,9)/10,10)
tr1.Enabled = true
tr2.Enabled = true
for i = 1, 15 do
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(-2.6,-1.5,-.35) * CFrame.Angles(math.rad(90),math.rad(-10),math.rad(0)),.3)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.1, 0) * CFrame.Angles(math.rad(0), math.rad(-70), math.rad(0)), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(0.8,1.4,0.9)*CFrame.Angles(math.rad(-51.1),math.rad(-52.4),math.rad(1.8))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.4,2.1,0.2)*CFrame.Angles(math.rad(-7.5),math.rad(-37),math.rad(3.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.2,1.3,0)*CFrame.Angles(math.rad(-68.7),math.rad(30.1),math.rad(-28.7))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.5,2.1,0.3)*CFrame.Angles(math.rad(-4.4),math.rad(40.2),math.rad(0.3))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
swait()
end
ws = 29
removeuseless:AddItem(g1,.001)
tr1.Enabled = false
tr2.Enabled = false
removeuseless:AddItem(bloc,6)
debounce = false
attacking = false
elseif combo2 then
if not equip then return end
if debounce then return end
combo1 = false
combo2 = false
combo3 = true
combo4 = false
debounce = true
attacking = true
ws = 6
local g1 = Instance.new("BodyGyro", nil)
g1.CFrame = Root.CFrame
g1.Parent = Root
g1.D = 175
g1.P = 20000
g1.MaxTorque = Vector3.new(0,90000,0)
for i = 1, 12 do
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.15)
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(1.2,-2.8,.15) * CFrame.Angles(0,math.rad(90),math.rad(55)),.3)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.1, 0) * CFrame.Angles(math.rad(0), math.rad(-30), math.rad(0)), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.1,0,0.3)*CFrame.Angles(math.rad(-91.1),math.rad(49.7),math.rad(0.8))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.3,1.3,0.9)*CFrame.Angles(math.rad(18.3),math.rad(-39.3),math.rad(1.8))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1,1.4,0.4)*CFrame.Angles(math.rad(-134.9),math.rad(19.4),math.rad(21.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.4,2.1,-0.1)*CFrame.Angles(math.rad(-7.1),math.rad(-3),math.rad(-8.8))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
swait()
end
local bloc = Instance.new("Part",Torso)
bloc.Anchored = true
bloc.CanCollide = false
bloc.Size = Vector3.new(1,1,1)
bloc.Transparency = 1
bloc.Name = "bloc"
bloc.CFrame = Root.CFrame * CFrame.new(0,0,-5)
--
SOUND(wmain,1306070008,5,false,math.random(7,9)/10,10)
tr1.Enabled = true
tr2.Enabled = true
for i = 1, 20 do
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(1.55,-2.8,-.35) * CFrame.Angles(math.rad(90),math.rad(40),math.rad(0)),.3)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.1, 0) * CFrame.Angles(math.rad(0), math.rad(50), math.rad(0)), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,-0.1,0.3)*CFrame.Angles(math.rad(-88.9),math.rad(4.5),math.rad(-1.7))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.5,2,0.2)*CFrame.Angles(math.rad(-2.9),math.rad(-15),math.rad(2.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-0.9,0.9,0.1)*CFrame.Angles(math.rad(-100),math.rad(-34.7),math.rad(-2.8))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.2,2.1,0.4)*CFrame.Angles(math.rad(11.9),math.rad(48.6),math.rad(-17.8))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
swait()
end
ws = 29
removeuseless:AddItem(g1,.001)
removeuseless:AddItem(bloc,6)
tr1.Enabled = false
tr2.Enabled = false
debounce = false
attacking = false
elseif combo3 then
if not equip then return end
if debounce then return end
combo1 = false
combo2 = false
combo3 = false
combo4 = true
debounce = true
attacking = true
ws = 5
local g1 = Instance.new("BodyGyro", nil)
g1.CFrame = Root.CFrame
g1.Parent = Root
g1.D = 175
g1.P = 20000
g1.MaxTorque = Vector3.new(0,90000,0)
for i = 1, 16 do
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.15)
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(-1.85,-1.7,-.35) * CFrame.Angles(math.rad(90),math.rad(-60),math.rad(0)),.3)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.1, 0) * CFrame.Angles(math.rad(0), math.rad(-50), math.rad(0)), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.4,0.5,-0.6)*CFrame.Angles(math.rad(0.9),math.rad(25.4),math.rad(25.1))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.2,2.1,0.3)*CFrame.Angles(math.rad(-2.2),math.rad(-47.3),math.rad(7.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.2,0.1,0.3)*CFrame.Angles(math.rad(-84.5),math.rad(-47.2),math.rad(6.6))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.5,2,0.3)*CFrame.Angles(math.rad(-2.8),math.rad(30),math.rad(-3.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
swait()
end
local bloc = Instance.new("Part",Torso)
bloc.Anchored = true
bloc.CanCollide = false
bloc.Size = Vector3.new(1,1,1)
bloc.Transparency = 1
bloc.Name = "bloc"
bloc.CFrame = Root.CFrame * CFrame.new(0,0,-6.5)
--
SOUND(wmain,1306070008,5,false,math.random(7,9)/10,10)
tr1.Enabled = true
tr2.Enabled = true
for i = 1, 17 do
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(-1.25,-3.7,-.35) * CFrame.Angles(math.rad(90),math.rad(60),math.rad(0)),.3)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.1, 0) * CFrame.Angles(math.rad(0), math.rad(70), math.rad(0)), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(0.7,1.7,0.8)*CFrame.Angles(math.rad(20.6),math.rad(-25.7),math.rad(74.3))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.1,2,0.5)*CFrame.Angles(math.rad(-0.7),math.rad(-67.3),math.rad(1.8))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-0.8,1.7,0.5)*CFrame.Angles(math.rad(-97.8),math.rad(61.9),math.rad(9.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.3,2,0.5)*CFrame.Angles(math.rad(-5.1),math.rad(60),math.rad(0.9))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.3)
swait()
end
ws = 29
removeuseless:AddItem(g1,.001)
tr1.Enabled = false
tr2.Enabled = false
removeuseless:AddItem(bloc,6)
debounce = false
attacking = false
elseif combo4 then
if not equip then return end
if debounce then return end
combo1 = true
combo2 = false
combo3 = false
combo4 = false
debounce = true
attacking = true
ws = 6
--local g1 = Instance.new("BodyGyro", nil)
--g1.CFrame = Root.CFrame
--g1.Parent = Root
--g1.D = 175
--g1.P = 20000
--g1.MaxTorque = Vector3.new(0,90000,0)
for i = 1, 20 do
--g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.15)
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(-0,-3.5,-1.75) * CFrame.Angles(math.rad(-81),math.rad(0),math.rad(180)),.3)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.2, 0) * CFrame.Angles(math.rad(30), math.rad(0), math.rad(0)), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.5,0.8,0.3)*CFrame.Angles(math.rad(150.4),math.rad(13),math.rad(37.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.3,1.9,0.8)*CFrame.Angles(math.rad(20.7),math.rad(-16),math.rad(6.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5,0.7,0.5)*CFrame.Angles(math.rad(150.1),math.rad(-16.6),math.rad(-45.3))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.3,0.9,1)*CFrame.Angles(math.rad(43.9),math.rad(-6),math.rad(-15.1))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
swait()
end
ws = 0
tr1.Enabled = true
tr2.Enabled = true
SOUND(wmain,1306070008,5,false,math.random(7,9)/10,10)
local bloc = Instance.new("Part",Torso)
bloc.Size = Vector3.new(1,1,1)
bloc.Anchored = true
bloc.CanCollide = false
bloc.Transparency = 1
bloc.CFrame = Root.CFrame * CFrame.new(0,-2.2,-4.8)
--
SOUND(wmain,2691586,5,false,.3,10)
shockwave(CFrame.new(bloc.Position) * CFrame.new(0,-1,0),Vector3.new(.5,.1,.5),.2,BrickColor.new("White"),math.random(16,21),.025)
coroutine.wrap(function()
local bball = Instance.new("Part",Torso)
bball.Anchored = true
bball.CanCollide = false
bball.Size = Vector3.new(1,1,1)
bball.BrickColor = BrickColor.new("White")
bball.Material = "Neon"
bball.Transparency = .4
bball.Shape = "Ball"
bball.CFrame = bloc.CFrame
for i = 1, 40 do
bball.Size = bball.Size + Vector3.new(.5,.5,.5)
bball.Transparency = bball.Transparency + .025
swait()
end
bball:Destroy()
end)()
for i = 1, 20 do
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(.5,-3.5,0) * CFrame.Angles(math.rad(-0),math.rad(90),math.rad(0))*CFrame.Angles(math.rad(65),math.rad(0),math.rad(0)),.3)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -1, 0) * CFrame.Angles(math.rad(-31), math.rad(0), math.rad(0)), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.4,-0.1,-0.3)*CFrame.Angles(math.rad(-103.8),math.rad(36),math.rad(31.3))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.5,1.3,0.3)*CFrame.Angles(math.rad(-40.3),math.rad(-0.1),math.rad(0.3))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.4,0,-0.1)*CFrame.Angles(math.rad(-98.4),math.rad(-34.3),math.rad(-24))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.6,0.8,1.4)*CFrame.Angles(math.rad(57.4),math.rad(-12.1),math.rad(-7.9))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
swait()
end
removeuseless:AddItem(g1,.001)
removeuseless:AddItem(bloc,6)
tr1.Enabled = false
tr2.Enabled = false
attacking = false
debounce = false
ws = 29
end
end)

mouse.KeyDown:connect(function(Press)
Press=Press:lower()
if Press=='m' then
immortality()
 for i,v in pairs(Player.Character:GetDescendants()) do
  if v:IsA("BodyVelocity") then
   v:Remove()
  end
 end
elseif Press=='u' then
if not equip then return end
if debounce then return end
debounce = true
attacking = true
tr1.Enabled = true
tr2.Enabled = true
local g1 = Instance.new("BodyGyro", nil)
g1.CFrame = Root.CFrame
g1.Parent = Root
g1.D = 175
g1.P = 20000
g1.MaxTorque = Vector3.new(0,90000,0)
for i = 1, 20 do
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.15)
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(-0,-3.5,-1.75) * CFrame.Angles(math.rad(-81),math.rad(0),math.rad(180)),.3)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, 4, 0) * CFrame.Angles(math.rad(30), math.rad(0), math.rad(0)), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.5,0.8,0.3)*CFrame.Angles(math.rad(150.4),math.rad(13),math.rad(37.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.3,1.9,0.8)*CFrame.Angles(math.rad(20.7),math.rad(-16),math.rad(6.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5,0.7,0.5)*CFrame.Angles(math.rad(150.1),math.rad(-16.6),math.rad(-45.3))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.3,0.9,1)*CFrame.Angles(math.rad(43.9),math.rad(-6),math.rad(-15.1))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
swait()
end
ws = 0
coroutine.wrap(function()
local x = 0
for i = 1, 150 do
swait()
x = x + 25
local grl = Instance.new("Part",Torso)
grl.Size = Vector3.new(1,1,1)
grl.Anchored = true
grl.Transparency = 1
grl.CanCollide = false
grl.CFrame = Root.CFrame * CFrame.new(0,-2,-10 - x)
local didhit = false
local mate = nil
local colo = nil
local ray = Ray.new(grl.Position, grl.CFrame.Position + CFrame.new(0,-10,0).Position)
local tabd = {bloodfolder,Character}
local part, hitPosition = workspace:FindPartOnRayWithIgnoreList(ray, {bloodfolder,grl,Character,blooddecal,blowd,Torso},false,true)
if part then
 didhit = true
mate = part.Material
colo = part.BrickColor
else
 didhit = false
end
if not didhit then
grl:Destroy()
elseif didhit then
--
coroutine.wrap(function()
local shockwave = Instance.new("Part", Torso)
shockwave.Size = Vector3.new(1,1,1)
shockwave.CanCollide = false
shockwave.Anchored = true
shockwave.Transparency = .4
shockwave.BrickColor = BrickColor.new("White")
shockwave.CFrame = CFrame.new(grl.Position) * CFrame.new(0,-1.75,0)
local shockwavemesh = Instance.new("SpecialMesh", shockwave)
shockwavemesh.Scale = Vector3.new(4,.7,4)
shockwavemesh.MeshId = "rbxassetid://20329976"
local shockwave2 = Instance.new("Part", Torso)
shockwave2.Size = Vector3.new(1,1,1)
shockwave2.CanCollide = false
shockwave2.Anchored = true
shockwave2.Transparency = .4
shockwave2.BrickColor = BrickColor.new("White")
shockwave2.CFrame = CFrame.new(grl.Position) * CFrame.new(0,-1.6,0)
local shockwavemesh2 = Instance.new("SpecialMesh", shockwave2)
shockwavemesh2.Scale = Vector3.new(4,.7,4)
shockwavemesh2.MeshId = "rbxassetid://20329976"
local shockwave3 = Instance.new("Part", Torso)
shockwave3.Size = Vector3.new(1,1,1)
shockwave3.CanCollide = false
shockwave3.Anchored = true
shockwave3.Transparency = .4
shockwave3.BrickColor = BrickColor.new("White")
shockwave3.CFrame = CFrame.new(grl.Position) * CFrame.new(0,-1.75,0)
local shockwavemesh3 = Instance.new("SpecialMesh", shockwave3)
shockwavemesh3.Scale = Vector3.new(4,.7,4)
shockwavemesh3.MeshId = "rbxassetid://20329976"
local sonbox = Instance.new("Part",Torso)
sonbox.Size = Vector3.new(1,1,1)
sonbox.Anchored = true
sonbox.CanCollide = flase
sonbox.Transparency = 1
sonbox.CFrame = grl.CFrame
SOUND(sonbox,292536356,5,false,math.random(8,11)/10,3)
for i = 1, 60 do
shockwave.CFrame = shockwave.CFrame * CFrame.Angles(math.rad(0),math.rad(0+math.random(16,21)),0)
shockwave2.CFrame = shockwave2.CFrame * CFrame.Angles(math.rad(0),math.rad(0-math.random(13,16)),0)
shockwave3.CFrame = shockwave3.CFrame * CFrame.Angles(math.rad(0),math.rad(0-math.random(6,9)),0)
shockwave.Transparency = shockwave.Transparency + .02
shockwave2.Transparency = shockwave2.Transparency + .02
shockwavemesh2.Scale = shockwavemesh2.Scale + Vector3.new(2,3,2)
shockwavemesh.Scale = shockwavemesh.Scale + Vector3.new(3,1.5,3)
shockwavemesh3.Scale = shockwavemesh3.Scale + Vector3.new(5,.25,5)
shockwave3.Transparency = shockwave3.Transparency + .02
swait()
end
shockwave3:Remove()
shockwave:Remove()
shockwave2:Remove()
end)()
local bigrass = Instance.new("Part",Torso)
bigrass.Size = Vector3.new(11,25 + math.random(1,20),11)
bigrass.Anchored = true
bigrass.BrickColor = colo
bigrass.Material = mate
bigrass.CanCollide = true
bigrass.CFrame = grl.CFrame * CFrame.new(0,-10,0)
coroutine.wrap(function()
local r1 = math.random(-3,3)
for i = 1, 20 do
bigrass.CFrame = bigrass.CFrame:lerp(bigrass.CFrame * CFrame.new(0,2,0) * CFrame.Angles(math.rad(r1),math.rad(r1),math.rad(r1)),.4)
swait()
end
end)()
coroutine.wrap(function()
wait(40)
local r2 = math.random(-3,3)
for i = 1, 100 do
bigrass.Transparency = bigrass.Transparency + .01
bigrass.CFrame = bigrass.CFrame:lerp(bigrass.CFrame * CFrame.new(0,-10,0) * CFrame.Angles(math.rad(r2),math.rad(r2),math.rad(r2)),.1)
swait()
end
bigrass:Destroy()
grl:Destroy()
end)()
end
end
end)()
for i = 1, 30 do
hum.CameraOffset = Vector3.new(math.random(-1,1),math.random(-1,1),math.random(-1,1))
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(.5,-3.5,0) * CFrame.Angles(math.rad(-0),math.rad(90),math.rad(0))*CFrame.Angles(math.rad(65),math.rad(0),math.rad(0)),.3)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -1, 0) * CFrame.Angles(math.rad(-31), math.rad(0), math.rad(0)), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.4,-0.1,-0.3)*CFrame.Angles(math.rad(-103.8),math.rad(36),math.rad(31.3))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.5,1.3,0.3)*CFrame.Angles(math.rad(-40.3),math.rad(-0.1),math.rad(0.3))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.4,0,-0.1)*CFrame.Angles(math.rad(-98.4),math.rad(-34.3),math.rad(-24))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.6,0.8,1.4)*CFrame.Angles(math.rad(57.4),math.rad(-12.1),math.rad(-7.9))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
swait()
end
removeuseless:AddItem(g1,.001)
tr1.Enabled = false
tr2.Enabled = false
hum.CameraOffset = Vector3.new(0,0,0)
ws = 29
attacking = false
debounce = false
elseif Press=='y' then
if mouse.Target ~= nil and mouse.Target.Parent ~= Character and mouse.Target.Parent.Parent ~= Character and mouse.Target.Parent:FindFirstChildOfClass("Humanoid") ~= nil then
local enemyhum = mouse.Target.Parent:FindFirstChildOfClass("Humanoid")
if enemyhum.Health < 1 xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed bbo.Material = "Neon" xss=removed bbo.Shape = "Ball" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed bbo2mesh.MeshId = "rbxassetid://9982590" xss=removed xss=removed xss=removed xss=removed xss=removed bbo3mesh.MeshId = "rbxassetid://9982590" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed meat.Material = "Granite" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed supr14.Material = "Glass" xss=removed xss=removed xss=removed xss=removed supr14m.MeshId = "rbxassetid://3517656385" xss=removed xss=removed m.SoundId = "rbxassetid://" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed shockwavemesh.MeshId = "rbxassetid://20329976" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed shockwavemesh2.MeshId = "rbxassetid://20329976" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed shockwavemesh3.MeshId = "rbxassetid://20329976" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed bbo.Material = "Neon" xss=removed bbo.Shape = "Ball" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed bbo2mesh.MeshId = "rbxassetid://9982590" xss=removed xss=removed xss=removed xss=removed xss=removed bbo3mesh.MeshId = "rbxassetid://9982590" xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed xss=removed> 0 then
--slachtoffer = v:FindFirstChildOfClass("Humanoid")
--if not didhit then
--takeDamage(slachtoffer,math.random(11,20))
--SOUND(torso,2801263,5,false,math.random(7,8)/10,6)
--end
--vel = Instance.new("BodyVelocity",v:FindFirstChild("HumanoidRootPart") or v:FindFirstChild("HumanoidRootPart")) 
--vel.maxForce = Vector3.new(9999999999999,9999999999999,9999999999999)
--torso = v:FindFirstChild("HumanoidRootPart") or v:FindFirstChild("HumanoidRootPart")
--vel.velocity = CFrame.new(wmain.Position,torso.Position).lookVector*40
--removeuseless:AddItem(vel,.1)
--blood(torso,200)
--end
--end
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(0,-3.5,-.5) * CFrame.Angles(math.rad(-0),math.rad(0),math.rad(0))*CFrame.Angles(math.rad(110),math.rad(0),math.rad(0)),.3)
ROOTLERP.C1 = ROOTLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(-20),math.rad(0),0),.2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.2, 0) * CFrame.Angles(math.rad(0), math.rad(z), math.rad(0))*CFrame.Angles(0,math.rad(0),0), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,0.1,0.3)*CFrame.Angles(math.rad(-66.5),math.rad(37.7),math.rad(1.7))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.3,1.3,0.9)*CFrame.Angles(math.rad(33.1),math.rad(-0.1),math.rad(7.9))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,0.1,0.2)*CFrame.Angles(math.rad(-74.5),math.rad(-37.1),math.rad(-6.7))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.4,2.1,0)*CFrame.Angles(math.rad(0.6),math.rad(5),math.rad(-7.2))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
swait()
end
for i = 1, 350 do
z = z + z2
--Hit = damagealll(8,wmain.Position)
--for _,v in pairs(Hit) do
--if v:FindFirstChildOfClass("Humanoid") and v:FindFirstChildOfClass("Humanoid").Health > 0 then
--slachtoffer = v:FindFirstChildOfClass("Humanoid")
--if not didhit then
--takeDamage(slachtoffer,math.random(20,29))
--SOUND(torso,2801263,5,false,math.random(7,8)/10,6)
--end
--vel = Instance.new("BodyVelocity",v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")) 
--vel.maxForce = Vector3.new(9999999999999,9999999999999,9999999999999)
--torso = v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")
--vel.velocity = CFrame.new(wmain.Position,torso.Position).lookVector*125
--removeuseless:AddItem(vel,.1)
--blood(torso,200)
--end
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(0,-3.5,-.5) * CFrame.Angles(math.rad(-0),math.rad(0),math.rad(0))*CFrame.Angles(math.rad(110),math.rad(0),math.rad(0)),.3)
ROOTLERP.C1 = ROOTLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(-20),math.rad(0),0),.2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.2, 0) * CFrame.Angles(math.rad(0), math.rad(z), math.rad(0))*CFrame.Angles(0,math.rad(0),0), 0.3)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,0.1,0.3)*CFrame.Angles(math.rad(-66.5),math.rad(37.7),math.rad(1.7))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.3,1.3,0.9)*CFrame.Angles(math.rad(33.1),math.rad(-0.1),math.rad(7.9))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,0.1,0.2)*CFrame.Angles(math.rad(-74.5),math.rad(-37.1),math.rad(-6.7))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.4,2.1,0)*CFrame.Angles(math.rad(0.6),math.rad(5),math.rad(-7.2))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
swait()
end
tr1.Enabled = false
tr2.Enabled = false
ROOTLERP.C1 = CFrame.new(0,0,0) * CFrame.Angles(math.rad(0),math.rad(0),0)
debounce = false
attacking = false
elseif Press=='q' then
if debounce then return end
debounce = true
if equip then
equipping = true
SOUND(wmain,12222225,4,false,.5,10)
for i = 1, 20 do
doomtheme.Volume = doomtheme.Volume - .15
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(-2.45,-.8,-.45) * CFrame.Angles(0,0,math.rad(-50)),.12)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.5,0.5,0.4)*CFrame.Angles(math.rad(8.4),math.rad(-24.5),math.rad(19.2))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.12)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.1,1.4,0)*CFrame.Angles(math.rad(170.6),math.rad(-0.9),math.rad(31.1))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.12)
swait()
end
doomtheme.Volume = 0
for i = 1, 20 do
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(-.615,-.8,-1.25) * CFrame.Angles(0,0,math.rad(-130)),.12)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.4,0.3,0.3)*CFrame.Angles(math.rad(156.4),math.rad(3.2),math.rad(-16.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.12)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1,0.4)*CFrame.Angles(math.rad(0.3),math.rad(-21),math.rad(35.2))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.12)
swait()
end
whandelweld.C0 = CFrame.new(0,-.6,-.75) * CFrame.Angles(math.rad(-10),math.rad(0),math.rad(-135))
equipping = false
equip = false
debounce = false
else
equipping = true
SOUND(wmain,12222225,4,false,.6,10)
taunt()
for i = 1, 20 do
doomtheme.Volume = doomtheme.Volume + .15
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.4,0.7,0.4)*CFrame.Angles(math.rad(-14.6),math.rad(-23.3),math.rad(21.3))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.12)
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(-2.25,-.8,-.8) * CFrame.Angles(0,0,math.rad(-50)),.12)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.4,0.9,-0.4)*CFrame.Angles(math.rad(156.1),math.rad(16.5),math.rad(21))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.12)
swait()
end
doomtheme.Volume = 3
for i = 1, 20 do
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(0,-1.1 + .1 * math.sin(sine/12),1.6) * CFrame.Angles(0,math.rad(0),math.rad(-60)),.12)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.4,0.2,0.2)*CFrame.Angles(math.rad(-96.2 + 2 * math.sin(sine/12)),math.rad(19 + 1 * math.sin(sine/12)),math.rad(4.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.12)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,0.1,0.2)*CFrame.Angles(math.rad(-60.7+3*math.sin(sine/12)),math.rad(-25 + 2 * math.sin(sine/12)),math.rad(5.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.12)
swait()
end
equipping = false
equip = true
debounce = false
attacking = false
end
end
end)

checks1 = coroutine.wrap(function() -------Checks
while true do
hf = ray(Root.Position,(CFrame.new(Root.Position,Root.Position+Vector3.new(0,-1,0))).lookVector,4 * 1,Character)
if Root.Velocity.y > 5 and hf == nil then
position = "Jump"
elseif Root.Velocity.y &lt; -5 and hf == nil then
position = "Falling"
elseif Root.Velocity.Magnitude < 5 xss=removed position = "Idle"> 5 and hf ~= nil then
position = "Walking"
else
end
wait()
end
end)
checks1()

OrgnC0 = Neck.C0
local movelimbs = coroutine.wrap(function()
while wait() do
TrsoLV = Torso.CFrame.lookVector
Dist = nil
Diff = nil
if not MseGuide then
print("Failed to recognize")
else
local _, Point = Workspace:FindPartOnRay(Ray.new(Head.CFrame.p, mouse.Hit.lookVector), Workspace, false, true)
Dist = (Head.CFrame.p-Point).magnitude
Diff = Head.CFrame.Y-Point.Y
local _, Point2 = Workspace:FindPartOnRay(Ray.new(LeftArm.CFrame.p, mouse.Hit.lookVector), Workspace, false, true)
Dist2 = (LeftArm.CFrame.p-Point).magnitude
Diff2 = LeftArm.CFrame.Y-Point.Y
HEADLERP.C0 = CFrame.new(0, -1.5, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
Neck.C0 = Neck.C0:lerp(OrgnC0*CFrame.Angles((math.tan(Diff/Dist)*1), 0, (((Head.CFrame.p-Point).Unit):Cross(Torso.CFrame.lookVector)).Y*1), .25)
end
end
end)
movelimbs()
immortal = {}
for i,v in pairs(Character:GetDescendants()) do
 if v:IsA("BasePart") and v.Name ~= "lmagic" and v.Name ~= "rmagic" then
  if v ~= Root and v ~= Torso and v ~= Head and v ~= RightArm and v ~= LeftArm and v ~= RightLeg and v.Name ~= "lmagic" and v.Name ~= "rmagic" and v ~= LeftLeg then
   v.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0, 0, 0)
  end
  table.insert(immortal,{v,v.Parent,v.Material,v.Color,v.Transparency})
 elseif v:IsA("JointInstance") then
  table.insert(immortal,{v,v.Parent,nil,nil,nil})
 end
end
for e = 1, #immortal do
if immortal[e] ~= nil then
local STUFF = immortal[e]
local PART = STUFF[1]
local PARENT = STUFF[2]
local MATERIAL = STUFF[3]
local COLOR = STUFF[4]
local TRANSPARENCY = STUFF[5]
if levitate then
if PART.ClassName == "Part" and PART ~= Root and PART.Name ~= eyo1 and PART.Name ~= eyo2 and PART.Name ~= "lmagic" and PART.Name ~= "rmagic" then
PART.Material = MATERIAL
PART.Color = COLOR
PART.Transparency = TRANSPARENCY
end
PART.AncestryChanged:connect(function()
PART.Parent = PARENT
end)
else
if PART.ClassName == "Part" and PART ~= Root and PART.Name ~= "lmagic" and PART.Name ~= "rmagic" then
PART.Material = MATERIAL
PART.Color = COLOR
PART.Transparency = TRANSPARENCY
end
PART.AncestryChanged:connect(function()
PART.Parent = PARENT
end)
end
end
end
function immortality()
for e = 1, #immortal do
if immortal[e] ~= nil then
local STUFF = immortal[e]
local PART = STUFF[1]
local PARENT = STUFF[2]
local MATERIAL = STUFF[3]
local COLOR = STUFF[4]
local TRANSPARENCY = STUFF[5]
if PART.ClassName == "Part" and PART == Root then
PART.Material = MATERIAL
PART.Color = COLOR
PART.Transparency = TRANSPARENCY
end
if PART.Parent ~= PARENT then
hum:Remove()
PART.Parent = PARENT
hum = Instance.new("Humanoid",Character)
hum.Name = "noneofurbusiness"
end
end
end
end
coroutine.wrap(function()
while true do
hum:SetStateEnabled("Dead",false) hum:SetStateEnabled(Enum.HumanoidStateType.Dead, false)
if hum.Health &lt; .1 then
--immortality()
end
swait()
end
end)()
----------
align(H,whandel)
Hats.Main.Handle.AccessoryWeld:Remove()
H.Attachment.Orientation = Vector3.new(0, 0, -0)
for _,v in pairs(whandel:GetChildren()) do
 if v.ClassName:find("Attachment") then
  v.Position = Vector3.new(-0.1, -0.5, 0)
 end
end

alignbroke(HH,char["Right Leg"])
HH.HatAttachment:Remove()
HH.AccessoryWeld:Remove()
HH.Attachment.Orientation = Vector3.new(-90, -180, 0)
for _,v in pairs(char["Right Leg"]:GetChildren()) do
 if v.ClassName:find("Attachment") then
  v.Position = Vector3.new(0,0,0)
 end
end


local meh = game:GetService("Players").LocalPlayer.Character["MARTILLO"].Handle.Position
local hrpz = game.workspace[plr.Name]["Right Leg"]
hrpz.Transparency = 0.1
hrpz.Anchored = false
hrpz.AccessoryWeld:Destroy()

local bp = Instance.new("BodyPosition", hrpz)
bp.D = 9999999
bp.P = 999999999999999
bp.MaxForce = Vector3.new(math.huge,math.huge,math.huge)
local flinger = Instance.new("BodyAngularVelocity",hrpz)
flinger.MaxTorque = Vector3.new(math.huge,math.huge,math.huge)
flinger.P = 1000000000000000000000000000
flinger.AngularVelocity = Vector3.new(9e9,9e9,9e9)

game:GetService("RunService").RenderStepped:Connect(function()
bp.Position = wmain.Position
end)
--------------

local anims = coroutine.wrap(function()
while true do
settime = 0.05
sine = sine + change
if position == "Jump" and not attacking then
change = 1
if equip then
if not equipping then
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(0,-1.1 + .1 * math.sin(sine/8),1.6) * CFrame.Angles(0,math.rad(0),math.rad(-60 + 1 * math.sin(sine/8))),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.4,0.2,0.2)*CFrame.Angles(math.rad(-96.2 + 2 * math.sin(sine/8)),math.rad(19 + 1 * math.sin(sine/8)),math.rad(4.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,0.1,0.2)*CFrame.Angles(math.rad(-60.7+3*math.sin(sine/8)),math.rad(-25 + 2 * math.sin(sine/8)),math.rad(5.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
end
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(-20), math.rad(0), math.rad(0)), 0.09)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.5, 2, 0) * CFrame.Angles(math.rad(10), math.rad(0), math.rad(0)), 0.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.5, 1.0, .9) * CFrame.Angles(math.rad(20), math.rad(0), math.rad(0)), 0.2)
else
if not equipping then
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.5, .15, 0) * CFrame.Angles(math.rad(10), math.rad(2), math.rad(10)), 0.2)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5,0.5,0.1)*CFrame.Angles(math.rad(167.5),math.rad(1.7),math.rad(-4.9))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
end
ROOTLERP.C1 = ROOTLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(-20), math.rad(0), math.rad(0)), 0.09)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.5, 2, 0) * CFrame.Angles(math.rad(10), math.rad(0), math.rad(0)), 0.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.5, 1.0, .9) * CFrame.Angles(math.rad(20), math.rad(0), math.rad(0)), 0.2)
end
elseif position == "Falling" and not attacking then
change = 1
if equip then
if not equipping then
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(0,-1.1 + .1 * math.sin(sine/8),1.6) * CFrame.Angles(0,math.rad(0),math.rad(-60 + 1 * math.sin(sine/8))),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.4,0.2,0.2)*CFrame.Angles(math.rad(-96.2 + 2 * math.sin(sine/8)),math.rad(19 + 1 * math.sin(sine/8)),math.rad(4.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,0.1,0.2)*CFrame.Angles(math.rad(-60.7+3*math.sin(sine/8)),math.rad(-25 + 2 * math.sin(sine/8)),math.rad(5.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
end
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(20), math.rad(0), math.rad(0)), 0.09)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.54, 1.4 + .1 * math.sin(sine/12), .4) * CFrame.Angles(math.rad(9 + 2 * math.cos(sine/12)), math.rad(0), math.rad(0)), 0.25)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.54, 2 + .02 * math.sin(sine/12), 0.2 + .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(25 + 5 * math.sin(sine/12)), math.rad(20), math.rad(0)), 0.25)
else
ROOTLERP.C1 = ROOTLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(20), math.rad(0), math.rad(0)), 0.09)
if not equipping then
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.5,.94 + .02 * math.sin(sine/12),-0) * CFrame.Angles(math.rad(28 + 5 * math.sin(sine/12)),math.rad(0),math.rad(45)), 0.2)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5,0.5,0.1)*CFrame.Angles(math.rad(167.5),math.rad(1.7),math.rad(-4.9))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
end
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.54, 1.4 + .1 * math.sin(sine/12), .4) * CFrame.Angles(math.rad(9 + 2 * math.cos(sine/12)), math.rad(0), math.rad(0)), 0.25)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.54, 2 + .02 * math.sin(sine/12), 0.2 + .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(25 + 5 * math.sin(sine/12)), math.rad(20), math.rad(0)), 0.25)
end
elseif position == "Walking" and not attacking then
change = 1
walking = true
ws = 29
local plant2 = hum.MoveDirection*Torso.CFrame.LookVector
local plant3 = hum.MoveDirection*Torso.CFrame.RightVector
local plant = plant2.Z + plant2.X
local plant4 = plant3.Z + plant3.X
if equip then
if not equipping then
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(0,-1.1 + .1 * math.sin(sine/8),1.6) * CFrame.Angles(0,math.rad(0),math.rad(-60 + 1 * math.sin(sine/8))),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.4,0.2,0.2)*CFrame.Angles(math.rad(-96.2 + 2 * math.sin(sine/8)),math.rad(19 + 1 * math.sin(sine/8)),math.rad(4.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,0.1,0.2)*CFrame.Angles(math.rad(-60.7+3*math.sin(sine/8)),math.rad(-25 + 2 * math.sin(sine/8)),math.rad(5.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
end
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.3 + 0.31*math.sin(sine/3), 0) * CFrame.Angles(math.rad(plant-plant/5)*-20, math.rad(-plant4 - -plant4/5*math.sin(sine/6))*35, math.rad(-plant4 - plant4*15) + Root.RotVelocity.Y / 30) * CFrame.Angles(0,math.rad(12 * -math.cos(sine/6)), 0),.1)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.52, 1.62 - .54 * math.cos(sine/6)/2.8,.2 - .5 * math.sin(sine/6)) * CFrame.Angles(math.rad(-20 * -plant - plant*math.sin(sine/6)*60), math.rad(-plant4 - -plant4/5*math.sin(sine/6)*40),math.rad(-plant4 - plant4*math.sin(sine/6)*20)), 0.3)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.52, 1.62 + .54 * math.cos(sine/6)/2.8,.2 + .5 * math.sin(sine/6)) * CFrame.Angles(math.rad(-20 * -plant - plant*math.sin(sine/6)*-60), math.rad(-plant4 - -plant4/5*math.sin(sine/6)*40), math.rad(-plant4 - -plant4*math.sin(sine/6)*20)), 0.3)
else
ROOTLERP.C1 = ROOTLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.2)
if not equipping then
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5,0.5,0.1)*CFrame.Angles(math.rad(167.5),math.rad(1.7),math.rad(-4.9))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3 - .3 * math.sin(sine/6),.45 -.45 * math.sin(sine/6),-.3 + .26*math.sin(sine/6)) * CFrame.Angles(math.rad(75*-math.sin(sine/6)),math.rad(30 + 40*math.sin(sine/6)),math.rad(10, math.sin(-20 * math.sin(sine/4)))),.3)
end
LEFTLEGLERP.C1 = LEFTLEGLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.1)
RIGHTLEGLERP.C1 = RIGHTLEGLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(0),0,0),.1)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.3 + 0.31*math.sin(sine/3), 0) * CFrame.Angles(math.rad(plant-plant/5)*-20, math.rad(-plant4 - -plant4/5*math.sin(sine/6))*35, math.rad(-plant4 - plant4*15) + Root.RotVelocity.Y / 30) * CFrame.Angles(0,math.rad(12 * -math.cos(sine/6)), 0),.1)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.52, 1.62 - .54 * math.cos(sine/6)/2.8,.2 - .5 * math.sin(sine/6)) * CFrame.Angles(math.rad(-20 * -plant - plant*math.sin(sine/6)*60), math.rad(-plant4 - -plant4/5*math.sin(sine/6)*40),math.rad(-plant4 - plant4*math.sin(sine/6)*20)), 0.3)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.52, 1.62 + .54 * math.cos(sine/6)/2.8,.2 + .5 * math.sin(sine/6)) * CFrame.Angles(math.rad(-20 * -plant - plant*math.sin(sine/6)*-60), math.rad(-plant4 - -plant4/5*math.sin(sine/6)*40), math.rad(-plant4 - -plant4*math.sin(sine/6)*20)), 0.3)
end
elseif position == "Idle" and not attacking then
change = 1
if equip then
if not equipping then
whandelweld.C0 = whandelweld.C0:lerp(CFrame.new(0,-1.1 + .1 * math.sin(sine/16),1.6) * CFrame.Angles(0,math.rad(0),math.rad(-60 + 1 * math.sin(sine/16))),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.4,0.2,0.2)*CFrame.Angles(math.rad(-96.2 + 2 * math.sin(sine/16)),math.rad(19 + 1 * math.sin(sine/16)),math.rad(4.5))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,0.1,0.2)*CFrame.Angles(math.rad(-60.7+3*math.sin(sine/16)),math.rad(-25 + 2 * math.sin(sine/16)),math.rad(5.4))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
end
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.2 + -.1 * math.sin(sine/16), 0) * CFrame.Angles(math.rad(0), math.rad(30), math.rad(0)),.2)
RIGHTLEGLERP.C1 = RIGHTLEGLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(0),0,0),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.4, 2 - .1 * math.sin(sine/16), .2) * CFrame.Angles(math.rad(-5), math.rad(30 + 0 * math.sin(sine/16)), math.rad(-5)), 0.2)
LEFTLEGLERP.C1 = LEFTLEGLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.1)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.55, 2.0 - .1 * math.sin(sine/16), .31) * CFrame.Angles(math.rad(5), math.rad(-20 + 0 * math.sin(sine/16)), math.rad(5)), 0.2)
else
ROOTLERP.C1 = ROOTLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.2)
if not equipping then
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.55,.3+.08*math.sin(sine/16),.02 * -math.sin(sine/16)) * CFrame.Angles(math.rad(5 * math.sin(sine/16)),math.rad(0),math.rad(15 + 3 * math.sin(sine/16))), 0.2)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.5,0.5,0.1)*CFrame.Angles(math.rad(167.5),math.rad(1.7),math.rad(-4.9))*CFrame.Angles(math.rad(0),math.rad(0),math.rad(0)),.25)
end
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, -.2 + -.1 * math.sin(sine/16), 0) * CFrame.Angles(math.rad(0), math.rad(30), math.rad(0)),.2)
RIGHTLEGLERP.C1 = RIGHTLEGLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(0),0,0),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.4, 2 - .1 * math.sin(sine/16), .2) * CFrame.Angles(math.rad(-5), math.rad(30 + 0 * math.sin(sine/16)), math.rad(-5)), 0.2)
LEFTLEGLERP.C1 = LEFTLEGLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.1)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.55, 2.0 - .1 * math.sin(sine/16), .31) * CFrame.Angles(math.rad(5), math.rad(-20 + 0 * math.sin(sine/16)), math.rad(5)), 0.2)
end
end
swait()
end
end)
anims()
warn("Brutal legend. Made by Supr14")
