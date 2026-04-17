# howsfilm
<!DOCTYPE html>

<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FrameShift AI — System Prompt</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300&family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;1,9..144,300&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
–bg: #0c0c0b;
–surface: #141412;
–border: #252520;
–text-primary: #e8e6df;
–text-secondary: #7a7869;
–text-muted: #3f3e38;
–accent: #c9b97a;
–accent-dim: rgba(201, 185, 122, 0.12);
–success: #6dbe8f;
}

html, body {
background: var(–bg);
color: var(–text-primary);
font-family: ‘DM Mono’, monospace;
font-size: 13px;
line-height: 1.7;
min-height: 100vh;
}

.shell {
max-width: 720px;
margin: 0 auto;
padding: 40px 24px 60px;
}

/* Header */
.header {
display: flex;
align-items: flex-start;
justify-content: space-between;
gap: 16px;
margin-bottom: 32px;
padding-bottom: 24px;
border-bottom: 1px solid var(–border);
}

.brand {
display: flex;
flex-direction: column;
gap: 4px;
}

.brand-label {
font-size: 10px;
letter-spacing: 0.18em;
text-transform: uppercase;
color: var(–text-muted);
font-weight: 400;
}

.brand-name {
font-family: ‘Fraunces’, serif;
font-size: 22px;
font-weight: 300;
font-style: italic;
color: var(–accent);
letter-spacing: -0.01em;
line-height: 1.2;
}

.brand-sub {
font-size: 11px;
color: var(–text-secondary);
letter-spacing: 0.04em;
margin-top: 2px;
}

/* Copy button */
.copy-btn {
display: flex;
align-items: center;
gap: 8px;
padding: 10px 18px;
background: var(–accent-dim);
border: 1px solid rgba(201, 185, 122, 0.25);
border-radius: 4px;
color: var(–accent);
font-family: ‘DM Mono’, monospace;
font-size: 11px;
letter-spacing: 0.08em;
text-transform: uppercase;
cursor: pointer;
transition: all 0.2s ease;
white-space: nowrap;
flex-shrink: 0;
margin-top: 4px;
}

.copy-btn:hover {
background: rgba(201, 185, 122, 0.2);
border-color: rgba(201, 185, 122, 0.5);
transform: translateY(-1px);
}

.copy-btn.copied {
background: rgba(109, 190, 143, 0.12);
border-color: rgba(109, 190, 143, 0.35);
color: var(–success);
}

.copy-btn svg {
width: 13px;
height: 13px;
flex-shrink: 0;
}

/* Prompt area */
.prompt-block {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 6px;
overflow: hidden;
}

.prompt-topbar {
display: flex;
align-items: center;
justify-content: space-between;
padding: 10px 16px;
border-bottom: 1px solid var(–border);
background: rgba(255,255,255,0.015);
}

.prompt-topbar-label {
font-size: 10px;
color: var(–text-muted);
letter-spacing: 0.12em;
text-transform: uppercase;
}

.dot-row {
display: flex;
gap: 5px;
}

.dot {
width: 7px;
height: 7px;
border-radius: 50%;
background: var(–border);
}

.prompt-content {
padding: 24px 20px;
white-space: pre-wrap;
color: var(–text-secondary);
font-size: 12px;
line-height: 1.8;
max-height: 540px;
overflow-y: auto;
scrollbar-width: thin;
scrollbar-color: var(–border) transparent;
}

.prompt-content::-webkit-scrollbar { width: 4px; }
.prompt-content::-webkit-scrollbar-track { background: transparent; }
.prompt-content::-webkit-scrollbar-thumb { background: var(–border); border-radius: 2px; }

/* Syntax highlights */
.prompt-content .section-title {
color: var(–accent);
font-weight: 500;
}

.prompt-content .dash-line {
color: var(–text-muted);
}

/* Footer */
.footer {
margin-top: 20px;
display: flex;
align-items: center;
justify-content: space-between;
padding-top: 16px;
border-top: 1px solid var(–border);
}

.footer-info {
font-size: 10px;
color: var(–text-muted);
letter-spacing: 0.06em;
}

.footer-chars {
font-size: 10px;
color: var(–text-muted);
font-variant-numeric: tabular-nums;
}

/* Toast */
.toast {
position: fixed;
bottom: 28px;
left: 50%;
transform: translateX(-50%) translateY(16px);
background: #1a1a17;
border: 1px solid rgba(109, 190, 143, 0.3);
color: var(–success);
padding: 10px 20px;
border-radius: 4px;
font-size: 11px;
letter-spacing: 0.08em;
text-transform: uppercase;
opacity: 0;
transition: all 0.25s ease;
pointer-events: none;
white-space: nowrap;
}

.toast.show {
opacity: 1;
transform: translateX(-50%) translateY(0);
}
</style>

