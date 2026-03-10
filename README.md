# Optimeringskurs

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pyomo](https://img.shields.io/badge/Pyomo-6.x-orange?style=for-the-badge)
![Solver](https://img.shields.io/badge/Solver-GLPK%20%7C%20IPOPT-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow?style=for-the-badge)

Oppgaver og modeller fra et kurs i matematisk optimering. Bruker **Pyomo** som modelleringsspråk og løsere som **GLPK** (lineære/heltallsproblemer) og **IPOPT** (ikke-lineære problemer).

---

## Innhold

| Fil | Type | Beskrivelse |
|-----|------|-------------|
| `fabrikk.py` | Lineær programmering (MIP) | Maksimerer profitt for en fabrikk som produserer to produkter under kostnads-, CO₂- og malingsrestriksjoner |
| `optimering.py` | Ikke-lineær optimering (NLP) | Finner optimal lokasjon for et nytt kontor basert på avstand og kostnad til eksisterende kontorer |

---

## Modeller

### Fabrikk (fabrikk.py)

Bestemmer hvor mange enheter av produkt **A** og **B** en fabrikk skal produsere for å maksimere nettoprofitten.

**Beslutningsvariabler:**
- $x_A$ — antall enheter av produkt A
- $x_B$ — antall enheter av produkt B

**Objektivfunksjon:**
$$\max \quad (p_A - k_A) \cdot x_A + (p_B - k_B) \cdot x_B$$

**Restriksjoner:**
| Restriksjon | Grense |
|-------------|--------|
| Total produksjonskostnad | ≤ 10 000 000 kr |
| CO₂-utslipp | ≤ 20 000 kg (20 tonn) |
| Malingstimer (5 FTE) | ≤ 8 750 timer |

---

### Kontorlokasjon (optimering.py)

Finner den optimale geografiske plasseringen $(x, y)$ for et nytt kontor slik at vektet avstand til eksisterende kontorer minimeres.

**Objektivfunksjon:**
$$\min \quad \sum_{k} c_k \cdot \sqrt{(x - x_k)^2 + (y - y_k)^2}$$

---

## Kom i gang

### Krav

```bash
pip install pyomo
brew install glpk          # GLPK-solver (MIP)
brew install ipopt         # IPOPT-solver (NLP)
```

### Kjør modellene

```bash
python fabrikk.py
python optimering.py
```

---

## Teknologi

| Verktøy | Rolle |
|---------|-------|
| [Pyomo](http://www.pyomo.org/) | Modelleringsspråk for optimering i Python |
| [GLPK](https://www.gnu.org/software/glpk/) | Løser for lineære og heltallsproblemer |
| [IPOPT](https://github.com/coin-or/Ipopt) | Løser for ikke-lineære problemer |
