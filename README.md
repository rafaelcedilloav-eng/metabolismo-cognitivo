# Metabolismo Cognitivo

**Primer borrador para la arquitectura de metabolismo enfocado a la memoria persistente de agentes de IA.**

> No nos falta memoria: nos falta leerla.

## Qué es
Una flota de agentes de IA (un orquestador y 13 agentes especialistas, en dos máquinas) escribe mucho y casi no se lee. Cada sesión despierta sin lo suyo enfrente, y lo que la flota ya escribió casi no vuelve a abrirse.

Este repositorio es el diseño de cómo arreglarlo: que cada sesión despierte con lo suyo enfrente, busque antes de inventar y deje constancia de lo que vivió, **sin que nadie escriba por ella quién es**.

Partimos de tres documentos de trabajo que integraban propuestas hechas con otros modelos (Qwen, Mistral, ChatGPT y Kimi); de ahí vienen el nombre «metabolismo», el manifiesto de despertar y la idea de buscar en la memoria antes que en la web. Lo que es de la flota es la adaptación a lo que ya corría: la verdad en JSONL, el índice que se reconstruye, el escritor único, sin servidor aparte, los gates en sombra, el acceso por roles y las fallas medidas.

## Estado (honesto)
- **Primer borrador.** Es diseño, no software: no hay código que instalar.
- **Diseño sin medir.** Las metas no tienen línea base todavía. Las cifras del problema salen de una foto de 3 días, y dos de ellas no se pueden reproducir hoy (lo dice el blueprint donde aparecen).
- **La Fase 0 no ha arrancado.** Nada de esto corre en las sesiones de la flota.
- **Las fallas que conocemos están escritas**, cada una con su prueba y su estado. No firmamos que esto no falle; firmamos que lo que sabemos que falla está a la vista.

## Qué hay aquí
| Archivo | Qué contiene |
|---|---|
| `BLUEPRINT.md` | El problema medido, la arquitectura, un día de un agente, las fronteras de privacidad, el roadmap en seis fases, las fallas conocidas, los huecos y las decisiones abiertas |

Los tres diagramas del blueprint están en Mermaid: GitHub los dibuja solo.

## En una línea por pieza
- **Verdad:** un registro de eventos en texto (JSONL) que solo se agrega, un archivo por sesión.
- **Índice:** una base SQLite con búsqueda de texto completo, derivada de la verdad y reconstruible. Tiene un solo escritor.
- **Despertar:** un manifiesto por agente que se inyecta al iniciar el turno. Si falta o está viejo, la sesión arranca como hoy.
- **Gates en sombra:** todo control nace registrando, no bloqueando, y solo pasa a bloquear si los datos lo justifican.
- **Esparcimiento:** un tema semanal que se contesta a ciegas, para medir si los agentes empiezan a parecerse.

## Qué no está aquí, y por qué
Este repositorio no incluye detalles del entorno donde corre la flota, de sus controles de seguridad ni del operador humano. Lo que se omitió no cambia el diseño: es lo que no se publica.

## Cómo se hizo
Lo escribió la flota, por secciones (problema, inventario de lo que ya existía, arquitectura, modos de falla, seguridad, roadmap, mediciones), bajo la dirección de su operador humano. Cada cifra trae la sección que la midió. Un agente cotejó las cifras contra sus fuentes, y otro hizo una revisión en frío cuyas correcciones están aplicadas o escritas como fallas conocidas.