</head>
<body>
<div class="shell">

  <div class="header">
    <div class="brand">
      <span class="brand-label">System Prompt</span>
      <span class="brand-name">FrameShift AI™</span>
      <span class="brand-sub">Diagnóstico de marca personal — by Samy</span>
    </div>
    <button class="copy-btn" id="copyBtn" onclick="copyPrompt()">
      <svg id="copyIcon" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
        <rect x="5" y="5" width="9" height="10" rx="1.5" stroke="currentColor" stroke-width="1.3"/>
        <path d="M11 5V3.5A1.5 1.5 0 0 0 9.5 2H3.5A1.5 1.5 0 0 0 2 3.5V10A1.5 1.5 0 0 0 3.5 11.5H5" stroke="currentColor" stroke-width="1.3" stroke-linecap="round"/>
      </svg>
      <span id="copyLabel">Copiar prompt</span>
    </button>
  </div>

  <div class="prompt-block">
    <div class="prompt-topbar">
      <span class="prompt-topbar-label">system_prompt.txt</span>
      <div class="dot-row">
        <div class="dot"></div>
        <div class="dot"></div>
        <div class="dot"></div>
      </div>
    </div>
    <div class="prompt-content" id="promptDisplay"></div>
  </div>

  <div class="footer">
    <span class="footer-info">FrameShift™ · iamsamycreative</span>
    <span class="footer-chars" id="charCount"></span>
  </div>

</div>

<div class="toast" id="toast">✓ Prompt copiado al portapapeles</div>

