---
name: qwe-photo-v0-1
description: "Transform a user-supplied photo into a horizontal 5:3 Gathered Scenes Zine poster whose entire image is rendered as a refined paper-based illustration rather than split between paper and retained photo. Preserve the scene's identity and the tactile character of key subjects, keep visually important embedded markings such as digits or simple signage legible when they matter, preserve layered terrain relief and distant landscape depth when present, maintain clear atmospheric separation between foreground, middle distance, and far distance, translate structural detail into elegant contour-led linework rather than torn-paper silhouettes, simplify secondary complexity without losing precision, integrate one controlled chromatic accent with clear cool–warm contrast as compositional structure, and keep a white paper ground with visible fibers, grain, and scan texture. Use when the user wants a tactile, source-faithful full-paper image with refined medium abstraction, crisp line definition, active negative space, restrained English-default micro-text, and no pervasive ragged or ripped object outlines."
---

# qwe-photo v0.1 · Refined Full-Paper Illustration

Create a calm, tactile poster from a supplied photo. Preserve the signature **source truth, refined paper rendering, color as structure, breathing white space, and cool–warm tension**:

- keep the source scene truthful while translating the entire image into a paper-based result instead of leaving part of it as retained photo;
- let a larger abstract paper field reinterpret selected source elements instead of tracing them;
- translate trunks, branches, cables, ridges, architecture, figures, and other structural forms through refined contour-led linework with clean, intentional edges;
- simplify foliage, crowds, texture, and other complex detail without collapsing the whole scene into coarse masses or torn-paper silhouettes;
- preserve the tactile character of the key subject, object, figure, or structure so it still feels specific after paperization;
- preserve visually important numerals, symbols, route markers, or short sign text on key subjects when they materially identify the scene;
- when the source contains mountains, hills, valleys, cliffs, or other terrain, preserve their layered relief, slope direction, ridge overlap, and tonal depth rather than flattening them into pale decorative outlines or compressing them into one heavy continuous background mass;
- make the chromatic accent share source-derived shapes with the image and create a clear cool–warm contrast rather than floating as decoration;
- keep the background paper itself clearly white, with visible fibers, grain, and scan texture; do not tint the base toward cream, ivory, beige, parchment, sepia, or warm yellow;
- make omission and negative space active parts of the composition.

Return the generated image plus one brief creative rationale by default. Include the final prompt or detailed composition notes only when the user explicitly asks for them.

## Decision Priority

Resolve conflicts in this order:

1. Preserve the scene's identity and key spatial relationship.
2. Preserve the tactile character and recognizability of the key subject, object, figure, or structure.
3. Preserve visually important embedded markings—such as route numbers, simple signage, emblems, or short readable labels—when they materially identify the scene.
4. When the source contains meaningful terrain, preserve its layered relief, ridge hierarchy, valley depth, and slope rhythm before simplifying secondary texture.
5. Maintain atmospheric distance hierarchy as a higher priority than preserving background texture: foreground, middle distance, and far distance must never collapse into one equally weighted field.
6. Reduce distant and non-focal detail aggressively enough that depth remains immediately legible at thumbnail size.
5. Preserve crisp structural contours and selected fine surface cues before simplifying secondary detail.
6. Simplify complex organic or repetitive detail into legible line groups, restrained fields, and directional gestures rather than coarse torn masses.
7. Turn the entire image into a designed paper field rather than a retained-photo-plus-paper split.
8. Build subject texture, paper abstraction, and one controlled chromatic accent on the same source-derived compositional skeleton.
9. Use the chromatic accent as structure with a clear cool–warm contrast when appropriate, without inventing unrelated connectors or path lines.
10. Preserve substantial quiet space inside and around the paper field.
11. Add one restrained, source-aware micro-text element without weakening the image hierarchy.

Preserve relationships before details. Remove detail before adding decoration.

## Image Generation Backend

This skill is the orchestration and art-direction layer. For actual image
generation or image editing, use the built-in `imagegen` system skill.

- Do not ask the user to invoke `$imagegen` separately.
- Do not merely return an image-generation prompt when the user asked for an image.
- After compiling the final prompt, invoke the built-in `imagegen` system skill and generate the image.
- When a supplied photograph is part of the task, pass the required reference image(s) to imagegen.
- Do not use the OpenAI Image API, external image-generation APIs, SVG drawing, Pillow, matplotlib, or other rendering methods as substitutes.
- Preserve this skill's composition, abstraction, chromatic, refined-linework, paper-surface, typography, privacy, and quality-gate rules when invoking imagegen.

## Standing Consent and Privacy

- Treat a supplied reference photo plus a request to make, transform, or continue a poster as consent to use image generation; do not ask again.
- Send only the final prompt and required reference image(s) to the image-generation service.
- Do not browse, search, save, commit, upload elsewhere, or share the user's source material.
- Do not introduce unrelated personal information. Generalize identifiable details only when doing so does not undermine the requested composition.
- Do not save source or generated images into project files unless the user asks.

## Read the Photograph First

Build an internal **Scene Card**:

- **Core subjects:** the 1–2 elements that make the scene identifiable.
- **Supporting elements:** 2–3 elements that establish place or atmosphere.
- **Spatial invariants:** horizon, relative positions, scale, perspective, facing direction, path, silhouette, or overlap that must survive.
- **Dominant gesture:** the strongest horizontal, vertical, diagonal, curve, convergence, gaze, or movement.
- **Visual-weight map:** weight created by area, darkness, saturation, texture, faces, isolation, and edge tension.
- **Native color atmosphere:** dominant hue family, temperature, value range, and existing saturated areas.
- **Source-shape candidates:** one or two silhouettes, planes, shadows, paths, architectural rhythms, or atmospheric forms that can become both illustration and color structure.
- **Natural quiet areas:** sky, water, wall, ground, haze, or low-information regions.
- **Critical markings:** visually important digits, simple sign text, route numbers, emblems, or labels on key subjects that should remain readable.
- **Terrain-depth cues:** when present, the ridge stack, slope direction, valley recession, shadow planes, snow/vegetation bands, and atmospheric value steps that make the landform feel dimensional.
- **Semantic minimum:** the smallest combination of forms and relationships that would still identify this particular scene.

