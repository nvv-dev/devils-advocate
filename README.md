# devils-advocate

> Asume que la idea va a fracasar e intenta demostrarlo.

**Abogado del diablo** · Skill para agentes de código de la comunidad [nvvdev](https://github.com/nvv-dev). Funciona en Claude Code como plugin o como skill suelta, y en cualquier agente compatible con el formato abierto [`SKILL.md`](https://agentskills.io).

*English summary at the end.*

## Qué hace

Critica una idea, un MVP o una decisión costosa desde ocho ángulos (premisas, mercado, competencia, viabilidad, números, ejecución, pre-mortem y punto ciego), después de seis preguntas que obligan a replantearla. Distingue evidencia de inferencia, recomienda expandir, mantener o reducir el alcance, y cierra con un veredicto y una lista priorizada de arreglos. No adula, pero tampoco inventa defectos.

## Objetivo

Descartar o fortalecer ideas antes de invertirles semanas o dinero.

## Cuándo usarla

- Antes de construir un producto o funcionalidad grande
- Antes de una decisión de arquitectura cara

## Cuándo no

- Tareas ya decididas y de bajo costo

## Ejemplo

```text
/devils-advocate Quiero hacer un SaaS de inventario para tiendas de barrio en Colombia.
```

## Cómo se activa

Esta skill **solo se activa a mano** (`disable-model-invocation: true`): no ocupa contexto en cada sesión y la invocas cuando la necesitas:

- Instalada como plugin: `/devils-advocate:devils-advocate`
- Copiada a `.claude/skills/`: `/devils-advocate`

## Instalación

### Opción 1: Claude Code, como plugin (recomendada)

Dentro de Claude Code:

```text
/plugin marketplace add nvv-dev/claude-plugins
/plugin install devils-advocate@nvvdev
```

La primera línea agrega el catálogo de nvvdev una sola vez; la segunda instala esta skill. Si prefieres el paquete completo, instala `dev-workflow@nvvdev` en su lugar (incluye esta skill y las demás de [dev-workflow](https://github.com/nvv-dev/dev-workflow)); no instales los dos a la vez.

### Opción 2: Claude Code, copiando la skill

Para un solo proyecto (se comparte con tu equipo por git):

```bash
git clone --depth 1 https://github.com/nvv-dev/devils-advocate.git /tmp/devils-advocate
mkdir -p .claude/skills
cp -R /tmp/devils-advocate/skills/devils-advocate .claude/skills/
```

Para todos tus proyectos, cópiala en `~/.claude/skills/` en lugar de `.claude/skills/`.

### Opción 3: otros agentes

Copia la carpeta `skills/devils-advocate/` en la carpeta de skills de tu agente (cada agente documenta la suya). Con la CLI [skills](https://github.com/vercel-labs/skills) de Vercel Labs:

```bash
DISABLE_TELEMETRY=1 npx skills add nvv-dev/devils-advocate
```

### Verificar

Abre una sesión nueva y pregunta "¿qué skills tienes disponibles?"; `devils-advocate` debe aparecer. Con el plugin, `/plugin` la muestra como instalada.

### Actualizar o desinstalar

- Plugin: `/plugin marketplace update nvvdev` para actualizar; `/plugin uninstall devils-advocate@nvvdev` para quitarla.
- Copia manual: repite la copia para actualizar, o borra la carpeta `.claude/skills/devils-advocate`.

Antes de instalar cualquier skill, incluida esta, conviene leerla: es un solo archivo, [`skills/devils-advocate/SKILL.md`](skills/devils-advocate/SKILL.md). Ver [vetting-external-skills](https://github.com/nvv-dev/vetting-external-skills).

## Contenido

| Ruta | Qué es |
|---|---|
| `skills/devils-advocate/SKILL.md` | La skill: instrucciones en inglés para que los escáneres de seguridad las analicen completas; el agente responde en tu idioma |
| `.claude-plugin/plugin.json` | Manifiesto para instalarla como plugin |
| `.github/workflows/` | Validación de estructura y escaneo con SkillSpector en cada cambio |

## Contribuir

Este repo se **genera** desde [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow), donde vive la versión canónica. Abre issues y PRs allí. La mejor contribución es un caso real en la sección *Known failures* de la skill, con la regla que lo evita.

## Origen

Escrita desde cero por nvvdev. Inspirada en: [Hainrixz/abogado-del-diablo](https://github.com/Hainrixz/abogado-del-diablo) (eight angles), [garrytan/gstack](https://github.com/garrytan/gstack) (/office-hours forcing questions, /plan-ceo-review scope modes).

## Licencia

MIT.

---

## English

**devils-advocate** — Attacks an idea from eight angles after six forcing questions, then gives a verdict, a scope mode and a prioritized fix list.

Install in Claude Code with `/plugin marketplace add nvv-dev/claude-plugins` and `/plugin install devils-advocate@nvvdev`, or copy `skills/devils-advocate/` into `.claude/skills/` (project) or `~/.claude/skills/` (personal). Other agents: copy the folder into their skills directory, or run `DISABLE_TELEMETRY=1 npx skills add nvv-dev/devils-advocate`. Manual-only skill: invoke it with `/devils-advocate:devils-advocate` (plugin) or `/devils-advocate` (copied). Canonical source: [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow). License: MIT.
