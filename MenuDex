-- ==============================================
-- 🎀 MENU SASUKE COMPLETO E ORGANIZADO (DELTA MOBILE)
-- ==============================================

local Players = game:GetService("Players")
local CoreGui = game:GetService("CoreGui")
local Tween = game:GetService("TweenService")
local UIS = game:GetService("UserInputService")

-- LIMPA VERSÃO ANTIGA PARA EVITAR CRASH
if CoreGui:FindFirstChild("Menu_Sasaki") then
    CoreGui.Menu_Sasaki:Destroy()
end

-- BASE PRINCIPAL
local Menu = Instance.new("ScreenGui")
Menu.Name = "Menu_Sasaki"
Menu.ResetOnSpawn = false
Menu.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
Menu.DisplayOrder = 999
Menu.Parent = CoreGui

-- ==============================================
-- ✅ JANELA PRINCIPAL (LARGURA: 400 | ALTURA: 270)
-- ==============================================
local Janela = Instance.new("Frame")
Janela.Size = UDim2.new(0, 0, 0, 0) -- Começa em 0 para a animação de abertura funcionar
Janela.Position = UDim2.new(0.5, -200, 0.5, -135) -- Centralizado por padrão no mobile
Janela.BackgroundColor3 = Color3.fromRGB(255, 240, 245)
Janela.ClipsDescendants = true
Janela.Visible = false
Janela.Active = true
Janela.Parent = Menu
Instance.new("UICorner", Janela).CornerRadius = UDim.new(0, 24)

local Borda = Instance.new("UIStroke")
Borda.Thickness = 2
Borda.Color = Color3.fromRGB(255, 180, 200)
Borda.Parent = Janela

-- ==============================================
-- ✅ CABEÇALHO E TÍTULO
-- ==============================================
local Cabecalho = Instance.new("Frame")
Cabecalho.Size = UDim2.new(1, 0, 0, 45)
Cabecalho.BackgroundColor3 = Color3.fromRGB(255, 200, 220)
Cabecalho.Parent = Janela
Instance.new("UICorner", Cabecalho).CornerRadius = UDim.new(0, 24)

local Titulo = Instance.new("TextLabel")
Titulo.Size = UDim2.new(1, -50, 1, 0)
Titulo.Position = UDim2.new(0, 15, 0, 0)
Titulo.BackgroundTransparency = 1
Titulo.Text = "🎀 SASAKI 🎀"
Titulo.TextColor3 = Color3.fromRGB(220, 100, 150)
Titulo.Font = Enum.Font.GothamBold
Titulo.TextSize = 18
Titulo.TextXAlignment = Enum.TextXAlignment.Left
Titulo.Parent = Cabecalho

-- ==============================================
-- ✅ BOTÃO FECHAR + CONFIRMAÇÃO
-- ==============================================
local BtnFechar = Instance.new("TextButton")
BtnFechar.Size = UDim2.new(0, 28, 0, 28)
BtnFechar.Position = UDim2.new(1, -38, 0.5, -14)
BtnFechar.BackgroundColor3 = Color3.fromRGB(255, 220, 230)
BtnFechar.Text = "×"
BtnFechar.TextColor3 = Color3.fromRGB(220, 100, 150)
BtnFechar.Font = Enum.Font.GothamBold
BtnFechar.TextSize = 22
BtnFechar.Parent = Cabecalho
Instance.new("UICorner", BtnFechar).CornerRadius = UDim.new(1, 0)

local Confirmar = Instance.new("Frame")
Confirmar.Size = UDim2.new(0, 220, 0, 110)
Confirmar.Position = UDim2.new(0.5, -110, 0.5, -55)
Confirmar.BackgroundColor3 = Color3.fromRGB(255, 240, 245)
Confirmar.Visible = false
Confirmar.Parent = Menu
Instance.new("UICorner", Confirmar).CornerRadius = UDim.new(0, 18)

local BordaConf = Instance.new("UIStroke")
BordaConf.Thickness = 2
BordaConf.Color = Color3.fromRGB(255, 180, 200)
BordaConf.Parent = Confirmar

local TextoConf = Instance.new("TextLabel")
TextoConf.Size = UDim2.new(1, 0, 0, 50)
TextoConf.BackgroundTransparency = 1
TextoConf.Text = "Deseja apagar o menu?"
TextoConf.TextColor3 = Color3.fromRGB(220, 100, 150)
TextoConf.Font = Enum.Font.GothamBold
TextoConf.TextSize = 16
TextoConf.Parent = Confirmar

local BotoesArea = Instance.new("Frame")
BotoesArea.Size = UDim2.new(1, 0, 0, 50)
BotoesArea.Position = UDim2.new(0, 0, 0, 60)
BotoesArea.BackgroundTransparency = 1
BotoesArea.Parent = Confirmar

local BtnSim = Instance.new("TextButton")
BtnSim.Size = UDim2.new(0, 90, 0, 32)
BtnSim.Position = UDim2.new(0.5, -95, 0, 0)
BtnSim.BackgroundColor3 = Color3.fromRGB(255, 80, 80)
BtnSim.Text = "SIM"
BtnSim.TextColor3 = Color3.new(1, 1, 1)
BtnSim.Font = Enum.Font.GothamBold
BtnSim.TextSize = 14
BtnSim.Parent = BotoesArea
Instance.new("UICorner", BtnSim).CornerRadius = UDim.new(0, 12)