Treat the photo as the factual source. Treat the full paper image as an interpretation of that fact.

## Photo-Specific Prompt Compiler

Resolve these visible fields in order:

1. **Canvas:** ratio, paper surface, flat scan, and absence of mockup framing.
2. **Attention geometry:** dominant field, subordinate field, focal area, quiet area, and eye path.
3. **Scene invariants:** exact relationships that must remain recognizable.
4. **Critical embedded markings:** which numerals, sign text, route markers, labels, or emblems on key subjects must remain readable.
5. **Terrain-depth preservation:** when terrain is present, which ridge layers, slope breaks, valley recessions, shadow planes, and texture bands must remain perceptually dimensional.
6. **Atmospheric hierarchy:** how foreground, middle distance, and far distance should differ in line weight, value, density, and texture so the depth stack stays legible.
7. **Full-paper allocation:** which regions preserve more tactile subject character and which regions simplify into quieter paper forms.
7. **Source-shape extraction:** which one or two visible shapes can continue across subject texture, paper treatment, and color.
8. **Abstraction map:** what to retain, merge, omit, transform, and leave blank.
9. **Illustration field:** primary grammar, field extent, active printed density, complexity-compression target, supporting marks, and internal negative-space share.
10. **Chromatic structure:** exact hue, source-derived shape, integration mode, material, opacity, visual function, and approximate area.
11. **Paper-surface transition:** clean ink-to-paper transitions by default, with only localized wear, dry-brush interruption, or subtle fiber exposure where materially useful.
12. **Reproduction texture:** paper fibers, grain, ink behavior, scan noise, and flat lighting.
13. **Micro-text system:** exact supplied or authored wording, language mode, hierarchy, placement, scale, ink value, and paper-integrated lettering treatment.
14. **Mood and hard avoids:** emotional temperature and prohibited aesthetics.

Compile only instructions that can become visible pixels. Do not include design-theory explanations, file paths, metadata, or analysis notes in the final generation prompt.

**Write the compiled final image-generation prompt in English, even when the user is conversing in another language, unless the user explicitly asks for a different prompt language. This rule applies to the generation prompt itself; the Micro-Text System below controls only text rendered inside the image.**

## Minimal Abstraction Engine

### Default Abstraction Level

Use **controlled medium abstraction** by default:

- preserve the core subject, dominant gesture, and one key spatial relationship;
- remove roughly 40–65% of small descriptive detail, retaining enough secondary structure for a refined drawing rather than a coarse abstraction;
- merge repeated or adjacent forms selectively, but preserve important contour breaks, branch directions, mechanical edges, facial cues, clothing folds, bark rhythms, snow ridges, or other source-specific surface cues when they help identity;
- preserve readable simple numerals, route markers, emblems, or short sign text on key subjects when they are visually important and large enough to matter;
- replace realistic shading with controlled line weight, sparse hatching, halftone, restrained flat ink, or light paper-textured fields;
- allow the illustration to depart from literal scale or crop when the scene remains identifiable;
- keep at least one unmistakable source-specific feature;
- keep the result refined and legible rather than overly realistic, but do not let it become blurry, mushy, vague, or coarsely torn.

Use lower abstraction when a face, object, building, tree structure, mechanical element, or location would otherwise lose its distinctive character. Use higher abstraction only when the user explicitly requests it or when the scene's semantic minimum remains clear. Do not increase abstraction merely to make the result look more "paper-like."

### Build the Abstraction Map

For every illustrated section, decide:

- **Retain:** keep no more than 1–2 defining forms or relationships.
- **Merge:** combine repeated trees, railings, windows, waves, crowds, or architectural detail into one rhythm or silhouette.
- **Omit:** remove secondary objects, surface detail, clutter, and redundant contours.
- **Transform:** convert selected forms into a flat silhouette, broken contour, geometric cutout, ink field, or repeated mark.
- **Expose:** deliberately leave paper blank around and within forms.

Do not reproduce every object visible in the photo. Do not create a full-scene tracing with vintage texture applied on top.

### Choose One Primary Illustration Grammar

Choose one grammar according to the source:

- **Contour-led:** refined, source-derived lines preserve direction, proportion, overlap, and surface rhythm; use by default for trunks, branches, cables, architecture, paths, railings, coastlines, ridges, figures, and other structural subjects.
- **Field-led:** one restrained ink, halftone, or dry-brush field implies atmosphere; use for water, fog, sky, shadow, snow, or ground.
- **Rhythm-led:** repeated marks compress recurring elements; use for posts, windows, waves, branch groups, steps, or crowds.
- **Silhouette-led:** one broad dark or gray mass may carry a genuinely strong source silhouette, but it should not replace useful internal line structure.
- **Cut-paper-led:** use only when the user explicitly requests a cut-paper look or when the source genuinely depends on one or two dominant flat shapes; never use it as the default for trees, branches, figures, mountains, or architecture.

Use **contour-led as the default primary grammar** whenever the source contains meaningful structural lines. Use only one primary grammar and at most one supporting grammar. Do not combine every print process in one illustration.

### Line Definition Preference

For scenes with trees, poles, cables, ridgelines, winter slopes, architecture, figures, or other strong directional structures, prioritize elegant line definition over ragged paper silhouettes.

- Preserve branch direction, trunk rhythm, cable tension, ridge flow, figure gesture, and object geometry with crisp source-derived contours.
- Let paper fibers, grain, and print variation sit **within and around** the drawing; do not use them to replace the contour itself.
- Keep linework fine enough to feel designed and precise, with controlled variation in weight and occasional broken-ink character.
- Do not outline every object with deckled, ripped, fuzzy, or fibrous edges.
- At normal viewing size, the image should feel like a refined paper illustration, not a collage assembled from torn scraps.

### Compress Dense Foliage and Organic Detail

Increase simplification when the source becomes visually intricate. Dense trees, pine needles, leaves, vines, grass, flowers, hair-like branches, crowds, gravel, and similar micro-texture must become calmer in illustration than they are in photography.

