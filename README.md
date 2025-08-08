````markdown
# Javier's Improved Fog

**Author:** [@javierbendezuv](https://www.curseforge.com/members/javierbendezuv/projects)  
**Platforms:** [CurseForge](https://www.curseforge.com/members/javierbendezuv/projects) · [PlanetMinecraft](https://www.planetminecraft.com/member/javierbendezuv/) · [Modrinth](https://modrinth.com/user/javierbendezuv) · [YouTube](https://www.youtube.com/@resourcepacksdejavierbendezuv)  
**Minecraft Java Edition** – Vanilla core shader modification

---

## 📷 Preview / Vista previa

![Preview](https://i.imgur.com/273Er1j.png)  

---

## 🇺🇸 English – Description

**Javier's Improved Fog** replaces Minecraft's default fog behavior with a **progressive density curve** for a more natural and immersive feel.  
Instead of the sudden and flat vanilla fog, this shader starts farther from the player, keeps nearby terrain crisp, and blends the distance into a smooth haze.

**Key features:**
- **Smooth, distant fog** – preserves nearby visibility while gradually increasing opacity with distance.  
- **Custom curve formula** – starts almost linear, then eases into full opacity for realism.  
- **Improved environmental blending** – merges ambient and player-centric fog calculations.  
- **Vanilla-compatible** – works with other resource packs or shaders that do not replace `fog` core shaders.  

**Recommended:** Set **render distance to 32 chunks** for the best visual experience.

---

## 🇪🇸 Español – Descripción

**Javier's Improved Fog** reemplaza la niebla predeterminada de Minecraft por una **curva de densidad progresiva** para una experiencia más natural e inmersiva.  
En lugar de la niebla abrupta de vanilla, este shader empieza más lejos del jugador, mantiene nítida la vista cercana y difumina el horizonte en una bruma suave.

**Características principales:**
- **Niebla lejana y gradual** – mantiene la visibilidad cercana mientras incrementa la opacidad de forma progresiva.  
- **Fórmula de curva personalizada** – casi lineal al inicio y suavizada al final para mayor realismo.  
- **Mejor integración ambiental** – combina el cálculo de niebla ambiental con la centrada en el jugador.  
- **Compatible con vanilla** – funciona con otros resource packs o shaders que no reemplacen el core shader `fog`.  

**Recomendado:** Configurar la **distancia de renderizado a 32 chunks** para el mejor efecto.

---

## 🔍 Code Explanation

### `linear_fog_value(vertexDistance, fogStart, fogEnd)`
Calculates fog intensity between two distances:
- Returns `0.0` if the object is closer than `fogStart`.  
- Returns `1.0` if it's farther than `fogEnd`.  
- Returns a linear interpolation between these values for in-between distances.

### `total_fog_value(sphericalVertexDistance, cylindricalVertexDistance, ...)`
Combines **environmental fog** (spherical) and **player-centric fog** (cylindrical):
- Uses `start_multiplier` and `end_multiplier` to tweak fog start/end distances.  
- Adds both fog types together and clamps the value between `0.0` and `1.0`.  

### `apply_fog(inColor, ..., fogColor)`
Applies the final fog effect to a fragment:
- Scales `fogValue` for earlier fog appearance.  
- Uses a **custom progressive curve**:  
  ```glsl
  curvedFog = pow(fogValue, 1.1) / (pow(fogValue, 1.1) + pow(1.0 - fogValue, 3));
````

* **pow(fogValue, 1.1):** Controls how quickly fog starts appearing.
* **pow(1.0 - fogValue, 3):** Controls how fast it reaches full opacity.
* Mixes the original color with `fogColor` based on the curve output.

### `fog_spherical_distance(pos)`

Returns the Euclidean distance from the camera to the point.

### `fog_cylindrical_distance(pos)`

Calculates the maximum of horizontal and vertical distances for more uniform fog in all directions.

---

## 📜 Credits

* Shader concept & code: **[@javierbendezuv](https://www.curseforge.com/members/javierbendezuv/projects)**
* Platforms:

  * [CurseForge](https://www.curseforge.com/members/javierbendezuv/projects)
  * [PlanetMinecraft](https://www.planetminecraft.com/member/javierbendezuv/)
  * [Modrinth](https://modrinth.com/user/javierbendezuv)
  * [YouTube](https://www.youtube.com/@resourcepacksdejavierbendezuv)
* License: Free to use and modify with credit to the author.

---

```
```