local BtnNao = Instance.new("TextButton")
BtnNao.Size = UDim2.new(0, 90, 0, 32)
BtnNao.Position = UDim2.new(0.5, 5, 0, 0)
BtnNao.BackgroundColor3 = Color3.fromRGB(255, 180, 210)
BtnNao.Text = "NÃO"
BtnNao.TextColor3 = Color3.fromRGB(220, 100, 150)
BtnNao.Font = Enum.Font.GothamBold
BtnNao.TextSize = 14
BtnNao.Parent = BotoesArea
Instance.new("UICorner", BtnNao).CornerRadius = UDim.new(0, 12)

BtnFechar.MouseButton1Click:Connect(function() Confirmar.Visible = true end)
BtnNao.MouseButton1Click:Connect(function() Confirmar.Visible = false end)
BtnSim.MouseButton1Click:Connect(function() Menu:Destroy() end)

-- ==============================================
-- ✅ SISTEMA DE ARRASTE MOBILE (ANTI-BUG MULTITOUCH)
-- ==============================================
local function AtivarArrastavel(InstanciaClique, InstanciaMover)
    local Arrastando = false
    local InicioInput, PosicaoInicial
    local DedoPrincipal = nil

    InstanciaClique.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            if Arrastando then return end
            Arrastando = true
            DedoPrincipal = input
            InicioInput = input.Position
            PosicaoInicial = InstanciaMover.Position
        end
    end)

    UIS.InputChanged:Connect(function(input)
        if Arrastando and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
            if input == DedoPrincipal then
                local Delta = input.Position - InicioInput
                InstanciaMover.Position = UDim2.new(
                    PosicaoInicial.X.Scale, PosicaoInicial.X.Offset + Delta.X,
                    PosicaoInicial.Y.Scale, PosicaoInicial.Y.Offset + Delta.Y
                )
            end
        end
    end)

    UIS.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            if input == DedoPrincipal then
                Arrastando = false
                DedoPrincipal = nil
            end
        end
    end)
end

AtivarArrastavel(Cabecalho, Janela)

-- ==============================================
-- ✅ MENU LATERAL & ESTRUTURA DE ABAS (POSIÇÃO CORRIGIDA)
-- ==============================================
local MenuLateral = Instance.new("Frame")
MenuLateral.Size = UDim2.new(0, 95, 1, -60)
MenuLateral.Position = UDim2.new(0, 8, 0, 50) -- Começa logo abaixo do cabeçalho
MenuLateral.BackgroundColor3 = Color3.fromRGB(255, 230, 240)
MenuLateral.Parent = Janela
Instance.new("UICorner", MenuLateral).CornerRadius = UDim.new(0, 12)

local FuncoesAba = {}
local AbaAtual = "Player" -- Iniciando na Aba Player por padrão
local AnimAba = TweenInfo.new(0.15, Enum.EasingStyle.Quad)

local function CriarAba(Nome, PosicaoY)
    local BotaoAba = Instance.new("TextButton")
    BotaoAba.Size = UDim2.new(1, -10, 0, 35)
    BotaoAba.Position = UDim2.new(0, 5, 0, PosicaoY)
    BotaoAba.BackgroundColor3 = Nome == AbaAtual and Color3.fromRGB(255, 180, 210) or Color3.fromRGB(255, 240, 245)
    BotaoAba.Text = Nome
    BotaoAba.TextColor3 = Color3.fromRGB(200, 80, 130)
    BotaoAba.Font = Enum.Font.GothamBold
    BotaoAba.TextSize = 11
    BotaoAba.Parent = MenuLateral
    Instance.new("UICorner", BotaoAba).CornerRadius = UDim.new(0, 9)

    local AreaConteudo = Instance.new("Frame")
    AreaConteudo.Size = UDim2.new(0, 280, 0, 205)
    AreaConteudo.Position = UDim2.new(0, 110, 0, 50) -- Alinhado perfeitamente abaixo do cabeçalho
    AreaConteudo.BackgroundTransparency = 1
    AreaConteudo.Visible = Nome == AbaAtual
    AreaConteudo.Name = "Conteudo_"..Nome
    AreaConteudo.Parent = Janela

    FuncoesAba[Nome] = {Botao = BotaoAba, Conteudo = AreaConteudo}

    BotaoAba.MouseButton1Click:Connect(function()
        for N, Dados in pairs(FuncoesAba) do
            Tween:Create(Dados.Botao, AnimAba, {BackgroundColor3 = Color3.fromRGB(255, 240, 245)}):Play()
            Dados.Conteudo.Visible = false
        end
        Tween:Create(BotaoAba, AnimAba, {BackgroundColor3 = Color3.fromRGB(255, 180, 210)}):Play()
        AreaConteudo.Visible = true
        AbaAtual = Nome
    end)

    return AreaConteudo
end