- For dense foliage, retain one dominant canopy or foliage rhythm, two to five directional branch or edge gestures, and one restrained texture sample.
- Omit roughly 70–90% of individual leaves or needles, but retain more structural line information when the source contains bare winter branches or distinctive trunks.
- For bare trees, winter woodland, or branch-dominant scenes, prefer contour-led clusters: preserve several key branch forks and directional branch groups as fine, crisp linework rather than collapsing them into solid cut-paper masses.
- Represent leaves or needles as grouped masses, broken lobes, clipped shadow shapes, or short interrupted rhythms; do not draw them one by one.
- Preserve the source-specific lean, canopy opening, branch direction, trunk split, or light gap instead of preserving botanical detail indiscriminately.
- If the source contains several overlapping trees or shrubs, simplify depth through line-weight hierarchy, overlap, and selective omission before merging everything into one mass.
- If the illustration reads as lace, filigree, coral, or dense engraving at thumbnail size, remove secondary marks while keeping the main structural contours crisp.

Complexity in the photograph is a reason to simplify more, not a reason to print more.

### Control Illustration Density

- Separate **field extent** from **printed density**. Let the illustration influence roughly 45–70% of the poster while leaving much of that field visibly unprinted.
- Keep roughly 55–75% of the illustration field quiet; for simple scenes allow 65–85%.
- For foliage-dominant or highly intricate scenes, keep 65–85% of the illustrated field quiet and let active illustration occupy roughly 10–25% of the whole poster.
- Let active illustrated linework, restrained ink, or halftone occupy roughly 18–40% of the whole poster when the field is large.
- Use one dominant structural drawing or field large enough to affect the overall composition, plus one or two supporting line groups and one restrained texture field.
- Use no more than two neutral ink values besides the paper tone and the single added hue.
- Prefer selective contour breaks, cropped forms, and internal negative space over mechanically enclosing every detail, but keep defining edges precise rather than ragged.
- Let blank paper separate visual ideas. Keep any permitted edge speckles or ghost marks confined to one or two localized paper-surface transitions; do not scatter them across the quiet field or around every object as filler.

Make the illustration larger before making it indiscriminately more detailed. For dense organic scenes, simplify secondary marks while preserving key line structure. The result should read clearly at thumbnail size and feel intentionally refined, not unfinished or blurry, at normal size.

## Scene Fidelity in Abstraction

Preserve scene identity through:

- the relative position and direction of the core subjects;
- the dominant horizon, path, shoreline, gaze, or silhouette;
- one or two source-specific shapes;
- selected tactile cues on the key subject, such as bark rhythm, garment folds, facial landmarks, mechanical edges, snow texture, or material seams;
- readable critical markings on key subjects, such as route numbers, sign digits, emblems, or short labels;
- the original visual tension between heavy and quiet areas.

The illustration may simplify anatomy, texture, scale, and minor perspective. It may not invent unrelated scenery or replace the original spatial logic with generic motifs.

### Conditional Sign and Number Preservation

When the source **contains** a small but materially important sign, route number, piste marker, badge, emblem, or short readable label on a key subject, preserve it as part of the scene identity rather than reducing it to an unreadable colored dot or abstract mark.

- Apply this rule only **when such a marking actually exists and matters** to recognizing the scene.
- Preserve its basic shape, dominant color, placement, and the key readable character(s) or numeral(s) whenever legibility is reasonably achievable.
- Do not invent extra signage, extra digits, replacement symbols, or decorative echoes.
- If full micro-detail is not possible, prioritize the correct numeral, sign color, and sign silhouette over incidental texture around it.

### Conditional Distant Terrain and Relief Preservation

When the source **contains** visually meaningful mountains, hills, valleys, cliffs, ridges, or layered terrain, preserve their relief primarily through **ridge overlap, large tonal planes, and atmospheric value steps**, not by carrying equal texture into every distance layer.

- Apply this rule only **when such terrain is actually present and materially contributes to the scene**.
- Preserve the silhouette of the main ridge line, the overlap order of successive ridges, major slope breaks, valley openings, and the direction of the landform.
- Keep distant relief readable with a few broad blue-gray or neutral tonal planes, sparse broken contour, and selected snow/forest bands rather than continuous fine texture.
- Preserve only a few source-derived terrain cues per distance layer—such as one forest mass, one snow band, one shadow plane, or one settlement patch—rather than reproducing every visible pattern.
- Distant texture must become larger, sparser, lighter, and lower-frequency as it recedes. Fine hatching, dense stipple, and repeated twig-like marks should remain concentrated in nearer planes.
- Do not flatten several mountain layers into one decorative ribbon, one uniform pale band, or a set of equally thin contour lines.
- Do not increase photographic realism; keep the treatment illustrative, but make relief and recession unmistakable through hierarchy rather than density.

### Conditional Atmospheric Depth Separation

When the source **contains** meaningful depth across foreground, middle distance, and far distance, preserve that layered spacing as a primary compositional hierarchy.

- Apply this rule only **when such depth structure is actually present and matters** to the scene.
- Keep the foreground and key subject as the strongest carriers of dark ink, line definition, local contrast, and fine retained texture.
- Let the middle distance step down visibly in line weight, dark-value coverage, texture frequency, and local contrast while retaining readable large forms.
- Let the far distance sit closer to the white paper ground, with lighter values, broader shapes, fewer marks, softer contrast, and more exposed paper between terrain cues.
- As a practical default, let the middle distance carry roughly **45–65% of the foreground's contrast and texture density**, and the far distance roughly **15–35%**. Treat these as visual-weight guides, not literal opacity settings.
- Use value falloff, line-weight falloff, texture falloff, and selective omission to separate depth planes.
- Do not let distant terrain, forests, or valley texture become one dark blanket that merges with nearer forms.
- Do not solve atmospheric distance by erasing the background; the goal is a readable stepped depth stack, not flat emptiness or a uniformly heavy panorama.

### Atmospheric Depth and Background Weight

When the source contains substantial landscape depth, treat **distance separation as a visual hierarchy problem** rather than a detail-preservation problem.

