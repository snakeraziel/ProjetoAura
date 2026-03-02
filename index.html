<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>PROJETO AURA - Código Zero</title>
<style>
:root {
  --bg:#0f172a; --card:#1e293b; --accent:#3b82f6; --success:#22c55e; --text:#f1f5f9;
}
body{margin:0;padding:15px;font-family:system-ui;background:var(--bg);color:var(--text)}
.container{max-width:520px;margin:auto}
h2{text-align:center;color:var(--accent);font-size:1.2rem}
.upload-area{border:2px dashed var(--accent);padding:20px;text-align:center;border-radius:12px;background:var(--card);margin-bottom:15px}
.btn{width:100%;padding:14px;border-radius:10px;border:none;font-weight:700;font-size:1rem;margin-top:10px}
.btn-upload{background:var(--accent);color:#fff}
.btn-search{background:#334155;color:#fff}
.btn-apply{background:var(--success);color:#fff}
.search-box{display:flex;gap:10px;margin-bottom:15px}
input{flex:1;padding:12px;border-radius:10px;border:1px solid #334155;background:#020617;color:#fff}
#painelCliente{display:none;background:var(--card);padding:15px;border-radius:12px;border:1px solid #334155}
.info-row{display:flex;justify-content:space-between;margin-bottom:6px;font-size:.9rem}
.label{color:#94a3b8}.val{font-weight:700;color:#fde047}
.history-item{background:#334155;padding:10px;border-radius:8px;margin-bottom:6px;font-size:.8rem;display:flex;justify-content:space-between}
small{color:#94a3b8}
</style>
</head>
<body>

<div class="container">
<h2>PROJETO AURA – CÓDIGO ZERO</h2>

<div class="upload-area">
  <small id="nomeArquivo">Nenhum arquivo carregado</small>
  <label class="btn btn-upload">
    📂 CARREGAR TXT
    <input type="file" id="inputTxt" accept=".txt" hidden>
  </label>
</div>

<div class="search-box">
  <input id="idBusca" placeholder="Nº Cliente ou Medidor" inputmode="numeric">
  <button class="btn btn-search" onclick="buscar()">🔍</button>
</div>

<div id="painelCliente">
  <div id="nomeCliente" style="color:var(--accent);font-weight:800;margin-bottom:10px"></div>
  <div class="info-row"><span class="label">Medidor:</span><span class="val" id="valMedidor"></span></div>
  <div class="info-row"><span class="label">Última leitura:</span><span class="val" id="valULeitura"></span></div>
  <div class="info-row"><span class="label">Média anterior:</span><span class="val" id="valMediaAnt"></span></div>
  <div class="info-row"><span class="label">Nova leitura (simulação):</span><span class="val" id="valNova"></span></div>
  <button class="btn btn-apply" onclick="aplicarMedia()">✅ APLICAR MÉDIA</button>
</div>

<div style="margin-top:15px">
  <small>ÚLTIMAS 3 MÉDIAS APLICADAS (DESTE CLIENTE)</small>
  <div id="listaHistorico"></div>
</div>

</div>

<script>
let base = [];

document.getElementById('inputTxt').addEventListener('change', e => {
  const file = e.target.files[0];
  const reader = new FileReader();

  reader.onload = ev => {
    const linhas = ev.target.result.split(/\r?\n/);

    base = linhas.map(linha => {
      if (!linha || !linha.includes(';')) return null;

      const limpa = linha.replace(/\r/g, '');
      const p = limpa.split(';');

      const nc = p[0]?.trim();
      const nome = p[15]?.trim();

      // Medidor = campo que contém hífen (ex: 9085188-FAE-004)
      const medidor = p.find(x => x && x.includes('-')) || '';

      // Encontrar "Sim" e pegar os dois próximos números
      const idxSim = p.findIndex(x => x === 'Sim');
      let uLeitura = '';
      let mediaAnt = '';

      if (idxSim !== -1) {
        uLeitura = p[idxSim + 1] || '';
        mediaAnt = p[idxSim + 2] || '';
      }

      return {
        linha: limpa.toUpperCase(),
        nc,
        nome,
        medidor,
        uLeitura: uLeitura.trim(),
        mediaAnt: mediaAnt.trim()
      };
    }).filter(Boolean);

    document.getElementById('nomeArquivo').innerText =
      `Base carregada: ${file.name} (${base.length} registros)`;

    alert("TXT carregado com sucesso!");
  };

  reader.readAsText(file, "UTF-8");
});

function buscar() {
  const termo = document.getElementById('idBusca').value.trim().toUpperCase();
  if (!termo) return alert("Digite algo.");

  const c = base.find(item => item.linha.includes(termo));
  if (!c) return alert("Nada encontrado.");

  const u = parseInt((c.uLeitura || '').replace(/\D/g, '')) || 0;
  const m = parseInt((c.mediaAnt || '').replace(/\D/g, '')) || 0;
  const nova = u + m;

  const painel = document.getElementById('painelCliente');
  painel.style.display = 'block';

  document.getElementById('nomeCliente').innerText = c.nome || '(sem nome)';
  document.getElementById('valMedidor').innerText = c.medidor || '-';
  document.getElementById('valULeitura').innerText = u || '(vazio no TXT)';
  document.getElementById('valMediaAnt').innerText = m || '(vazio no TXT)';
  document.getElementById('valNova').innerText = nova || '-';

renderHistoricoCliente(c.nc);
document.getElementById('painelCliente').dataset.nc = c.nc;
}

function aplicarMedia() {
  const painel = document.getElementById('painelCliente');
  const nc = painel.dataset.nc;

  if (!nc) return alert("Cliente não encontrado.");

  const ultima = parseInt(document.getElementById('valULeitura').innerText) || 0;
  const media = parseInt(document.getElementById('valMediaAnt').innerText) || 0;
  const nova = ultima + media;

  salvarHistorico(nc, ultima, media, nova);
  renderHistoricoCliente(nc);

  alert("Média aplicada! Nova leitura: " + nova);
}

function salvarHistorico(nc, ultima, media, nova) {
  let historico = JSON.parse(localStorage.getItem('historicoClientes')) || {};

  if (!historico[nc]) historico[nc] = [];

  historico[nc].unshift({
    data: new Date().toLocaleString("pt-BR"),
    mediaAplicada: media,
    ultima,
    nova
  });

  if (historico[nc].length > 3) historico[nc].pop();

  localStorage.setItem('historicoClientes', JSON.stringify(historico));
}

function renderHistoricoCliente(nc) {
  const box = document.getElementById('listaHistorico');
  box.innerHTML = "";

  const historico = JSON.parse(localStorage.getItem('historicoClientes')) || {};
  const lista = historico[nc] || [];

  if (!lista.length) {
    box.innerHTML = "<small style='color:#94a3b8'>Nenhuma média aplicada ainda.</small>";
    return;
  }

  lista.forEach(h => {
    const d = document.createElement('div');
    d.className = 'history-item';
    d.innerHTML = `
      <span>${h.data}</span>
      <span>Média: <strong>${h.mediaAplicada}</strong> | ${h.ultima} + ${h.mediaAplicada} = <strong>${h.nova}</strong></span>
    `;
    box.appendChild(d);
  });
}

</script>


</body>
</html>