-- ✅ GLOBAL: FUNÇÃO DE SWITCH TOGGLE DISPONÍVEL
local function CriarBotaoConfig(Texto, Ordem, EstadoInicial, LocalParent, Callback)
    local Botao = Instance.new("TextButton")
    Botao.Size = UDim2.new(1, -10, 0, 40)
    Botao.BackgroundColor3 = Color3.fromRGB(255, 225, 235)
    Botao.Text = "  ⚡ " .. Texto
    Botao.TextColor3 = Color3.fromRGB(200, 80, 130)
    Botao.Font = Enum.Font.GothamBold
    Botao.TextSize = 13
    Botao.TextXAlignment = Enum.TextXAlignment.Left
    Botao.LayoutOrder = Ordem
    Botao.AutoButtonColor = false
    Botao.Parent = LocalParent
    Instance.new("UICorner", Botao).CornerRadius = UDim.new(0, 8)

    local BordaBotao = Instance.new("UIStroke")
    BordaBotao.Thickness = 1
    BordaBotao.Color = Color3.fromRGB(255, 200, 215)
    BordaBotao.Parent = Botao

    local SwitchBg = Instance.new("Frame")
    SwitchBg.Size = UDim2.new(0, 40, 0, 20)
    SwitchBg.Position = UDim2.new(1, -50, 0.5, -10)
    SwitchBg.BackgroundColor3 = EstadoInicial and Color3.fromRGB(220, 100, 150) or Color3.fromRGB(200, 200, 200)
    SwitchBg.Parent = Botao
    Instance.new("UICorner", SwitchBg).CornerRadius = UDim.new(1, 0)

    local BolinhaBranca = Instance.new("Frame")
    BolinhaBranca.Size = UDim2.new(0, 16, 0, 16)
    BolinhaBranca.Position = EstadoInicial and UDim2.new(1, -18, 0.5, -8) or UDim2.new(0, 2, 0.5, -8)
    BolinhaBranca.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    BolinhaBranca.Parent = SwitchBg
    Instance.new("UICorner", BolinhaBranca).CornerRadius = UDim.new(1, 0)

    local Ativo = EstadoInicial
    local TweenInfoSwitch = TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)

    Botao.MouseButton1Click:Connect(function()
        Ativo = not Ativo
        local PosicaoAlvo = Ativo and UDim2.new(1, -18, 0.5, -8) or UDim2.new(0, 2, 0.5, -8)
        local CorAlvo = Ativo and Color3.fromRGB(220, 100, 150) or Color3.fromRGB(200, 200, 200)
        
        Tween:Create(BolinhaBranca, TweenInfoSwitch, {Position = PosicaoAlvo}):Play()
        Tween:Create(SwitchBg, TweenInfoSwitch, {BackgroundColor3 = CorAlvo}):Play()
        
        Callback(Ativo)
    end)
end

-- CRIAÇÃO DAS ABAS LATERAIS (ORDEM CORRETA E ALINHADAS)
local AbaPlayer = CriarAba("Player", 5)
local AbaTeleporte = CriarAba("Teleporte", 45)
local AbaConfig = CriarAba("Configurações", 85)

-- ==============================================
-- 🌀 2. ABA TELEPORTE (LISTA DINÂMICA DE PLAYERS)
-- ==============================================
local ScrollTeleporte = Instance.new("ScrollingFrame")
ScrollTeleporte.Size = UDim2.new(1, 0, 1, 0)
ScrollTeleporte.BackgroundTransparency = 1
ScrollTeleporte.ScrollBarThickness = 3
ScrollTeleporte.ScrollBarImageColor3 = Color3.fromRGB(255, 180, 200)
ScrollTeleporte.CanvasSize = UDim2.new(0, 0, 0, 300)
ScrollTeleporte.Parent = AbaTeleporte

local ListTeleport = Instance.new("UIListLayout")
ListTeleport.Padding = UDim.new(0, 8)
ListTeleport.SortOrder = Enum.SortOrder.LayoutOrder
ListTeleport.Parent = ScrollTeleporte

-- Botão Principal "TP Jogador"
local BotaoAbasLista = Instance.new("TextButton")
BotaoAbasLista.Size = UDim2.new(1, -10, 0, 40)
BotaoAbasLista.BackgroundColor3 = Color3.fromRGB(255, 225, 235)
BotaoAbasLista.Text = "  📍 TP Jogador"
BotaoAbasLista.TextColor3 = Color3.fromRGB(200, 80, 130)
BotaoAbasLista.Font = Enum.Font.GothamBold
BotaoAbasLista.TextSize = 13
BotaoAbasLista.TextXAlignment = Enum.TextXAlignment.Left
BotaoAbasLista.LayoutOrder = 1
BotaoAbasLista.Parent = ScrollTeleporte
Instance.new("UICorner", BotaoAbasLista).CornerRadius = UDim.new(0, 8)

local BordaTP = Instance.new("UIStroke")
BordaTP.Thickness = 1
BordaTP.Color = Color3.fromRGB(255, 200, 215)
BordaTP.Parent = BotaoAbasLista

-- Container que vai guardar a lista de nomes dos players
local FrameListaPlayers = Instance.new("Frame")
FrameListaPlayers.Size = UDim2.new(1, -10, 0, 0)
FrameListaPlayers.BackgroundTransparency = 1
FrameListaPlayers.LayoutOrder = 2
FrameListaPlayers.Visible = false
FrameListaPlayers.ClipsDescendants = true
FrameListaPlayers.Parent = ScrollTeleporte