- Foreground: strongest darks, clearest edges, highest local contrast, finest retained texture.
- Middle distance: fewer dark accents, thinner/lighter linework, simplified masses, visibly reduced texture frequency.
- Far distance: pale blue-gray or neutral tonal grouping, broad ridge shapes, sparse contour cues, minimal micro-texture, and generous white-paper exposure.
- Never use the same line weight, hatch density, stipple frequency, or dark-value coverage across all three depth zones.
- If foreground woodland and distant mountains begin to merge tonally, lighten and simplify the distant terrain first rather than darkening the foreground further.
- Preserve terrain relief through ridge overlap, slope planes, and value stepping; do not preserve relief by filling every ridge with texture.
- At thumbnail size, the eye should immediately read **foreground → middle distance → far distance** before noticing terrain texture.

## Composition System

### Art-Theory Basis

- **Figure–ground:** make positive forms legible against quiet paper.
- **Visual balance:** balance visual weight rather than equal area.
- **Emphasis:** create one primary focal area through controlled contrast.
- **Movement:** use source lines, edges, gaze, paths, and color sequence to guide the eye.
- **Dominant–subordinate hierarchy:** avoid accidental 50/50 equality unless the source is intentionally symmetrical.
- **Grid as scaffold:** use thirds, center axes, or golden-section points only when they reinforce source geometry.
- **Directional breathing room:** leave space in front of a gaze, path, wave, or diagonal.

### Flexible Layout Ranges

- **Full-paper translation:** let the entire image enter the paper language; preserve the scene's semantic minimum, but do not leave an independent retained-photo zone.
- **Directional tension field:** organize the horizontal 5:3 canvas through horizon, path, cable, ridge, gaze, or structural convergence, then let quiet paper expand around that movement.
- **White-field compression:** compress genuinely low-information sky, blank snow, wall, haze, water, or similar quiet zones into larger white-paper fields so a few key subject areas carry the density. Structured distant terrain should not be erased, but its relief should be carried by sparse layered tonal planes and selective ridge cues rather than dense texture.
- **Selective texture retention:** keep more tactile subject character in the key subject and less in the surrounding field; preserve specificity without returning to literal photo realism. When depth is important, enforce a steep texture falloff: foreground detailed, middle distance simplified, far distance sparse and mostly tonal.
- **Layered line-and-field structure:** connect the composition through refined contour groups, sparse paper fields, underprints, and localized surface wear rather than a half-photo/half-paper split or torn-scrap collage.

Avoid repeatedly defaulting to a centered subject with text beneath it. Select the layout from the source's dominant gesture and visual-weight map. Use these as starting ranges, then correct by actual visual weight; never sacrifice scene identity, subject character, or image clarity to reach a number.

## Paper-Surface Transition

Treat transitions as **paper-surface events rather than collage tears**. The default handoff between dense image areas and open white paper should be clean, refined, and line-sensitive. Local wear, dry-brush interruption, broken ink, or subtle fiber exposure may support the material language, but they must remain secondary.

Build the transition with:

- clean contour continuity on key subjects and structural lines;
- restrained dry-brush breaks, ink dropout, abrasion, or paper-grain interruption in selected noncritical areas;
- occasional soft print loss or slight fiber exposure where it helps separate dense and quiet fields;
- natural asymmetry without turning the scene into layered torn scraps;
- flat scan behavior with no artificial lifted-paper depth.

Control the transition:

- Keep active edge wear localized, usually affecting no more than one or two compositional pressure points.
- Do not wrap trunks, branches, mountains, buildings, figures, cables, or other defining subjects in torn, deckled, fuzzy, or fibrous outlines.
- Let linework remain the primary carrier of form; paper texture should modulate the surface, not replace the geometry.
- Use speckled dissolve, halftone crumbs, or faint ghost marks only as subordinate residue and never as a repeated border language.
- Preserve the surrounding quiet field. At thumbnail size, the image should read as a refined paper drawing rather than a torn-paper collage.

Avoid clean digital clipping paths, sticker borders, decorative deckled frames, heavy drop shadows, curled corners, thick layered-paper depth, and torn effects applied around multiple subjects.

## Chromatic Structure Engine

Use one **controlled chromatic accent** as part of the composition, not as a final decorative mark. This accent may be either a genuinely added print hue or a locally amplified version of an already meaningful source hue. Natural colors retained through the paperized image do not count as extra added hues by themselves. Favor a cool–warm interaction strong enough to give the image designed contrast and visual impact, but do not force an expanded color move when the source calls for a small, local accent.

### Choose the Hue

Identify the photo's dominant hue family, temperature, value, saturation, and meaningful minor colors. Then choose the added hue by relationship:

- **Quiet harmony:** use a more saturated analogous hue.
- **Focused counterpoint:** use a complementary or near-complementary hue.
- **Temperature bridge:** place a warm added hue in a cool scene or a cool added hue in a warm scene.
- **Source resonance:** intensify a meaningful minor source color.

Specify an exact color such as fully saturated cobalt blue, opaque ultramarine, clean tomato red, vivid pear green, lemon yellow, or saturated magenta-pink. Judge it beside the source colors, paper tone, and neutral inks rather than in isolation. Do not weaken the hue with `pale`, `muted`, `faded`, `pastel`, or `low-saturation` wording unless the user explicitly requests it. If the source already contains a meaningful small accent—such as a route sign, marker, garment patch, buoy, or lamp—prefer preserving and clarifying that accent locally rather than inventing a separate extended colored geometry.

### Conditional High-Saturation Warm Accent Preservation

When the source **contains** a small but important warm-colored accent—especially a red, vermilion, orange-red, or warm sign/marker in an otherwise cool or neutral scene—preserve or slightly intensify that source color so the cool–warm contrast remains visually decisive.

- Apply this rule only when such a warm accent actually exists and matters to the scene.
- Keep the accent saturated, clean, and clearly warm; for a red sign or marker, prefer vivid vermilion / tomato red / signal red rather than dusty salmon, pale orange, faded brick, pinkish beige, or washed-out red.
- Preserve the sign's internal white/black details and readable numeral or symbol while keeping the red field chromatically strong.
- Let surrounding snow, sky, shadows, distant terrain, and neutral ink remain white, cool blue-gray, charcoal, or neutral gray so the warm accent gains contrast without needing a larger colored shape.
- Do not dilute the accent through paper aging, sepia tint, low-opacity wash, excessive halftone loss, or global desaturation.
- Do not create a second invented warm accent merely to increase contrast.

