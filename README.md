<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>VULPS+ · Planejamento para Concursos</title>
  <link rel="preconnect" href="https://cdnjs.cloudflare.com">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/fontawesome.min.css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/solid.min.css">
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1"></script>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --accent-primary: #00D9E8;
      --accent-secondary: #00C2D1;
      --accent-strong: #007F8C;
      --accent-soft: rgba(0, 217, 232, 0.12);
      --accent-glow: rgba(0, 217, 232, 0.25);
      --bg-primary: #0D141C;
      --bg-secondary: #0F1720;
      --bg-card: #121C26;
      --text-primary: #F0F8FF;
      --text-secondary: #B0E5EB;
      --text-muted: #7FB8C0;
      --border-light: #1F2E3A;
      --border-hover: #00D9E8;
      --success: #22C55E;
      --danger: #EF4444;
      --warning: #F59E0B;
      --radius-sm: 12px;
      --radius-lg: 24px;
      --card-shadow: 0 8px 20px rgba(0, 0, 0, 0.5);
    }

    html[data-theme="light"] {
      --bg-primary: #F0F7F9;
      --bg-secondary: #E1F0F3;
      --bg-card: #FFFFFF;
      --border-light: #C5E0E5;
      --border-hover: #00C2D1;
      --text-primary: #0A1A1F;
      --text-secondary: #1A3D47;
      --text-muted: #4A7B85;
      --accent-primary: #007F8C;
      --accent-secondary: #006B75;
      --accent-strong: #005A63;
      --accent-soft: rgba(0, 127, 140, 0.1);
      --accent-glow: rgba(0, 127, 140, 0.2);
      --card-shadow: 0 8px 20px rgba(0, 0, 0, 0.06);
    }

    body {
      font-family: 'Segoe UI', 'Roboto', system-ui, sans-serif;
      background: var(--bg-primary);
      color: var(--text-primary);
      padding: 24px 16px;
      line-height: 1.5;
      transition: background-color 0.2s, color 0.2s;
    }

    .app-container {
      max-width: 1000px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 24px;
    }

    .app-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      margin-bottom: 4px;
      border-bottom: 2px solid var(--accent-primary);
      padding-bottom: 16px;
    }

    .header-brand {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .brand-logo {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 48px;
      height: 48px;
      background: linear-gradient(135deg, var(--accent-primary), var(--accent-strong));
      border-radius: 14px;
      box-shadow: 0 4px 12px var(--accent-glow);
    }

    .brand-logo svg { width: 32px; height: 32px; }

    .brand-text h1 {
      font-weight: 650;
      font-size: 1.8rem;
      background: linear-gradient(135deg, var(--text-primary) 0%, var(--accent-primary) 80%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      line-height: 1.2;
    }

    .brand-text p { color: var(--text-secondary); font-size: 0.9rem; }

    .card {
      background: var(--bg-card);
      border-radius: var(--radius-lg);
      padding: 24px 22px;
      box-shadow: var(--card-shadow);
      border: 1px solid var(--border-light);
    }

    h2 {
      font-size: 1.4rem;
      font-weight: 600;
      margin-bottom: 18px;
      color: var(--text-primary);
      display: flex;
      align-items: center;
      gap: 8px;
      border-bottom: 1px solid var(--border-light);
      padding-bottom: 12px;
    }

    h2 i { color: var(--accent-primary); }

    h3 { font-weight: 600; font-size: 1.1rem; margin-bottom: 12px; color: var(--text-primary); }

    .btn {
      background: var(--bg-card);
      border: 1.5px solid var(--border-light);
      border-radius: 40px;
      padding: 10px 22px;
      font-weight: 600;
      font-size: 0.95rem;
      color: var(--text-primary);
      cursor: pointer;
      box-shadow: var(--card-shadow);
      transition: all 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .btn:disabled { opacity: 0.6; pointer-events: none; }

    .btn-primary {
      background: linear-gradient(135deg, var(--accent-primary), var(--accent-strong));
      border: none;
      color: #0A1418;
      font-weight: 700;
    }

    .btn-primary:hover:not(:disabled) {
      background: linear-gradient(135deg, #00F0FF, var(--accent-primary));
      transform: translateY(-2px);
    }

    .btn-outline:hover:not(:disabled) {
      background: var(--accent-soft);
      border-color: var(--accent-primary);
    }

    .btn-success { background: rgba(34, 197, 94, 0.15); border-color: var(--success); color: var(--success); }
    .btn-success:hover { background: var(--success); color: white; }

    .badge {
      background: var(--accent-soft);
      padding: 4px 10px;
      border-radius: 30px;
      font-size: 0.8rem;
      font-weight: 600;
      color: var(--accent-primary);
      border: 1px solid var(--accent-primary);
    }

    .flex-row {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
    }

    #theme-toggle {
      background: var(--bg-card);
      border: 1px solid var(--border-light);
      border-radius: 40px;
      padding: 8px 16px;
      color: var(--text-primary);
      display: flex;
      align-items: center;
      gap: 8px;
      cursor: pointer;
    }

    .theme-text { display: none; }
    @media (min-width: 600px) { .theme-text { display: inline; } }

    @media (max-width: 480px) {
      body { padding: 16px 10px; }
      .card { padding: 18px 14px; }
      .btn { padding: 12px 16px; }
    }

    .metrics-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
      gap: 16px;
      margin-top: 16px;
    }

    .metric-card {
      background: var(--bg-secondary);
      border-radius: 16px;
      padding: 16px;
      border: 1px solid var(--border-light);
      text-align: center;
    }

    .metric-value { font-size: 2rem; font-weight: 700; color: var(--accent-primary); }
    .metric-label { font-size: 0.8rem; color: var(--text-muted); text-transform: uppercase; }

    .task-list {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-top: 16px;
    }

    .task-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 16px;
      background: var(--bg-secondary);
      border-radius: var(--radius-lg);
      border: 1px solid var(--border-light);
      transition: all 0.2s;
    }

    .task-item.completed {
      opacity: 0.7;
      background: var(--accent-soft);
      border-color: var(--success);
    }

    .task-info {
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    .task-subject { font-weight: 600; }
    .task-duration { font-size: 0.85rem; color: var(--text-muted); }

    .task-actions {
      display: flex;
      gap: 8px;
    }

    .progress-bar {
      width: 100%;
      height: 8px;
      background: var(--border-light);
      border-radius: 4px;
      margin: 16px 0;
    }

    .progress-fill {
      height: 100%;
      background: var(--accent-primary);
      border-radius: 4px;
      transition: width 0.3s;
    }

    .subjects-grid {
      display: flex;
      flex-direction: column;
      gap: 8px;
      max-height: 350px;
      overflow-y: auto;
      padding: 4px;
      margin: 16px 0;
    }

    .subject-category {
      margin-top: 12px;
    }

    .subject-category h4 {
      color: var(--accent-primary);
      margin-bottom: 8px;
      font-size: 0.9rem;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }

    .subject-item {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 8px 10px;
      background: var(--bg-secondary);
      border-radius: var(--radius-sm);
      border: 1px solid var(--border-light);
    }

    .subject-item input[type="checkbox"] {
      accent-color: var(--accent-primary);
      width: 18px;
      height: 18px;
    }

    .subject-weight {
      width: 60px;
      margin-left: auto;
      padding: 4px 8px;
      border: 1px solid var(--border-light);
      border-radius: 20px;
      background: var(--bg-card);
      color: var(--text-primary);
      text-align: center;
    }

    .modal-overlay {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: rgba(0,0,0,0.7);
      backdrop-filter: blur(4px);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 1000;
    }

    .modal-card {
      background: var(--bg-card);
      max-width: 600px;
      width: 90%;
      max-height: 80vh;
      overflow-y: auto;
      border-radius: 28px;
      padding: 24px;
      border: 2px solid var(--accent-primary);
    }

    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    input, select {
      width: 100%;
      padding: 12px 14px;
      border: 1.5px solid var(--border-light);
      border-radius: var(--radius-sm);
      font-size: 1rem;
      background: var(--bg-secondary);
      color: var(--text-primary);
      margin-bottom: 12px;
    }

    .template-buttons {
      display: flex;
      gap: 8px;
      margin-bottom: 16px;
    }

    .toast {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: var(--bg-card);
      color: var(--text-primary);
      padding: 12px 24px;
      border-radius: 40px;
      border-left: 4px solid var(--accent-primary);
      box-shadow: var(--card-shadow);
      z-index: 9999;
      animation: slideUp 0.3s;
    }

    @keyframes slideUp {
      from { opacity: 0; transform: translateX(-50%) translateY(20px); }
      to { opacity: 1; transform: translateX(-50%) translateY(0); }
    }

    .empty-state {
      text-align: center;
      padding: 40px 20px;
      color: var(--text-muted);
    }

    .empty-state i { font-size: 3rem; margin-bottom: 16px; opacity: 0.5; }

    .timer-display {
      font-size: 3rem;
      font-weight: 700;
      text-align: center;
      color: var(--accent-primary);
      margin: 20px 0;
    }

    .active-task-card {
      background: var(--accent-soft);
      border: 2px solid var(--accent-primary);
      border-radius: var(--radius-lg);
      padding: 24px;
      text-align: center;
    }

    .remaining-time {
      text-align: center;
      margin-top: 8px;
      font-size: 0.9rem;
      color: var(--text-secondary);
    }

    .weekly-chart {
      display: flex;
      justify-content: space-around;
      margin-top: 20px;
    }

    .chart-bar {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;
    }

    .bar {
      width: 30px;
      height: 100px;
      background: var(--border-light);
      border-radius: 8px;
      overflow: hidden;
      display: flex;
      flex-direction: column-reverse;
    }

    .bar-fill {
      background: var(--accent-primary);
      width: 100%;
      transition: height 0.3s;
    }

    .bar-label {
      font-size: 0.7rem;
      color: var(--text-muted);
    }
  </style>
</head>
<body>
<div class="app-container">
  
  <div class="app-header">
    <div class="header-brand">
      <div class="brand-logo">
        <svg viewBox="0 0 40 40" fill="none">
          <path d="M8 12L20 6L32 12V28L20 34L8 28V12Z" fill="#0D141C" stroke="white" stroke-width="2"/>
          <text x="20" y="26" font-size="20" font-weight="700" text-anchor="middle" fill="white" font-family="Segoe UI">V+</text>
        </svg>
      </div>
      <div class="brand-text">
        <h1>VULPS+ Planner</h1>
        <p>Planejamento inteligente para concursos</p>
      </div>
    </div>
    <div style="display: flex; gap: 10px;">
      <button id="theme-toggle">
        <i class="fas" id="theme-icon">🌙</i>
        <span class="theme-text">Escuro</span>
      </button>
    </div>
  </div>

  <!-- Dashboard -->
  <div class="card">
    <h2><i class="fas fa-chart-line"></i> Seu Progresso</h2>
    <div class="metrics-grid">
      <div class="metric-card">
        <div class="metric-value" id="todayTime">0min</div>
        <div class="metric-label">Hoje</div>
      </div>
      <div class="metric-card">
        <div class="metric-value" id="todayTasks">0/0</div>
        <div class="metric-label">Tarefas</div>
      </div>
      <div class="metric-card">
        <div class="metric-value" id="completionRate">0%</div>
        <div class="metric-label">Conclusão</div>
      </div>
      <div class="metric-card">
        <div class="metric-value" id="currentStreak">0🔥</div>
        <div class="metric-label">Streak</div>
      </div>
    </div>
    
    <!-- Gráfico semanal -->
    <div style="margin-top: 20px;">
      <h3><i class="fas fa-calendar-week"></i> Últimos 7 dias</h3>
      <div class="weekly-chart" id="weeklyChart"></div>
    </div>
  </div>

  <!-- Plano do Dia -->
  <div class="card">
    <div class="flex-row">
      <h2 style="border-bottom: none; padding-bottom: 0; margin-bottom: 0;"><i class="fas fa-calendar-day"></i> Plano de Hoje</h2>
      <div style="display: flex; gap: 10px;">
        <button class="btn btn-outline" id="configBtn"><i class="fas fa-cog"></i> Configurar</button>
        <button class="btn btn-primary" id="generatePlanBtn"><i class="fas fa-magic"></i> Gerar Plano</button>
      </div>
    </div>
    
    <div class="progress-bar">
      <div class="progress-fill" id="dailyProgress" style="width: 0%;"></div>
    </div>
    
    <div class="remaining-time" id="remainingTimeDisplay"></div>
    
    <div id="planContainer">
      <div class="empty-state">
        <i class="fas fa-clipboard-list"></i>
        <p>Configure seu plano de estudos</p>
        <button class="btn btn-primary" id="setupPlanBtn" style="margin-top: 16px;">
          <i class="fas fa-plus"></i> Configurar Agora
        </button>
      </div>
    </div>
  </div>

  <!-- Tarefa Ativa -->
  <div class="card" id="activeTaskCard" style="display: none;">
    <div class="flex-row">
      <h2 style="border-bottom: none; padding-bottom: 0;"><i class="fas fa-play-circle"></i> Estudando Agora</h2>
      <div style="display: flex; gap: 8px;">
        <button class="btn btn-outline" id="skipTaskBtn"><i class="fas fa-forward"></i> Pular</button>
        <button class="btn btn-outline" id="closeTaskBtn"><i class="fas fa-times"></i></button>
      </div>
    </div>
    <div class="active-task-card">
      <h3 id="activeSubject">Direito Constitucional</h3>
      <div class="timer-display" id="taskTimer">30:00</div>
      <p style="color: var(--text-muted);">Tempo planejado: <span id="plannedTime">30</span> min</p>
      <p style="color: var(--text-muted);">Tempo estudado: <span id="actualTime">0</span> min</p>
      <div style="display: flex; gap: 12px; justify-content: center; margin-top: 24px;">
        <button class="btn btn-success" id="completeTaskBtn"><i class="fas fa-check"></i> Concluir Tarefa</button>
      </div>
    </div>
  </div>

  <!-- Matérias mais estudadas -->
  <div class="card">
    <h2><i class="fas fa-trophy"></i> Matérias mais estudadas</h2>
    <div id="topSubjectsContainer" class="task-list">
      <div class="empty-state">Complete tarefas para ver estatísticas</div>
    </div>
  </div>

  <!-- Modal Configuração -->
  <div class="modal-overlay" id="configModal">
    <div class="modal-card">
      <div class="modal-header">
        <h3>⚙️ Configurar Plano de Estudos</h3>
        <button class="btn btn-outline" onclick="window.closeConfigModal()"><i class="fas fa-times"></i></button>
      </div>
      
      <label>Tempo diário disponível (minutos)</label>
      <input type="number" id="dailyTimeInput" value="120" min="30" max="480" step="15">
      
      <label>Templates rápidos</label>
      <div class="template-buttons">
        <button class="btn btn-outline" data-template="juridico">⚖️ Concursos Jurídicos</button>
        <button class="btn btn-outline" data-template="fiscal">💰 Concursos Fiscais</button>
        <button class="btn btn-outline" data-template="administrativo">🏛️ Área Administrativa</button>
      </div>
      
      <label>Buscar matérias</label>
      <input type="text" id="subjectSearch" placeholder="Digite para filtrar...">
      
      <label>Selecione suas matérias e defina os pesos (1-5)</label>
      <p style="font-size:0.8rem; color: var(--text-muted); margin-bottom: 8px;">Peso maior = mais tempo de estudo</p>
      
      <div class="subjects-grid" id="subjectsGrid"></div>
      
      <div class="flex-row" style="margin-top: 20px;">
        <button class="btn btn-primary" id="saveConfigBtn">Salvar Configuração</button>
        <button class="btn btn-outline" onclick="window.closeConfigModal()">Cancelar</button>
      </div>
    </div>
  </div>
</div>

<script>
  (function(){
    "use strict";

    const DISCIPLINAS = [
      "Acessibilidade", "Administração", "Administração da Produção", "Administração de Materiais",
      "Administração de Pessoal", "Administração Estratégica", "Administração Financeira",
      "Administração Financeira e Orçamentária (AFO)", "Administração Geral", "Administração Pública",
      "Administração de Recursos Humanos", "Administração de Recursos Materiais", "Administração Tributária",
      "Análise de Sistemas", "Antropologia", "Arquivologia", "Artes", "Atualidades", "Auditoria",
      "Auditoria Governamental", "Biblioteconomia", "Biologia", "Biomedicina", "Ciência Política",
      "Ciências Contábeis", "Comércio Internacional", "Comunicação Social", "Conhecimentos Bancários",
      "Conhecimentos Específicos", "Conhecimentos Gerais", "Contabilidade", "Contabilidade de Custos",
      "Contabilidade Geral", "Contabilidade Pública", "Controle Externo", "Criminalística",
      "Direito Administrativo", "Direito Ambiental", "Direito Civil", "Direito Constitucional",
      "Direito do Consumidor", "Direito do Trabalho", "Direito Econômico", "Direito Eleitoral",
      "Direito Empresarial (Comercial)", "Direito Financeiro", "Direito Internacional", "Direito Penal",
      "Direito Penal Militar", "Direito Previdenciário", "Direito Processual Civil", "Direito Processual do Trabalho",
      "Direito Processual Penal", "Direito Processual Penal Militar", "Direito Sanitário", "Direito Tributário",
      "Direitos Humanos", "Economia", "Educação", "Educação Física", "Enfermagem", "Engenharia Civil",
      "Engenharia de Software", "Engenharia Elétrica", "Engenharia Mecânica", "Espanhol", "Estatística",
      "Ética no Serviço Público", "Filosofia", "Finanças", "Física", "Fisioterapia", "Geografia",
      "Gestão de Pessoas", "História", "Informática", "Inglês", "Legislação", "Legislação Aduaneira",
      "Legislação Específica", "Legislação de Trânsito", "Legislação Municipal", "Legislação Penal Especial",
      "Legislação Tributária", "Libras", "Matemática", "Matemática Financeira", "Medicina", "Medicina Legal",
      "Meio Ambiente", "Nutrição", "Odontologia", "Pedagogia", "Português", "Psicologia", "Química",
      "Raciocínio Lógico", "Redação", "Saúde Pública", "Segurança da Informação", "Segurança do Trabalho",
      "Serviço Social", "Sociologia", "Tecnologia da Informação (TI)"
    ];

    const TEMPLATES = {
      juridico: ['Direito Constitucional', 'Direito Administrativo', 'Direito Civil', 'Direito Penal', 'Português'],
      fiscal: ['Direito Tributário', 'Contabilidade', 'Legislação Tributária', 'Português', 'Matemática Financeira'],
      administrativo: ['Administração Geral', 'Administração Pública', 'Direito Administrativo', 'Português', 'Raciocínio Lógico']
    };

    const DB_NAME = 'planner-db-v2';
    let db = null;
    let executionsCache = null;
    let cacheTimestamp = 0;
    
    function openDB() {
      return new Promise((resolve, reject) => {
        if (db) return resolve(db);
        const request = indexedDB.open(DB_NAME, 1);
        request.onerror = () => reject(request.error);
        request.onsuccess = () => { db = request.result; resolve(db); };
        request.onupgradeneeded = (e) => {
          const db = e.target.result;
          if (!db.objectStoreNames.contains('plan')) db.createObjectStore('plan', { keyPath: 'id' });
          if (!db.objectStoreNames.contains('executions')) db.createObjectStore('executions', { keyPath: 'date' });
        };
      });
    }

    async function getPlan() {
      const db = await openDB();
      return new Promise((resolve) => {
        const tx = db.transaction('plan', 'readonly');
        const request = tx.objectStore('plan').get('current');
        request.onsuccess = () => resolve(request.result);
      });
    }

    async function savePlan(plan) {
      const db = await openDB();
      return new Promise((resolve) => {
        const tx = db.transaction('plan', 'readwrite');
        tx.objectStore('plan').put({ id: 'current', ...plan });
        tx.oncomplete = () => resolve();
      });
    }

    async function getTodayExecution() {
      const db = await openDB();
      const today = new Date().toISOString().split('T')[0];
      return new Promise((resolve) => {
        const tx = db.transaction('executions', 'readonly');
        const request = tx.objectStore('executions').get(today);
        request.onsuccess = () => resolve(request.result || { date: today, tasks: [] });
      });
    }

    async function saveTodayExecution(execution) {
      const db = await openDB();
      executionsCache = null;
      return new Promise((resolve) => {
        const tx = db.transaction('executions', 'readwrite');
        tx.objectStore('executions').put(execution);
        tx.oncomplete = () => resolve();
      });
    }

    async function getAllExecutions() {
      if (executionsCache && Date.now() - cacheTimestamp < 5000) return executionsCache;
      const db = await openDB();
      return new Promise((resolve) => {
        const tx = db.transaction('executions', 'readonly');
        const request = tx.objectStore('executions').getAll();
        request.onsuccess = () => {
          executionsCache = request.result || [];
          cacheTimestamp = Date.now();
          resolve(executionsCache);
        };
      });
    }

    function showToast(msg, type = 'info') {
      const toast = document.createElement('div'); 
      toast.className = 'toast'; 
      toast.textContent = msg;
      if (type === 'success') toast.style.borderLeftColor = '#22C55E';
      document.body.appendChild(toast); 
      setTimeout(() => toast.remove(), 3000);
    }

    let currentPlan = null;
    let todayExecution = null;
    let activeTask = null;
    let timerInterval = null;
    let timerSeconds = 0;
    let actualStudiedSeconds = 0;
    let animationFrame = null;

    const htmlEl = document.documentElement;
    const themeToggle = document.getElementById('theme-toggle');
    const themeIcon = document.getElementById('theme-icon');
    const themeText = themeToggle.querySelector('.theme-text');
    const savedTheme = localStorage.getItem('theme') || 'dark';
    function updateThemeUI(t) {
      htmlEl.setAttribute('data-theme', t);
      themeIcon.className = t === 'dark' ? 'fas fa-moon' : 'fas fa-sun';
      themeText.textContent = t === 'dark' ? 'Escuro' : 'Claro';
    }
    updateThemeUI(savedTheme);
    themeToggle.onclick = () => {
      const n = htmlEl.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
      updateThemeUI(n); localStorage.setItem('theme', n);
    };

    function daysSince(dateStr) {
      const diff = new Date() - new Date(dateStr);
      return Math.floor(diff / (1000 * 60 * 60 * 24));
    }

    function generateDailyTasks(plan, history) {
      if (!plan || !plan.subjects || plan.subjects.length === 0) return [];
      
      const lastStudied = {};
      history.forEach(exec => {
        exec.tasks.forEach(task => {
          if (task.completed) {
            if (!lastStudied[task.subject] || exec.date > lastStudied[task.subject]) {
              lastStudied[task.subject] = exec.date;
            }
          }
        });
      });
      
      const sortedSubjects = [...plan.subjects].sort((a, b) => {
        const daysA = lastStudied[a.name] ? daysSince(lastStudied[a.name]) : 999;
        const daysB = lastStudied[b.name] ? daysSince(lastStudied[b.name]) : 999;
        return daysB - daysA;
      });
      
      const totalWeight = sortedSubjects.reduce((sum, s) => sum + s.weight, 0);
      const tasks = [];
      const MAX_BLOCK = 90;
      
      sortedSubjects.forEach((subject, index) => {
        const proportion = subject.weight / totalWeight;
        let duration = Math.floor(plan.dailyTime * proportion);
        
        if (duration < 25) duration = 25;
        
        let remaining = duration;
        while (remaining > 0) {
          const block = Math.min(remaining, MAX_BLOCK);
          tasks.push({
            subject: subject.name,
            duration: block,
            completed: false
          });
          remaining -= block;
        }
      });
      
      return tasks.slice(0, 10);
    }

    async function generateTodayPlan() {
      const plan = await getPlan();
      if (!plan || !plan.subjects || plan.subjects.length === 0) {
        showToast('Configure seu plano de estudos primeiro');
        return;
      }
      
      let execution = await getTodayExecution();
      
      if (execution.tasks.length === 0) {
        const history = await getAllExecutions();
        execution.tasks = generateDailyTasks(plan, history);
        await saveTodayExecution(execution);
      }
      
      todayExecution = execution;
      currentPlan = plan;
      renderPlan();
      updateDashboard();
    }

    function renderPlan() {
      const container = document.getElementById('planContainer');
      
      if (!todayExecution || todayExecution.tasks.length === 0) {
        container.innerHTML = `
          <div class="empty-state">
            <i class="fas fa-clipboard-list"></i>
            <p>Nenhuma tarefa para hoje</p>
            <button class="btn btn-primary" onclick="window.generateTodayPlan()" style="margin-top: 16px;">
              <i class="fas fa-magic"></i> Gerar Plano
            </button>
          </div>
        `;
        document.getElementById('remainingTimeDisplay').textContent = '';
        return;
      }
      
      const completed = todayExecution.tasks.filter(t => t.completed).length;
      const total = todayExecution.tasks.length;
      const progress = (completed / total) * 100;
      const remaining = todayExecution.tasks.filter(t => !t.completed).reduce((sum, t) => sum + t.duration, 0);
      
      document.getElementById('dailyProgress').style.width = `${progress}%`;
      document.getElementById('remainingTimeDisplay').textContent = `⏳ ${remaining} minutos restantes para concluir o plano de hoje`;
      
      container.innerHTML = todayExecution.tasks.map((task, index) => `
        <div class="task-item ${task.completed ? 'completed' : ''}">
          <div class="task-info">
            <span class="task-subject">${task.subject}</span>
            <span class="task-duration">⏱️ ${task.duration} minutos ${task.actualDuration ? `(estudado: ${task.actualDuration}min)` : ''}</span>
          </div>
          <div class="task-actions">
            ${!task.completed ? `
              <button class="btn btn-outline start-task-btn" data-index="${index}">
                <i class="fas fa-play"></i> Iniciar
              </button>
            ` : `
              <span class="badge" style="background: var(--success); color: white;">✓ Concluído</span>
            `}
          </div>
        </div>
      `).join('');
      
      document.querySelectorAll('.start-task-btn').forEach(btn => {
        btn.addEventListener('click', (e) => {
          const index = parseInt(e.target.closest('button').dataset.index);
          startTask(index);
        });
      });
    }

    function startTask(index) {
      const task = todayExecution.tasks[index];
      activeTask = { ...task, index };
      actualStudiedSeconds = 0;
      
      document.getElementById('activeSubject').textContent = task.subject;
      document.getElementById('plannedTime').textContent = task.duration;
      document.getElementById('actualTime').textContent = '0';
      timerSeconds = task.duration * 60;
      updateTimerDisplay();
      
      document.getElementById('activeTaskCard').style.display = 'block';
      
      if (timerInterval) clearInterval(timerInterval);
      if (animationFrame) cancelAnimationFrame(animationFrame);
      
      let lastTick = Date.now();
      const updateTimer = () => {
        const now = Date.now();
        if (!document.hidden) {
          const delta = Math.floor((now - lastTick) / 1000);
          timerSeconds -= delta;
          actualStudiedSeconds += delta;
          
          if (timerSeconds <= 0) {
            timerSeconds = 0;
            updateTimerDisplay();
            completeTask(true);
            return;
          }
          
          updateTimerDisplay();
          document.getElementById('actualTime').textContent = Math.floor(actualStudiedSeconds / 60);
          
          if (actualStudiedSeconds % 60 === 0 && actualStudiedSeconds > 0) {
            todayExecution.tasks[activeTask.index].actualDuration = Math.floor(actualStudiedSeconds / 60);
            saveTodayExecution(todayExecution);
          }
        }
        lastTick = now;
        animationFrame = requestAnimationFrame(updateTimer);
      };
      
      animationFrame = requestAnimationFrame(updateTimer);
    }

    function updateTimerDisplay() {
      const mins = Math.floor(Math.abs(timerSeconds) / 60);
      const secs = Math.abs(timerSeconds) % 60;
      document.getElementById('taskTimer').textContent = 
        `${timerSeconds < 0 ? '-' : ''}${mins.toString().padStart(2,'0')}:${secs.toString().padStart(2,'0')}`;
    }

    async function completeTask(auto = false) {
      if (!activeTask) return;
      
      if (animationFrame) cancelAnimationFrame(animationFrame);
      if (timerInterval) clearInterval(timerInterval);
      
      const actualDuration = Math.max(1, Math.floor(actualStudiedSeconds / 60));
      todayExecution.tasks[activeTask.index].completed = true;
      todayExecution.tasks[activeTask.index].actualDuration = actualDuration;
      await saveTodayExecution(todayExecution);
      
      document.getElementById('activeTaskCard').style.display = 'none';
      
      const allCompleted = todayExecution.tasks.every(t => t.completed);
      if (allCompleted) {
        confetti({ particleCount: 100, spread: 70, origin: { y: 0.6 } });
        showToast('🎉 Parabéns! Você concluiu todas as tarefas de hoje!', 'success');
      }
      
      activeTask = null;
      renderPlan();
      updateDashboard();
      showToast(`✅ Tarefa concluída! ${actualDuration} minutos estudados.`);
    }

    async function skipTask() {
      if (!activeTask) return;
      
      if (animationFrame) cancelAnimationFrame(animationFrame);
      if (timerInterval) clearInterval(timerInterval);
      
      document.getElementById('activeTaskCard').style.display = 'none';
      activeTask = null;
      showToast('Tarefa pulada. Ela continua pendente para hoje.');
    }

    async function updateDashboard() {
      const execution = await getTodayExecution();
      const allExecutions = await getAllExecutions();
      
      const todayTime = execution.tasks.reduce((sum, t) => sum + (t.completed ? (t.actualDuration || t.duration) : 0), 0);
      const completed = execution.tasks.filter(t => t.completed).length;
      const total = execution.tasks.length;
      
      const completionRate = allExecutions.length > 0 
        ? Math.round((allExecutions.reduce((sum, e) => 
            sum + (e.tasks.filter(t => t.completed).length / Math.max(e.tasks.length, 1)), 0) / allExecutions.length) * 100)
        : 0;
      
      let streak = 0;
      const dates = allExecutions.map(e => e.date).sort().reverse();
      if (dates.length) {
        let check = new Date();
        for (let d of dates) {
          if (d === check.toISOString().split('T')[0]) { 
            const exec = allExecutions.find(e => e.date === d);
            if (exec && exec.tasks.length > 0 && exec.tasks.every(t => t.completed)) streak++;
            else break;
            check.setDate(check.getDate() - 1);
          } else break;
        }
      }
      
      document.getElementById('todayTime').textContent = `${todayTime}min`;
      document.getElementById('todayTasks').textContent = `${completed}/${total}`;
      document.getElementById('completionRate').textContent = `${completionRate}%`;
      document.getElementById('currentStreak').textContent = `${streak}🔥`;
      
      const subjectStats = {};
      allExecutions.forEach(e => {
        e.tasks.forEach(t => {
          if (t.completed) {
            subjectStats[t.subject] = (subjectStats[t.subject] || 0) + (t.actualDuration || t.duration);
          }
        });
      });
      
      const topSubjects = Object.entries(subjectStats).sort((a, b) => b[1] - a[1]).slice(0, 5);
      const container = document.getElementById('topSubjectsContainer');
      if (topSubjects.length === 0) {
        container.innerHTML = '<div class="empty-state">Complete tarefas para ver estatísticas</div>';
      } else {
        container.innerHTML = topSubjects.map(([subject, minutes]) => `
          <div class="task-item">
            <div class="task-info">
              <span class="task-subject">${subject}</span>
              <span class="task-duration">${Math.floor(minutes / 60)}h ${minutes % 60}min total</span>
            </div>
          </div>
        `).join('');
      }
      
      renderWeeklyChart(allExecutions);
    }

    function renderWeeklyChart(executions) {
      const chart = document.getElementById('weeklyChart');
      const last7Days = [];
      for (let i = 6; i >= 0; i--) {
        const d = new Date(); d.setDate(d.getDate() - i);
        last7Days.push(d.toISOString().split('T')[0]);
      }
      
      const maxMinutes = Math.max(30, ...last7Days.map(date => {
        const exec = executions.find(e => e.date === date);
        return exec ? exec.tasks.reduce((s, t) => s + (t.completed ? (t.actualDuration || t.duration) : 0), 0) : 0;
      }));
      
      chart.innerHTML = last7Days.map(date => {
        const exec = executions.find(e => e.date === date);
        const minutes = exec ? exec.tasks.reduce((s, t) => s + (t.completed ? (t.actualDuration || t.duration) : 0), 0) : 0;
        const height = maxMinutes > 0 ? (minutes / maxMinutes) * 100 : 0;
        const dayName = new Date(date).toLocaleDateString('pt-BR', { weekday: 'short' }).slice(0, 3);
        return `
          <div class="chart-bar">
            <div class="bar"><div class="bar-fill" style="height: ${height}%;"></div></div>
            <div class="bar-label">${dayName}</div>
            <div class="bar-label">${minutes}m</div>
          </div>
        `;
      }).join('');
    }

    let allSubjects = DISCIPLINAS;
    
    function renderSubjectsGrid(filter = '') {
      const grid = document.getElementById('subjectsGrid');
      getPlan().then(plan => {
        const selectedSubjects = plan?.subjects || [];
        const filtered = filter ? allSubjects.filter(s => s.toLowerCase().includes(filter.toLowerCase())) : allSubjects;
        
        const categorized = {};
        filtered.forEach(s => {
          let cat = 'Outros';
          if (s.includes('Direito')) cat = 'Direito';
          else if (s.includes('Administração') || s.includes('Gestão')) cat = 'Administração';
          else if (s.includes('Contabilidade') || s.includes('Finan')) cat = 'Contabilidade/Finanças';
          else if (s.includes('Português') || s.includes('Inglês') || s.includes('Redação')) cat = 'Linguagens';
          else if (s.includes('Matemática') || s.includes('Raciocínio') || s.includes('Estatística')) cat = 'Exatas';
          else if (s.includes('Informática') || s.includes('TI')) cat = 'Tecnologia';
          if (!categorized[cat]) categorized[cat] = [];
          categorized[cat].push(s);
        });
        
        grid.innerHTML = Object.entries(categorized).map(([cat, subjects]) => `
          <div class="subject-category">
            <h4>${cat}</h4>
            ${subjects.map(subject => {
              const selected = selectedSubjects.find(s => s.name === subject);
              return `
                <div class="subject-item">
                  <input type="checkbox" value="${subject}" ${selected ? 'checked' : ''}>
                  <span style="flex:1;">${subject}</span>
                  <input type="number" class="subject-weight" value="${selected?.weight || 1}" min="1" max="5" ${!selected ? 'disabled' : ''}>
                </div>
              `;
            }).join('')}
          </div>
        `).join('');
        
        grid.querySelectorAll('input[type="checkbox"]').forEach(cb => {
          cb.addEventListener('change', (e) => {
            const weightInput = e.target.closest('.subject-item').querySelector('.subject-weight');
            weightInput.disabled = !e.target.checked;
          });
        });
      });
    }

    async function saveConfiguration() {
      const dailyTime = parseInt(document.getElementById('dailyTimeInput').value);
      const subjects = [];
      
      document.querySelectorAll('.subject-item').forEach(item => {
        const cb = item.querySelector('input[type="checkbox"]');
        if (cb.checked) {
          subjects.push({
            name: cb.value,
            weight: parseInt(item.querySelector('.subject-weight').value)
          });
        }
      });
      
      if (subjects.length === 0) { showToast('Selecione pelo menos uma matéria'); return; }
      
      await savePlan({ dailyTime, subjects });
      window.closeConfigModal();
      showToast('Configuração salva!', 'success');
      generateTodayPlan();
    }

    window.closeConfigModal = () => document.getElementById('configModal').style.display = 'none';
    window.generateTodayPlan = generateTodayPlan;

    document.getElementById('configBtn').addEventListener('click', () => {
      renderSubjectsGrid();
      getPlan().then(plan => {
        if (plan) document.getElementById('dailyTimeInput').value = plan.dailyTime;
      });
      document.getElementById('configModal').style.display = 'flex';
      document.getElementById('subjectSearch').value = '';
    });

    document.getElementById('subjectSearch').addEventListener('input', (e) => {
      renderSubjectsGrid(e.target.value);
    });

    document.querySelectorAll('[data-template]').forEach(btn => {
      btn.addEventListener('click', () => {
        const template = TEMPLATES[btn.dataset.template];
        document.querySelectorAll('.subject-item input[type="checkbox"]').forEach(cb => {
          cb.checked = template.includes(cb.value);
          const weightInput = cb.closest('.subject-item').querySelector('.subject-weight');
          weightInput.disabled = !cb.checked;
          if (cb.checked) weightInput.value = 2;
        });
        showToast(`Template "${btn.textContent}" aplicado!`, 'success');
      });
    });

    document.getElementById('setupPlanBtn').addEventListener('click', () => document.getElementById('configBtn').click());
    document.getElementById('generatePlanBtn').addEventListener('click', generateTodayPlan);
    document.getElementById('saveConfigBtn').addEventListener('click', saveConfiguration);
    document.getElementById('completeTaskBtn').addEventListener('click', () => completeTask(false));
    document.getElementById('skipTaskBtn').addEventListener('click', skipTask);
    
    document.getElementById('closeTaskBtn').addEventListener('click', () => {
      if (animationFrame) cancelAnimationFrame(animationFrame);
      if (timerInterval) clearInterval(timerInterval);
      document.getElementById('activeTaskCard').style.display = 'none';
      activeTask = null;
    });

    openDB().then(async () => {
      const plan = await getPlan();
      if (plan) {
        currentPlan = plan;
        await generateTodayPlan();
      } else {
        document.getElementById('planContainer').innerHTML = `
          <div class="empty-state">
            <i class="fas fa-clipboard-list"></i>
            <p>Configure seu plano de estudos</p>
            <button class="btn btn-primary" id="setupPlanBtn2" style="margin-top: 16px;">
              <i class="fas fa-plus"></i> Configurar Agora
            </button>
          </div>
        `;
        document.getElementById('setupPlanBtn2').addEventListener('click', () => document.getElementById('configBtn').click());
      }
      updateDashboard();
    });
  })();
</script>
</body>
</html>