local LayoutJogadores = Instance.new("UIListLayout")
LayoutJogadores.Padding = UDim.new(0, 4)
LayoutJogadores.SortOrder = Enum.SortOrder.Name
LayoutJogadores.Parent = FrameListaPlayers

local ListaAberta = false

-- Função para atualizar a lista de players dentro do menu
local function AtualizarListaPlayers()
    -- Limpa os botões antigos
    for _, filho in pairs(FrameListaPlayers:GetChildren()) do
        if filho:IsA("TextButton") then filho:Destroy() end
    end

    local AlturaTotal = 0
    
    -- Cria um botão para cada jogador no servidor (exceto você)
    for _, jogador in pairs(Players:GetPlayers()) do
        if jogador ~= Players.LocalPlayer then
            AlturaTotal = AlturaTotal + 34 -- Adiciona tamanho para o canvas ir crescendo
            
            local BotaoPlayer = Instance.new("TextButton")
            BotaoPlayer.Size = UDim2.new(1, 0, 0, 30)
            BotaoPlayer.BackgroundColor3 = Color3.fromRGB(255, 245, 248)
            BotaoPlayer.Text = "👤 " .. jogador.DisplayName .. " (@" .. jogador.Name .. ")"
            BotaoPlayer.TextColor3 = Color3.fromRGB(150, 70, 100)
            BotaoPlayer.Font = Enum.Font.Gotham
            BotaoPlayer.TextSize = 11
            BotaoPlayer.Parent = FrameListaPlayers
            Instance.new("UICorner", BotaoPlayer).CornerRadius = UDim.new(0, 6)
            
            local BordaP = Instance.new("UIStroke")
            BordaP.Thickness = 1
            BordaP.Color = Color3.fromRGB(255, 220, 230)
            BordaP.Parent = BotaoPlayer

            -- Sistema de Teleporte nas costas do alvo
            BotaoPlayer.MouseButton1Click:Connect(function()
                local MeuChar = Players.LocalPlayer.Character
                local AlvoChar = jogador.Character
                
                if MeuChar and AlvoChar and AlvoChar:FindFirstChild("HumanoidRootPart") and MeuChar:FindFirstChild("HumanoidRootPart") then
                    -- Calcula a posição exata de 3 studs atrás do jogador alvo
                    local HRPAlvo = AlvoChar.HumanoidRootPart
                    local PosicaoCostas = HRPAlvo.Position - (HRPAlvo.CFrame.LookVector * 3)
                    
                    -- Move o seu personagem olhando para a mesma direção que ele
                    MeuChar.HumanoidRootPart.CFrame = CFrame.new(PosicaoCostas, PosicaoCostas + HRPAlvo.CFrame.LookVector)
                end
            end)
        end
    end
    
    -- Atualiza o tamanho da caixa se ela estiver aberta
    if ListaAberta then
        FrameListaPlayers.Size = UDim2.new(1, -10, 0, AlturaTotal)
        ScrollTeleporte.CanvasSize = UDim2.new(0, 0, 0, AlturaTotal + 60)
    end
end

-- Abrir e fechar a lista ao clicar em "TP Jogador"
BotaoAbasLista.MouseButton1Click:Connect(function()
    ListaAberta = not ListaAberta
    
    if ListaAberta then
        AtualizarListaPlayers()
        FrameListaPlayers.Visible = true
        Tween:Create(FrameListaPlayers, TweenInfo.new(0.2, Enum.EasingStyle.Quad), {Size = UDim2.new(1, -10, 0, LayoutJogadores.AbsoluteContentSize.Y)}):Play()
    else
        local AnimFechar = Tween:Create(FrameListaPlayers, TweenInfo.new(0.2, Enum.EasingStyle.Quad), {Size = UDim2.new(1, -10, 0, 0)})
        AnimFechar:Play()
        AnimFechar.Completed:Connect(function()
            if not ListaAberta then
                FrameListaPlayers.Visible = false
                ScrollTeleporte.CanvasSize = UDim2.new(0, 0, 0, 300)
            end
        end)
    end
end)


-- Mantém a lista atualizada se alguém entrar ou sair do servidor
Players.PlayerAdded:Connect(function() if ListaAberta then task.wait(0.5) AtualizarListaPlayers() end end)
Players.PlayerRemoving:Connect(function() if ListaAberta then task.wait(0.5) AtualizarListaPlayers() end end)


-- ==============================================
-- 🏃 3. ABA PLAYER (REAPLICA AO MORRER)
-- ==============================================
local ScrollPlayer = Instance.new("ScrollingFrame")
ScrollPlayer.Size = UDim2.new(1, 0, 1, 0)
ScrollPlayer.BackgroundTransparency = 1
ScrollPlayer.ScrollBarThickness = 3
ScrollPlayer.ScrollBarImageColor3 = Color3.fromRGB(255, 180, 200)
ScrollPlayer.CanvasSize = UDim2.new(0, 0, 0, 420)
ScrollPlayer.Parent = AbaPlayer