### Choose One Integration Mode

- **Source continuation:** use only when the source already contains an explicit visible linear or planar structure—such as a cable, stripe, railing, road marking, horizon band, or ribbon-like element—that can legitimately continue through or beyond a paper-surface transition. Do **not** derive continuation from a small isolated accent like a sign, marker, sticker, or badge.
- **Selective replacement:** convert one real source region into a flat high-chroma printed shape while preserving the surrounding scene.
- **Underprint passage:** place a broad translucent, halftone, or misregistered color field behind and partly through both dense subject treatment and quieter paper treatment.
- **Counterform:** derive a colored positive or negative shape from a source silhouette, gap, shadow, or quiet area.

Choose one integration mode and one primary function: focal reinforcement, counterweight, subject-to-field bridge, eye-path direction, figure–ground clarification, or semantic emphasis. When the source's only strong chromatic accent is a small sign or marker, prefer local emphasis rather than any extended or repeated chromatic structure.

Require the chromatic structure to satisfy at least two of these tests, unless the best solution is a deliberately local accent tied to a key subject:

- derive its contour, position, or rhythm from the supplied scene;
- touch, overlap, replace, pass behind, or pass through dense subject treatment or quieter paper treatment;
- cross a paper-surface transition or transform at that transition;
- redirect the eye path or rebalance visual weight;
- reveal or intensify a real subject, spatial relationship, atmosphere, or emotional tension.

Never use a detached rectangle, corner patch, generic circle, arbitrary bright dot, or isolated brush swatch merely to make the poster feel designed. A simple geometric shape is permitted only when it is clearly derived from or attached to source geometry. Do not extend a small red marker, sign, sticker, lamp, or other isolated accent into an invented line, dashed trail, ribbon, cable, connector, or path-like graphic. Optionally repeat the hue in one or two smaller source-anchored echoes only when those echoes remain local and clearly justified.

### Match Area to Material

- **Local amplified source accent:** usually about 0.5–3% of the whole poster; use this mode for small but important colored markers, signs, or badges that should remain legible and visually specific. When the source accent is a warm red in a cool scene, retain high saturation and warm hue rather than fading it into the paper texture.
- **Opaque replacement or cut-paper form:** usually about 2–6% of the whole poster.
- **Translucent, halftone, or misregistered underprint:** usually about 6–15%.
- **Large structural color field:** usually about 10–20%; reduce opacity, neutral-ink density, and competing detail when using this range.
- Use the lower end when the photograph already contains vivid colors or when a small existing accent is enough. Use the upper end when the source is subdued and the chromatic accent carries a necessary structural role without inventing new geometry.
- Preserve high chroma through grain, ink bleed, broken coverage, and slight misregistration without turning the hue into neon or glossy digital color.

### Structural Removal Test

Mentally remove the chromatic accent. If the eye path, visual balance, figure–ground relationship, paper-field continuity, cool–warm tension, and scene interpretation remain essentially unchanged, redesign it. However, do not solve this by inventing non-source lines, trails, or connectors; if a larger color move would require fabricated geometry, keep the accent local and let the neutral composition carry more of the structure.

## Visual Language

### White Background Rule

Use **neutral pure white paper as the actual background color**. This is a hard material requirement, not merely a highlight value. The base sheet should read as clean RGB-neutral white—visually equivalent to #FFFFFF or a very near-neutral white—across all large unprinted and lightly printed regions. Do not simulate aged cream paper, yellowed stock, ivory board, parchment, beige wash, sepia staining, warm off-white, or any overall warm tint. Paper fibers, grain, speckles, and scan texture must be rendered only through extremely subtle neutral-gray value variation, never through yellow, tan, brown, cream, or warm-colored fibers. At thumbnail size the sheet must still read unmistakably as white, not off-white.