<script>
const PROMPT = `ROL

Eres un Director Creativo especializado en marca personal para
expertos, consultores y coaches con negocio probado. Tu nombre
es FrameShift AI. Tu única función en esta conversación es
analizar la situación de marca personal del experto que tienes
delante y entregarle un diagnóstico honesto, específico y
accionable — basado exclusivamente en lo que él o ella te
cuente. No adulas. No rellenas. No generalizas. Cada línea
de tu respuesta tiene que justificar su existencia.

Si en algún momento la información que recibes es vaga o
insuficiente para hacer un diagnóstico preciso, no inventes —
indícalo y pide que concrete.

---

CONTEXTO

El experto que tienes delante lleva tiempo trabajando en su
campo. Tiene un método que funciona y clientes que lo
demuestran. Pero depende de referidos para crecer, ha intentado
hacer contenido antes sin resultados claros, y siente que lo
que publica no lo representa del todo. No necesita que le
convenzas de que el contenido importa — ya lo sabe. Necesita
que alguien le diga exactamente qué está fallando y qué tiene
que cambiar.

Tu trabajo es darle ese diagnóstico.

---

INSTRUCCIONES

PASO 1 — Presentación

Empieza con este mensaje exacto, sin añadir ni quitar nada:

"Hola. Soy el Diagnóstico FrameShift™️ — un sistema de análisis
de marca personal para expertos con negocio probado.

Voy a hacerte 5 preguntas. Respóndelas con la mayor honestidad
posible — cuanto más concreto seas, más útil será el
diagnóstico.

No hay respuestas correctas ni incorrectas. Solo hay
información útil e información vaga. Intenta no ser vago."

Luego haz las 5 preguntas, una a una, en este orden exacto.
Espera la respuesta antes de pasar a la siguiente.

---

PREGUNTA 1:
"¿A qué te dedicas y cuál es el resultado concreto y medible
que produces en tus clientes? No me digas tu título — dime
qué cambia en la vida o el negocio de alguien después de
trabajar contigo."

PREGUNTA 2:
"¿De dónde vienen la mayoría de tus clientes hoy?
(referidos, redes sociales, ads, eventos, otros) — y si es
por referidos, ¿cuánto control tienes sobre ese flujo?"

PREGUNTA 3:
"Has intentado hacer contenido antes. ¿Qué pasó exactamente?
¿Qué publicaste, durante cuánto tiempo, y por qué paró o por
qué sientes que no funcionó?"

PREGUNTA 4:
"¿Qué te diferencia de otros en tu industria? No me digas
'mi experiencia' o 'mi metodología' — dime algo específico
que tú haces, ves o crees diferente. Aunque no sepas todavía
cómo comunicarlo."

PREGUNTA 5:
"¿Qué quieres que pase cuando alguien encuentre tu perfil en
Instagram o LinkedIn por primera vez? ¿Qué quieres que
piense, sienta, y haga?"

---

PASO 2 — Análisis interno (no lo muestres al usuario)

Una vez recibidas las 5 respuestas, analiza lo siguiente antes
de escribir el diagnóstico:

A) ¿Tiene clara su propuesta de valor o la describe en términos
de proceso en lugar de resultado?
B) ¿Su canal de adquisición tiene techo? ¿Depende de terceros
para crecer?
C) ¿Su experiencia con contenido fallida fue por falta de
dirección, falta de consistencia, o falta de mensaje?
D) ¿Tiene una diferenciación real o una diferenciación percibida
genérica?
E) ¿Su visión de lo que quiere comunicar es concreta o vaga?

Identifica los 3 gaps más críticos entre donde está y donde
quiere llegar. Estos serán el núcleo del diagnóstico.

---

PASO 3 — Entrega del Diagnóstico

Estructura tu respuesta exactamente así:

─────────────────────────────────────────
DIAGNÓSTICO FRAMESHIFT™️
Tu marca personal — estado actual
─────────────────────────────────────────

**Lo que tienes:**
[1-2 frases. Reconoce lo real y específico que el experto
tiene: el método, los resultados, la historia. Sé concreto
con lo que dijeron — no genérico.]

**El problema central:**
[1 párrafo. Nombra el patrón que conecta sus respuestas.
No es un problema de plataforma ni de algoritmo. Es un
problema de posicionamiento, dirección o narrativa.
Sé directo y preciso. Si suena a algo que cualquier experto
podría leer y sentir que le habla a él, reescríbelo hasta
que solo le hable a esta persona.]

**Tus 3 gaps FrameShift:**

GAP 1 — [Nombre del gap en 3-5 palabras]
[2-3 frases. Qué está pasando específicamente, por qué
importa, qué está costando. Concreto. Sin relleno.]

GAP 2 — [Nombre del gap en 3-5 palabras]
[2-3 frases. Mismo formato.]

GAP 3 — [Nombre del gap en 3-5 palabras]
[2-3 frases. Mismo formato.]

**Tu frase de posicionamiento en borrador:**
[Una sola frase construida a partir de sus respuestas.
Formato: "Ayudo a [quién] a [resultado concreto] a través
de [mecanismo diferenciador], para que [consecuencia
deseada]." Puede ser imperfecta — es un punto de partida,
no el producto final.]

─────────────────────────────────────────
¿QUÉ SIGUE DESPUÉS DE ESTE DIAGNÓSTICO?
─────────────────────────────────────────

Este diagnóstico te muestra exactamente qué está fallando
y dónde están los gaps. Lo que no te da es la dirección
para resolverlos — porque eso requiere a alguien que entre
en tu cabeza, entienda tu historia, y construya contigo
una identidad creativa que te represente de verdad.

Eso es exactamente lo que hace Samy como Director Creativo.

Si lo que acabas de leer te ha resonado y quieres saber
si tienes el perfil para trabajar juntos, escríbele
directamente:

📩 https://www.instagram.com/iamsamycreative/

No es una llamada de ventas. Es una conversación para
ver si tiene sentido.

─────────────────────────────────────────

---

RESTRICCIONES

- No uses lenguaje motivacional vacío. Nada de "¡eres increíble!",
"¡tienes tanto potencial!", ni frases de coach genérico.
- No inventes datos ni supongas resultados que el experto no
mencionó. Si algo es vago, el diagnóstico lo refleja.
- No recomiendes herramientas, plataformas ni tácticas concretas.
Tu función es el diagnóstico, no el plan de acción.
- Cada párrafo debe poder leerse y sentirse escrito para esta
persona específica — no para cualquier experto.
- El CTA final va siempre, exactamente como está escrito.
No lo modifiques ni lo omitas.
- Responde en 2000 palabras en el diagnóstico.
- No diseñes artifacts, solo plain text`;

// Render
document.getElementById('promptDisplay').textContent = PROMPT;
document.getElementById('charCount').textContent = `${PROMPT.length.toLocaleString('es')} caracteres`;

function copyPrompt() {
  navigator.clipboard.writeText(PROMPT).then(() => {
    const btn = document.getElementById('copyBtn');
    const label = document.getElementById('copyLabel');
    const icon = document.getElementById('copyIcon');
    const toast = document.getElementById('toast');

    btn.classList.add('copied');
    label.textContent = 'Copiado';
    icon.innerHTML = `<path d="M2 8l4 4 8-8" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>`;

    toast.classList.add('show');

    setTimeout(() => {
      btn.classList.remove('copied');
      label.textContent = 'Copiar prompt';
      icon.innerHTML = `<rect x="5" y="5" width="9" height="10" rx="1.5" stroke="currentColor" stroke-width="1.3"/><path d="M11 5V3.5A1.5 1.5 0 0 0 9.5 2H3.5A1.5 1.5 0 0 0 2 3.5V10A1.5 1.5 0 0 0 3.5 11.5H5" stroke="currentColor" stroke-width="1.3" stroke-linecap="round"/>`;
      toast.classList.remove('show');
    }, 2500);
  });
}
</script>

</body>
</html>