local ListaPlayer = Instance.new("UIListLayout")
ListaPlayer.Padding = UDim.new(0, 8)
ListaPlayer.SortOrder = Enum.SortOrder.LayoutOrder
ListaPlayer.Parent = ScrollPlayer

local ValorWalkSpeed = 16  
local ValorJumpPower = 50  
local VelocidadeLigada = false
local SuperPuloLigado = false

local function AplicarStatus(Char)
    local Hum = Char:WaitForChild("Humanoid", 5)
    if Hum then
        if VelocidadeLigada then Hum.WalkSpeed = ValorWalkSpeed end
        if SuperPuloLigado then
            Hum.UseJumpPower = true
            Hum.JumpPower = ValorJumpPower
        end
    end
end

Players.LocalPlayer.CharacterAdded:Connect(function(NovoChar)
    task.wait(0.5)
    AplicarStatus(NovoChar)
end)

local function CriarControleCompleto(Texto, Ordem, Placeholder, EstadoInicial, CallbackSwitch)
    local Frame = Instance.new("Frame")
    Frame.Size = UDim2.new(1, -10, 0, 45)
    Frame.BackgroundColor3 = Color3.fromRGB(255, 230, 240)
    Frame.LayoutOrder = Ordem
    Frame.Parent = ScrollPlayer
    Instance.new("UICorner", Frame).CornerRadius = UDim.new(0, 8)

    local BordaBotao = Instance.new("UIStroke")
    BordaBotao.Thickness = 1
    BordaBotao.Color = Color3.fromRGB(255, 200, 215)
    BordaBotao.Parent = Frame

    local Label = Instance.new("TextLabel")
    Label.Size = UDim2.new(0.4, 0, 1, 0)
    Label.Position = UDim2.new(0, 10, 0, 0)
    Label.Text = "⚡ " .. Texto
    Label.TextColor3 = Color3.fromRGB(200, 80, 130)
    Label.Font = Enum.Font.GothamBold
    Label.TextSize = 12
    Label.TextXAlignment = Enum.TextXAlignment.Left
    Label.BackgroundTransparency = 1
    Label.Parent = Frame

    local Box = Instance.new("TextBox")
    Box.Size = UDim2.new(0.2, 0, 0.6, 0)
    Box.Position = UDim2.new(0.45, 0, 0.2, 0)
    Box.BackgroundColor3 = Color3.new(1, 1, 1)
    Box.PlaceholderText = Placeholder
    Box.Text = ""
    Box.Font = Enum.Font.GothamBold
    Box.TextSize = 11
    Box.TextColor3 = Color3.fromRGB(100, 100, 100)
    Box.Parent = Frame
    Instance.new("UICorner", Box).CornerRadius = UDim.new(0, 6)

    local SwitchBg = Instance.new("TextButton")
    SwitchBg.Size = UDim2.new(0, 40, 0, 20)
    SwitchBg.Position = UDim2.new(1, -50, 0.5, -10)
    SwitchBg.BackgroundColor3 = EstadoInicial and Color3.fromRGB(220, 100, 150) or Color3.fromRGB(200, 200, 200)
    SwitchBg.Text = ""
    SwitchBg.AutoButtonColor = false
    SwitchBg.Parent = Frame
    Instance.new("UICorner", SwitchBg).CornerRadius = UDim.new(1, 0)

    local BolinhaBranca = Instance.new("Frame")
    BolinhaBranca.Size = UDim2.new(0, 16, 0, 16)
    BolinhaBranca.Position = EstadoInicial and UDim2.new(1, -18, 0.5, -8) or UDim2.new(0, 2, 0.5, -8)
    BolinhaBranca.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    BolinhaBranca.Parent = SwitchBg
    Instance.new("UICorner", BolinhaBranca).CornerRadius = UDim.new(1, 0)

    local Ativo = EstadoInicial
    local TweenInfoSwitch = TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)

    SwitchBg.MouseButton1Click:Connect(function()
        Ativo = not Ativo
        local PosicaoAlvo = Ativo and UDim2.new(1, -18, 0.5, -8) or UDim2.new(0, 2, 0.5, -8)
        local CorAlvo = Ativo and Color3.fromRGB(220, 100, 150) or Color3.fromRGB(200, 200, 200)
        
        Tween:Create(BolinhaBranca, TweenInfoSwitch, {Position = PosicaoAlvo}):Play()
        Tween:Create(SwitchBg, TweenInfoSwitch, {BackgroundColor3 = CorAlvo}):Play()
        
        CallbackSwitch(Ativo, Box.Text)
    end)
    
    Box.FocusLost:Connect(function()
        if Ativo then CallbackSwitch(true, Box.Text) end
    end)
end

CriarControleCompleto("Velocidade", 1, "Ex: 50", false, function(ativo, texto)
    local num = tonumber(texto)
    if num then ValorWalkSpeed = num end
    VelocidadeLigada = ativo
    local char = Players.LocalPlayer.Character
    local hum = char and char:FindFirstChild("Humanoid")
    if hum then hum.WalkSpeed = ativo and ValorWalkSpeed or 16 end
end)