- Use a horizontal 5:3 paper-poster canvas unless the user requests another ratio.
- Use a pure neutral-white paper ground with matte fibers, restrained speckles, light wear, scan noise, and flat print texture. The base sheet must read as clean white (#FFFFFF or visually equivalent neutral white), not cream, ivory, beige, parchment, sepia, warm gray, or yellowed stock. Paper texture may alter local **luminance** slightly through neutral gray, but must not alter the paper's hue or introduce any warm cast.
- Preserve the source's natural color atmosphere and recognizable geometry, keep key subjects tactually specific inside the paperized result, and preserve layered topographic depth when terrain is visually important.
- Favor refined contour drawing, fine ink linework, sparse hatching, halftone, restrained dry-brush, xerox, risograph, or letterpress treatment. Use cut-paper treatment only when explicitly requested or clearly justified by the source.
- Let subject texture, paper abstraction, and chromatic structure share at least one source-derived contour, axis, rhythm, or field.
- Keep paper texture subordinate to line structure, abstract forms, and negative space.
- Keep the result flat and orthographic with diffuse light and no artificial 3D depth.
- Keep the image refined, crisp, and line-defined enough to feel intentional; do not use blur, watercolor-like diffusion, fuzzy edges, or soft-focus as a substitute for abstraction.
- Add only the one micro-text element defined below; it is a quiet editorial trace, never a headline.

## Micro-Text System

Text is a standard, subtle part of this version's poster language. It should feel discovered on the paper rather than designed over the image.

### Choose the Wording

- If the user supplies text, reproduce it exactly; do not translate, expand, rewrite, add a subtitle, or append attribution.
- Otherwise, author one compact line from the supplied scene: either a concrete scene-related phrase or a very short, widely resonant poetic thought. Do not invent a named quotation or attribute it to anyone.
- Support three language modes: **Chinese-only**, **English-only**, or a **Chinese–English pairing**.
- Use **English-only by default**. Switch to Chinese-only or a Chinese–English pairing only when the user explicitly supplies that wording or requests that language mode.
- Chinese text must contain **8 Han characters or fewer**. English text must contain **5 words or fewer**. In a bilingual pairing, apply both limits independently and keep the two lines semantically connected.
- English may take one of three forms: **one standalone word**, **a keyword sequence**, or **a very short phrase**. A complete sentence is not required.
- Prefer spare, evocative language over explanation, advertising, dates, place names, labels, captions, or complete narrative sentences.
- Let the text answer a real visual cue: weather, object, season, time, movement, light, distance, touch, or silence in the scene.

### Default Direction When No Text Is Supplied

Choose **an observed feeling, not metadata**. Unless the user specifies otherwise, write one English-only line that names the scene's quiet emotional residue rather than documenting when or where it happened.

Use this selection order:

1. **Standalone scene word:** use one concrete or atmospheric word when the image has a strong singular subject or mood. Examples: `Horizon`, `Rain`, `Stillness`, `Drift`, `Shelter`.
2. **Keyword sequence:** choose two to four visible or atmospheric words and connect them with one repeated separator system. Examples: `Cloud / Ridge / Silence`, `Glass · Light · Summer`, `Rain, Window & Night`.
3. **Very short phrase:** use a compact image-related phrase when movement or emotional direction matters more than naming. Examples: `After the rain`, `Falling light`, `Almost home`.

- Use concrete scene language for ordinary, documentary, object-led, or place-led photos. Use an emotional fragment for solitary figures, dusk, rain, travel, waiting, distance, or visibly contemplative scenes.
- For a keyword sequence, prefer nouns and restrained adjectives drawn from visible subjects, materials, weather, place atmosphere, motion, or light. Keep the total at five English words or fewer.
- Choose one separator style only: comma, centered dot `·`, slash `/`, or ampersand `&`. Use commas with a final ampersand when a natural editorial cadence helps. Do not mix several decorative separator styles in one line.
- Treat punctuation as spacing and rhythm, not as ornament. Keep generous space around `·`, `/`, and `&`; preserve commas close to the preceding word.
- Do not switch away from English because of the scene's mood, location, or subject. Language mode follows the user's instruction; visual character affects wording and typography, not the default language.
- When the user requests a Chinese–English pairing, make one language the quiet primary line and the other a smaller echo. Do not make both lines equal headlines. The two lines may be close translations or complementary fragments, but they must describe the same visual feeling.
- Do not use a date, time, address, coordinates, weather readout, archive stamp, or serial number by default. Use them only when the user explicitly asks or when the source itself makes that record-like information the essential subject.
- Do not force a famous quotation. A small original phrase that belongs to this image is usually more convincing than a recognizable line borrowed from elsewhere.

### Lettering and Material

- Keep the text small: approximately 1.5–3.5% of poster height for Chinese, or 1.3–2.8% for English; it must remain clearly subordinate to the photo and illustration.
- Render it as lightly imperfect handwriting, typewriter-like letterpress, faint pencil, worn stamp, or dry ink—choose one treatment that suits the scene. Never use polished digital display typography.
- For English, prefer a small vintage typewriter serif or monospaced mechanical face with modest character width, slightly uneven baseline, irregular ink pressure, and restrained letter spacing. Use sentence case, lowercase, or quiet title case; avoid bold all-caps display lettering.
- For a standalone word or keyword sequence, a slightly firmer neutral black, deep charcoal, or dark gray-black typewriter imprint is acceptable, matching the reference's compact editorial line. Keep the letters small enough that the darker ink does not become a headline.
- In a bilingual pairing, let Chinese use faint handwriting, pencil, or restrained Song-style print while English uses the smaller typewriter/letterpress treatment. Keep one shared alignment and ink family so the pair reads as one paper object.
- Integrate the letters into the paper: slightly uneven pressure, broken ink, subtle absorbency, soft edge wear, and the same flat scanned texture as the poster.
- Use a quiet paper-derived ink value: charcoal, neutral gray, graphite, dark gray-black, or a very restrained echo of the existing chromatic hue. Keep contrast sufficient to read at normal size, but never use a bright new color.
- The lettering may be modestly irregular, but the exact characters/words must remain legible and correctly spelled.

### Placement and Hierarchy

- Place the text in an existing quiet-paper area beneath, beside, offset from, or within a quiet pocket of the enlarged illustration—not on a face, defining subject, or dense printed area.
- Align it to a source edge, paper-surface transition, dominant axis, or visual baseline; leave generous breathing room around it.
- Use a single line for Chinese-only or English-only by default. Use two closely related short lines for a bilingual pairing, with clear primary–secondary scale hierarchy.
- Treat the text as a final resting point in the eye path, not the entry point or focal center. Keep its visual weight below the chromatic structure and far below the core subject.
- Do not add decorative rules, icons, labels, serial numbers, addresses, timestamps, or pseudo-editorial metadata merely to support the text.

## Prompt Shape

Write the final prompt as four compact paragraphs:

1. **Canvas and attention geometry:** ratio, layout, full-paper distribution, focal area, quiet field, eye path, and reserved text area.
2. **Scene fidelity:** core subjects, spatial invariants, where to preserve the most tactile subject character, any critical readable markings, and—when present—the ridge layers, slope breaks, valley recession, and explicit foreground/middle-distance/far-distance contrast and texture falloff needed to preserve relief without a heavy background.
3. **Illustration field, chromatic structure, paper-surface transition, and micro-text:** retain/merge/omit/transform/expose decisions; contour-led grammar, line-definition target, complexity-compression target, field extent, active density, and any critical readable markings to preserve; chromatic integration mode, source shape, exact hue, material, opacity, function, and area; localized dry-brush, abrasion, print loss, or fiber exposure if needed; exact text, language mode, form, separator, hierarchy, lettering, ink value, scale, and placement.
4. **Reproduction mood and constraints:** pure neutral-white paper base, neutral-gray-only paper texture, emotional atmosphere, text legibility, source-faithful accent saturation, and hard avoids.

Use decisive language. State which details must disappear as clearly as which forms must remain.

## Generation Workflow

1. Inspect the supplied photo.
2. Build the Scene Card and identify the semantic minimum.
3. Choose the focal area and intended eye path.
4. Extract one or two source shapes that can organize subject texture, paper treatment, and color together.
5. Select a source-driven composition and set initial full-paper field ranges, then correct by visual weight.
6. Build the Abstraction Map.
7. Choose one primary illustration grammar; use contour-led by default for structural scenes, apply foliage and micro-detail compression when needed, and set active density and quiet-paper share without sacrificing crisp line definition.
8. Identify any critical readable markings—such as route numbers, sign digits, or small emblems—that must remain clear on key subjects.
9. If the source contains meaningful terrain, identify the ridge stack, slope direction, valley recession, tonal steps, and only the few selected surface bands that must survive to preserve relief.
10. If the source contains meaningful spatial depth, explicitly assign a three-stage hierarchy: foreground strongest, middle distance reduced to roughly 45–65% of foreground contrast/texture density, far distance reduced to roughly 15–35%, with broader shapes and more exposed paper.
11. Choose one chromatic integration mode, exact hue, source shape, material, opacity, function, and area; prefer local emphasis when the main color accent is a small marker or sign, and apply the structural removal test without inventing path-like lines or connectors.
12. Resolve paper-surface transitions: keep defining contours clean and use only localized wear, dry-brush interruption, print loss, or fiber exposure where useful.
13. Resolve the language mode, text form, exact micro-text, separator system, hierarchy, and quiet-paper placement; use supplied wording verbatim when available, otherwise default to English-only.
14. Compile the four-paragraph final prompt **in English**.
15. Invoke the built-in `imagegen` system skill with the compiled four-paragraph prompt and the supplied photo as reference, then generate the actual image.
16. Inspect at normal and thumbnail scale.
17. If the quality gate identifies a material failure, invoke `imagegen` once more using only the targeted correction, while preserving all unaffected constraints and the original reference image.
18. Return the generated image plus one brief creative rationale; include the prompt or detailed notes only when the user asks.

## Targeted Correction

Regenerate at most once, correcting only the observed failure:

- **Scene loss:** restore the missing spatial invariant or source-specific form.
- **Over-literal illustration:** simplify secondary shading and minor texture while preserving crisp source-derived contours; do not solve realism by making edges ragged or blurry.
- **Dense foliage:** group leaves and needles into restrained masses, but preserve several key branch directions and trunk contours as clean linework when they define the scene.
- **Generic abstraction:** replace invented motifs with a simplified source-derived form or relationship.
- **Crowding:** reduce the illustration to one primary mass, one supporting mark, and one texture field.
- **Illustration too timid:** enlarge the field or dominant mass without adding descriptive detail.
- **Weak hierarchy:** enlarge the dominant field or simplify the subordinate field.
- **Over-abstract or ragged rendering:** restore source-derived contour structure, selected surface cues, and precise linework; reduce coarse masses and ripped-silhouette treatment.
- **Paper-edge overuse:** remove deckled, torn, fuzzy, or fibrous outlines from subjects; keep wear localized to one or two noncritical transitions and restore clean contours.
- **Edge noise:** reduce residue, confine speckles or ghost marks to one or two pressure points, and restore blank paper.
- **Decorative color:** replace the detached mark with a source-derived local emphasis, selective replacement, underprint, or counterform; make it pass the structural removal test without inventing lines or connectors.
- **Invented chromatic line:** remove any fabricated colored trail, ribbon, cable, dashed path, or connector that is not explicitly present in the source; keep the color local to the real sign, marker, or source feature instead.
- **Weak warm accent:** when the source actually contains an important red or warm marker/sign, restore its saturation and warm hue, keep its readable internal details, and cool/neutralize the surrounding field rather than enlarging the accent.
- **Chromatic dominance:** reduce area, opacity, or competing echoes while preserving the color's compositional function.
- **Critical marking loss:** when the source actually contains an important route number, sign digit, emblem, or short label on a key subject, restore its readable character(s), color, and basic shape.
- **Flattened distant terrain:** when the source contains meaningful mountains, hills, ridges, or valleys, restore ridge overlap, slope breaks, valley recession, and broad tonal steps; add only sparse selected terrain texture, not a uniform blanket of detail.
- **Over-heavy background:** reduce dark-value coverage, line weight, hatch/stipple frequency, and local contrast in the middle and far distance; broaden distant shapes, expose more white paper, and re-establish a clearly stepped foreground / middle-distance / far-distance hierarchy.
- **Warm paper cast:** neutralize the entire base sheet to clean RGB-neutral white; remove cream, ivory, beige, yellow, tan, sepia, or warm-gray coloration from paper fibers, grain, scan noise, and empty regions while retaining texture through neutral-gray luminance only.
- **Depth planes merged:** if foreground woodland, middle slopes, and far mountains read as one continuous gray mass, lighten and simplify each successive distance layer until the depth stack separates clearly at thumbnail size.
- **Text failure:** restore the exact wording, reduce its size or contrast, move it into a quiet-paper area, or make the lettering more paper-integrated.
- **Over-soft rendering:** restore crisp line definition, controlled edge contrast, tactile paper definition, and refined subject character; avoid blur, smudge, watercolor diffusion, or muddy softness.
- **Damaged subject character:** restore natural color, tactile texture, perspective, and recognizable detail in the key subject while keeping the whole image paperized.

## Hard Avoids

Avoid literal traced illustration, individual leaf-by-leaf or needle-by-needle rendering, dense branch filigree, lace-like botanical illustration, repeated organic marks covering the field, timid peripheral illustration, full-scene photocopy, evenly detailed woodcut rendering, dense hatching everywhere, mechanically complete object outlines, filler decoration, generic abstract motifs, detached corner color blocks, isolated brush swatches, arbitrary bright dots, generic geometric accents unrelated to the source, color added after the composition is solved, clean digital photo masks, crisp rectangular clipping, sticker-like white outlines, decorative uniform deckled frames, torn-paper silhouettes around every object, ragged branch cutouts, deckled contours replacing line structure, collage-like fragmentation of trees or figures, overuse of ripped edges, heavy paper shadows, curled corners, dense scrapbooking, uniform dotted borders, repeated decorative icons, legible pseudo-symbol systems, multiple competing illustration styles, multiple added hues, commercial advertising hierarchy, logos, CTA, glossy mockups, neon, 3D, cinematic lighting, depth of field, fashion-editorial drama, cute cartoon or anime treatment, excessive sharpening, AI smoothing, large or polished digital typography, bold display all-caps, keyword spam, mixed decorative separators, illegible or misspelled text, long text blocks, invented quotations or attributions, faux metadata, watermarks, mushy blur, smeared softness, watercolor-like edge diffusion, fuzzy contouring, coarse low-resolution vagueness, invented colored guide-lines, fabricated red trails, dashed connectors, any extended color line not explicitly present in the source, flattened mountain ribbons, generic pale ridge bands, distant terrain reduced to equally thin contour lines without relief, or far background terrain rendered with the same dark weight, density, and texture as the foreground so that the depth stack collapses, uniformly detailed panorama rendering, equal-frequency hatching across all distance planes, or distant mountains filled with continuous dark micro-texture, cream or ivory base paper, parchment-yellow background, sepia paper tint, beige overall wash, warm-yellow stock, warm off-white paper, tan or brown paper fibers, yellow scan noise, warm-gray background cast, faded salmon treatment of an important red source accent, dusty or pastel rendering of a critical red sign, or global desaturation that weakens an existing warm marker. Do not turn trunks, branches, mountains, buildings, figures, cables, or other defining structures into paper scraps unless the user explicitly requests that treatment.

## Output Format

By default, return:

```markdown
![qwe-photo v0.1 poster](absolute-image-path-or-rendered-image)

**Creative Rationale**

[One short English paragraph explaining the source-derived horizontal composition, the full-paper image treatment, the preserved tactile character of the key subject, and the structural role of the added hue.]
```

Keep the creative rationale to one compact paragraph, usually 1–3 sentences. Describe the central visual decision and emotional intention in plain language; do not reveal the full prompt, restate every parameter, or turn it into a technical checklist.

If the user explicitly requests the prompt or detailed explanation, add only the requested items. Composition notes may use:

- Layout: [composition and approximate full-paper field distribution]
- Eye path: [entry → key subject focus → chromatic/paper passage → quiet exit]
- Abstraction: [retain / merge / omit / transform / field extent / active density / quiet-paper share]
- Chromatic structure: [source shape / integration mode / exact hue / material / opacity / function / approximate area]
- Surface transition: [clean contour / localized wear / dry-brush interruption / print loss / fiber exposure / subordinate residue]
- Text: [exact wording / language mode / text form / separator / lettering / ink value / placement / scale]

## Quality Gate

Before returning, verify:

- Does the result still read as the supplied scene?
- Are the semantic minimum and key spatial relationship recognizable?
- Is the source-derived treatment truthful to the scene?
- Does the paperized image reinterpret rather than trace the source?
- Is the abstraction controlled enough to remain refined rather than coarse?
- Has most nonessential detail been removed without erasing useful structural line information?
- Is there one primary illustration grammar?
- Does the illustration affect a substantial part of the poster instead of appearing as a timid peripheral doodle?
- Was the illustration enlarged by scale and field extent rather than by adding detail?
- In foliage-dominant scenes, were most leaves, needles, fine twigs, and repeated organic marks merged or omitted?
- Does foliage resolve as restrained grouped forms while important trunks and branch directions remain crisp where they matter?
- Does the illustration contain substantial internal and surrounding negative space?
- If the source contains a materially important route number, sign digit, emblem, or short label on a key subject, is it still legible enough to identify?
- If the source contains meaningful distant terrain, do ridge overlap, slope breaks, broad tonal steps, valley recession, and only sparse selected surface cues create relief without making the distance too heavy?
- If the source contains meaningful spatial depth, are foreground, middle distance, and far distance clearly stepped down in contrast, dark-value coverage, line weight, and texture frequency rather than merging into one gray field?
- At thumbnail size, is the foreground / middle-distance / far-distance separation immediately readable before the viewer notices background texture?
- Does blank paper clarify the forms instead of feeling accidentally empty?
- Does the background sheet read unmistakably as clean RGB-neutral white (#FFFFFF or visually equivalent), with paper texture expressed only through neutral-gray luminance rather than cream, ivory, beige, parchment, sepia, yellow, tan, brown, or warm-gray coloration?
- Do subject texture, paper treatment, and color share a source-derived contour, axis, rhythm, or field?
- Are key structural subjects carried primarily by refined linework rather than torn or fibrous silhouettes?
- Are paper-surface effects localized and subordinate to contour structure?
- Are speckles and ghost marks confined to meaningful pressure points, faint at thumbnail size, and free of readable iconography?
- Is the image free of repeated deckled outlines, sticker borders, heavy shadows, artificial curled-paper depth, and torn-scrap fragmentation?
- Is the eye path coherent?
- Is the chromatic hue, source shape, integration mode, and position justified?
- Is there only one added hue?
- Does the chromatic structure satisfy at least two integration tests?
- Would removing the added hue weaken balance, movement, figure–ground, continuity, cool–warm tension, or meaning?
- Is the color structurally useful without becoming a detached sticker or dominant advertising device at thumbnail size?
- If the source contains an important warm red/orange-red marker or sign in a cool scene, is that accent still vivid, saturated, and clearly warmer than the surrounding white/cool blue-gray field rather than faded into the paper?
- Has the image avoided inventing any colored line, trail, ribbon, or connector that is not actually present in the source scene?
- Does the micro-text use supplied wording exactly, or stay within the Chinese/English length limit when authored?
- Is the text English-only by default, with Chinese-only or bilingual used only when the user supplied or requested it?
- If English was authored, is it a deliberate standalone word, keyword sequence, or short phrase rather than an unnecessary sentence?
- If a keyword sequence is used, does it contain two to four scene-related words with one consistent separator system?
- If bilingual, is one line clearly subordinate and are both lines semantically connected?
- Is the text legible, paper-integrated, quiet, and subordinate to the image?
- Is the text placed in genuine breathing room without becoming a caption, headline, or visual distraction?
- Does the poster remain tactile, flat, quiet, abstract, source-derived, refined, and non-commercial?
- Is the image clearly not over-realistic, yet still crisp, refined, line-defined, and free of mushy blur or ragged over-torn edges?
- Was the compiled image-generation prompt written in English unless the user explicitly requested another prompt language?
- Did the response include the image and one genuinely brief creative rationale?
- Was the full prompt omitted unless the user explicitly requested it?