CriarControleCompleto("Super Pulo", 2, "Ex: 100", false, function(ativo, texto)
    local num = tonumber(texto)
    if num then ValorJumpPower = num end
    SuperPuloLigado = ativo
    local char = Players.LocalPlayer.Character
    local hum = char and char:FindFirstChild("Humanoid")
    if hum then
        if ativo then
            hum.UseJumpPower = true
            hum.JumpPower = ValorJumpPower
        else
            hum.JumpPower = 50
        end
    end
end)

CriarBotaoConfig("Pulo Infinito", 3, false, ScrollPlayer, function(ativo)
    _G.InfJump = ativo
    if not _G.InfJumpHooked then
        _G.InfJumpHooked = true
        UIS.JumpRequest:Connect(function()
            if _G.InfJump and Players.LocalPlayer.Character and Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid") then
                Players.LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):ChangeState(3)
            end
        end)
    end
end)

CriarBotaoConfig("Clique Rápido", 4, false, ScrollPlayer, function(ativo)
    _G.FastClick = ativo
end)

CriarBotaoConfig("Atravessa Parede", 5, false, ScrollPlayer, function(ativo)
    _G.Noclip = ativo
    if not _G.NoclipHooked then
        _G.NoclipHooked = true
        game:GetService("RunService").Stepped:Connect(function()
            if _G.Noclip and Players.LocalPlayer.Character then
                for _, v in pairs(Players.LocalPlayer.Character:GetChildren()) do
                    if v:IsA("BasePart") then v.CanCollide = false end
                end
            end
        end)
    end
end)

CriarBotaoConfig("Ver no Escuro", 6, false, ScrollPlayer, function(ativo)
    local lighting = game:GetService("Lighting")
    if ativo then
        lighting.Brightness = 5
        lighting.ClockTime = 14
        lighting.GlobalShadows = false
        lighting.OutdoorAmbient = Color3.fromRGB(255, 255, 255)
    else
        lighting.Brightness = 1
        lighting.GlobalShadows = true
        lighting.OutdoorAmbient = Color3.fromRGB(128, 128, 128)
    end
end)

-- ==============================================
-- 👁️ FUNÇÃO: VER JOGADORES (ESP / WALLHACK / AURA) - ATUALIZADO
-- ==============================================
local EspAtivo = false
local ConexoesESP = {}

-- Função que cria a aura e o texto na cabeça de um jogador específico
local function CriarESP(jogador)
    if jogador == Players.LocalPlayer then return end

    local function AdicionarEfeitos(char)
        -- Remove efeitos antigos se existirem para não acumular
        if char:FindFirstChild("Sasaki_Esp") then char.Sasaki_Esp:Destroy() end
        if char:FindFirstChild("Sasaki_Aura") then char.Sasaki_Aura:Destroy() end

        local hrp = char:WaitForChild("HumanoidRootPart", 5)
        local head = char:WaitForChild("Head", 5)
        if not hrp or not head then return end

        -- 1. CRIAR A AURA (HIGHLIGHT) QUE VÊ ATRAVÉS DA PAREDE E DA TRANSPARÊNCIA
        local Aura = Instance.new("Highlight")
        Aura.Name = "Sasaki_Aura"
        Aura.FillColor = Color3.fromRGB(255, 180, 210) -- Cor interna rosa
        Aura.FillTransparency = 0.5 -- Transparência de dentro fixa (aparece mesmo se o char for invisível)
        Aura.OutlineColor = Color3.fromRGB(220, 100, 150) -- Cor da borda
        Aura.OutlineTransparency = 0 -- Borda bem visível
        Aura.Adornee = char
        Aura.Parent = char

        -- 2. CRIAR O TEXTO DE NOME E DISTÂNCIA (BILLBOARDGUI)
        local BoxTexto = Instance.new("BillboardGui")
        BoxTexto.Name = "Sasaki_Esp"
        BoxTexto.Adornee = head
        BoxTexto.Size = UDim2.new(0, 150, 0, 35)
        BoxTexto.StudsOffset = Vector3.new(0, 2.5, 0) -- Distância acima da cabeça
        BoxTexto.AlwaysOnTop = true -- Sempre visível na tela (ignora paredes e transparência do modelo)
        BoxTexto.Parent = char

        local LabelTexto = Instance.new("TextLabel")
        LabelTexto.Size = UDim2.new(1, 0, 1, 0)
        LabelTexto.BackgroundTransparency = 1
        LabelTexto.TextColor3 = Color3.fromRGB(255, 255, 255)
        LabelTexto.Font = Enum.Font.GothamBold
        LabelTexto.TextSize = 11
        LabelTexto.TextStrokeTransparency = 0 -- Borda preta no texto para ler fácil
        LabelTexto.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
        LabelTexto.Parent = BoxTexto

        -- Loop para ficar atualizando a distância em tempo real
        local ConexaoLoop
        ConexaoLoop = game:GetService("RunService").RenderStepped:Connect(function()
            if not EspAtivo or not char.Parent or not hrp.Parent then
                ConexaoLoop:Disconnect()
                return
            end
            
            local MeuChar = Players.LocalPlayer.Character
            if MeuChar and MeuChar:FindFirstChild("HumanoidRootPart") then
                -- Calcula a distância em metros/studs
                local Distancia = math.floor((MeuChar.HumanoidRootPart.Position - hrp.Position).Magnitude)
                -- Formato limpo: Nome de exibição na linha de cima e os metros (M) na de baixo
                LabelTexto.Text = string.format("%s\n%dM", jogador.DisplayName, Distancia)
            end
        end)
    end

    -- Se o personagem já existir, aplica. Se não, espera carregar
    if jogador.Character then task.spawn(AdicionarEfeitos, jogador.Character) end
    local ConexaoChar = jogador.CharacterAdded:Connect(function(char)
        task.wait(0.5)
        if EspAtivo then AdicionarEfeitos(char) end
    end)
    
    table.insert(ConexoesESP, ConexaoChar)
end

-- Limpa tudo quando a função é desligada
local function LimparTodosESP()
    for _, conexao in pairs(ConexoesESP) do conexao:Disconnect() end
    ConexoesESP = {}

    for _, jogador in pairs(Players:GetPlayers()) do
        if jogador.Character then
            if jogador.Character:FindFirstChild("Sasaki_Esp") then jogador.Character.Sasaki_Esp:Destroy() end
            if jogador.Character:FindFirstChild("Sasaki_Aura") then jogador.Character.Sasaki_Aura:Destroy() end
        end
    end
end

-- Criando o Botão Switch na sua Aba Player
CriarBotaoConfig("Ver Jogadores (ESP)", 7, false, ScrollPlayer, function(ativo)
    EspAtivo = ativo
    
    if ativo then
        -- Ativa para quem já está no servidor
        for _, jogador in pairs(Players:GetPlayers()) do
            CriarESP(jogador)
        end
        
        -- Escuta se novos jogadores entrarem no servidor para ativar neles também
        local EntradaConexao = Players.PlayerAdded:Connect(function(novoJogador)
            if EspAtivo then CriarESP(novoJogador) end
        end)
        table.insert(ConexoesESP, EntradaConexao)
    else
        LimparTodosESP()
    end
end)

-- ==============================================
-- 🚀 FUNÇÃO: FLY INTEGRADO COM VELOCIDADE E BOTÕES UP/DOWN (CORRIGIDO)
-- ==============================================
local VoadorAtivo = false
local VelocidadeVoo = 50
local Subindo = false
local Descendo = false
local ConexaoVoo

local Camera = workspace.CurrentCamera

-- Interface dos botões de subir/descer (Criados direto no Menu para organização)
local BtnSubir = Instance.new("TextButton")
BtnSubir.Size = UDim2.new(0, 55, 0, 55)
BtnSubir.Position = UDim2.new(1, -70, 0.5, -60)
BtnSubir.BackgroundColor3 = Color3.fromRGB(255, 180, 210)
BtnSubir.Text = "▲"
BtnSubir.TextColor3 = Color3.fromRGB(220, 100, 150)
BtnSubir.Font = Enum.Font.GothamBold
BtnSubir.TextSize = 24
BtnSubir.Visible = false
BtnSubir.Parent = Menu
Instance.new("UICorner", BtnSubir).CornerRadius = UDim.new(1, 0)
Instance.new("UIStroke", BtnSubir).Color = Color3.fromRGB(220, 100, 150)

local BtnDescer = Instance.new("TextButton")
BtnDescer.Size = UDim2.new(0, 55, 0, 55)
BtnDescer.Position = UDim2.new(1, -70, 0.5, 10)
BtnDescer.BackgroundColor3 = Color3.fromRGB(255, 180, 210)
BtnDescer.Text = "▼"
BtnDescer.TextColor3 = Color3.fromRGB(220, 100, 150)
BtnDescer.Font = Enum.Font.GothamBold
BtnDescer.TextSize = 24
BtnDescer.Visible = false
BtnDescer.Parent = Menu
Instance.new("UICorner", BtnDescer).CornerRadius = UDim.new(1, 0)
Instance.new("UIStroke", BtnDescer).Color = Color3.fromRGB(220, 100, 150)

-- Configuração do toque para segurar e soltar os botões no Mobile
BtnSubir.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then Subindo = true end
end)
BtnSubir.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then Subindo = false end
end)

BtnDescer.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then Descendo = true end
end)
BtnDescer.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then Descendo = false end
end)

local function IniciarVoo()
    local Character = Players.LocalPlayer.Character
    if not Character then return end
    local HRP = Character:WaitForChild("HumanoidRootPart", 5)
    local Hum = Character:FindFirstChildOfClass("Humanoid")
    if not HRP or not Hum then return end

    Hum.PlatformStand = true

    local ForcaMovimento = Instance.new("BodyVelocity")
    ForcaMovimento.Name = "Sasaki_ForcaVoo"
    ForcaMovimento.Velocity = Vector3.new(0, 0, 0)
    ForcaMovimento.MaxForce = Vector3.new(math.huge, math.huge, math.huge)
    ForcaMovimento.Parent = HRP

    BtnSubir.Visible = true
    BtnDescer.Visible = true

    ConexaoVoo = game:GetService("RunService").RenderStepped:Connect(function()
        if not VoadorAtivo or not HRP.Parent or not Hum.Parent then
            if ConexaoVoo then ConexaoVoo:Disconnect() end
            return
        end

        -- Antibug de colisão (Noclip ativo ao voar)
        for _, parte in pairs(Character:GetChildren()) do
            if parte:IsA("BasePart") then parte.CanCollide = false end
        end

        -- Giro rápido acompanhando a câmera
        local CamLook = Camera.CFrame.LookVector
        HRP.CFrame = CFrame.new(HRP.Position, HRP.Position + Vector3.new(CamLook.X, CamLook.Y, CamLook.Z))

        -- Movimento analógico
        local DirecaoMove = Hum.MoveDirection
        local VetorVelocidade = DirecaoMove * VelocidadeVoo

        -- Subida e descida via botões verticais na tela
        local EixoY = 0
        if Subindo then
            EixoY = VelocidadeVoo
        elseif Descendo then
            EixoY = -VelocidadeVoo
        end

        ForcaMovimento.Velocity = Vector3.new(VetorVelocidade.X, EixoY, VetorVelocidade.Z)
        Hum.PlatformStand = true
    end)
end

local function DesativarVoo()
    VoadorAtivo = false
    BtnSubir.Visible = false
    BtnDescer.Visible = false
    if ConexaoVoo then ConexaoVoo:Disconnect() end
    
    local Character = Players.LocalPlayer.Character
    if Character then
        local HRP = Character:FindFirstChild("HumanoidRootPart")
        if HRP and HRP:FindFirstChild("Sasaki_ForcaVoo") then HRP.Sasaki_ForcaVoo:Destroy() end
        
        local Hum = Character:FindFirstChildOfClass("Humanoid")
        if Hum then Hum.PlatformStand = false end
        
        for _, parte in pairs(Character:GetChildren()) do
            if parte:IsA("BasePart") then parte.CanCollide = true end
        end
    end
end

-- Usa ordem fracionada (2.5) para forçar a inserção perfeita entre o Super Pulo (2) e o Pulo Infinito (3)
CriarControleCompleto("Voar", 2.5, "Ex: 50", false, function(ativo, texto)
    local num = tonumber(texto)
    if num then VelocidadeVoo = num else VelocidadeVoo = 50 end
    
    VoadorAtivo = ativo
    if ativo then
        IniciarVoo()
    else
        DesativarVoo()
    end
end)

-- Desativa ao morrer
Players.LocalPlayer.CharacterAdded:Connect(function()
    if VoadorAtivo then DesativarVoo() end
end)

-- ==============================================
-- ⚙️ 4. ABA CONFIGURAÇÕES
-- ==============================================
local ScrollConfig = Instance.new("ScrollingFrame")
ScrollConfig.Size = UDim2.new(1, 0, 1, 0)
ScrollConfig.BackgroundTransparency = 1
ScrollConfig.ScrollBarThickness = 3
ScrollConfig.ScrollBarImageColor3 = Color3.fromRGB(255, 180, 200)
ScrollConfig.CanvasSize = UDim2.new(0, 0, 0, 260)
ScrollConfig.Parent = AbaConfig

local ListaLayout = Instance.new("UIListLayout")
ListaLayout.Padding = UDim.new(0, 8)
ListaLayout.SortOrder = Enum.SortOrder.LayoutOrder
ListaLayout.Parent = ScrollConfig

CriarBotaoConfig("Menu Transparente", 1, false, ScrollConfig, function(estado)
    if estado then
        Janela.BackgroundTransparency = 0.4
        MenuLateral.BackgroundTransparency = 0.5
        Cabecalho.BackgroundTransparency = 0.3
    else
        Janela.BackgroundTransparency = 0
        MenuLateral.BackgroundTransparency = 0
        Cabecalho.BackgroundTransparency = 0
    end
end)

-- ==============================================
-- ✅ BOLINHA FLUTUANTE DE CONTROLE E ANIMAÇÕES
-- ==============================================
local Bolinha = Instance.new("TextButton")
Bolinha.Size = UDim2.new(0, 50, 0, 50)
Bolinha.Position = UDim2.new(0, 20, 0, 100)
Bolinha.BackgroundColor3 = Color3.fromRGB(255, 180, 210)
Bolinha.Text = "🎀"
Bolinha.TextSize = 24
Bolinha.Font = Enum.Font.GothamBold
Bolinha.Parent = Menu
Instance.new("UICorner", Bolinha).CornerRadius = UDim.new(1, 0)

local SombraBola = Instance.new("UIStroke")
SombraBola.Thickness = 2
SombraBola.Color = Color3.fromRGB(220, 100, 150)
SombraBola.Parent = Bolinha

AtivarArrastavel(Bolinha, Bolinha)

local Aberto = false
local AnimInfo = TweenInfo.new(0.3, Enum.EasingStyle.Back, Enum.EasingDirection.Out)
local AnimInfoFechar = TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.In)

Bolinha.MouseButton1Click:Connect(function()
    Aberto = not Aberto
    if Aberto then
        Janela.Size = UDim2.new(0, 0, 0, 0)
        Janela.Visible = true
        Tween:Create(Janela, AnimInfo, {Size = UDim2.new(0, 400, 0, 270)}):Play()
    else
        local FecharTween = Tween:Create(Janela, AnimInfoFechar, {Size = UDim2.new(0, 0, 0, 0)})
        FecharTween:Play()
        FecharTween.Completed:Connect(function()
            if not Aberto then Janela.Visible = false end
        end)
    end
end)
