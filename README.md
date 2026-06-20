# D.Lgs 81/08 — Testo Unico Sicurezza Lavoro (struttura per Titoli + indice articoli chiave)

Repository di riferimento per parsing strutturato del **Decreto Legislativo 9 aprile 2008, n. 81** (Testo Unico sulla salute e sicurezza nei luoghi di lavoro), organizzato per i 13 Titoli + indice JSON degli articoli più referenziati nella formazione e nella consulenza. Pensato per chatbot, legal-tech, AI agents, sistemi RAG e applicativi compliance che necessitano di una rappresentazione machine-readable della struttura del decreto.

> **English summary** — Structured parsing of the Italian Legislative Decree 81/2008 (Workplace Health & Safety Act), organized by the 13 Titles. Each title is a Markdown file with YAML frontmatter (article range, key articles, related annexes, topics). A JSON index lists the most-referenced articles with rubric, subject matter, applicable sanction. Useful for chatbots, legal-tech, AI agents, RAG systems and compliance applications.

## Cosa contiene

- `titoli/01-principi-comuni.md` ... `titoli/13-disposizioni-finali.md` — 13 file Markdown, uno per Titolo, con frontmatter YAML (numero, materia, range articoli, articoli chiave, allegati correlati), sommario, articoli chiave commentati, temi trattati e note di modifiche successive.
- `data/articoli-chiave.json` — indice machine-readable di oltre 65 articoli più referenziati: numero, titolo, rubrica ufficiale, materia trattata, riferimento sanzionatorio.

## Indice dei 13 Titoli

| Titolo | Materia | Articoli |
|--------|---------|----------|
| I | Principi comuni | 1–61 |
| II | Luoghi di lavoro | 62–68 |
| III | Uso delle attrezzature di lavoro e DPI | 69–87 |
| IV | Cantieri temporanei o mobili | 88–160 |
| V | Segnaletica di salute e sicurezza | 161–166 |
| VI | Movimentazione manuale dei carichi | 167–171 |
| VII | Attrezzature munite di videoterminali | 172–179 |
| VIII | Agenti fisici (rumore, vibrazioni, CEM, ROA) | 180–220 |
| IX | Sostanze pericolose (chimico, cancerogeno, amianto) | 221–265 |
| X | Esposizione ad agenti biologici | 266–286 |
| XI | Protezione da atmosfere esplosive (ATEX) | 287–297 |
| XII | Disposizioni in materia penale e di procedura penale | 298–303 |
| XIII | Disposizioni finali | 304–306 |

## Esempio uso (JSON)

```ts
import data from "./data/articoli-chiave.json";

const obblighiPreposto = data.articoli.find((a) => a.art === 19);
// { art: 19, titolo: "I", rubrica: "Obblighi del preposto", ... }

const articoliTitoloIV = data.articoli.filter((a) => a.titolo === "IV");
// art. 89, 90, 91, 92, 96, 97, 98, 100, 111, 115, 116, 117, 122, 136
```

```python
import json
with open("data/articoli-chiave.json") as f:
    data = json.load(f)
formazione = next(a for a in data["articoli"] if a["art"] == 37)
print(formazione["rubrica"])  # "Formazione dei lavoratori, dei preposti e dei dirigenti"
```

## Disclaimer

Questo repository contiene **sintesi strutturate** dei Titoli e degli articoli chiave del D.Lgs 81/08. **Non sostituisce il testo ufficiale.** Il testo coordinato e vigente è consultabile su [Normattiva](https://www.normattiva.it/uri-res/N2Ls?urn:nir:stato:decreto.legislativo:2008-04-09;81). Le modifiche successive (D.Lgs 106/2009, D.L. 146/2021, D.L. 19/2024, ecc.) sono indicate nella sezione "Note di modifiche successive" di ciascun Titolo, ma per applicazioni operative è sempre necessario verificare la versione vigente.

## Versione consultabile online

Una versione narrata con esempi pratici, casi applicativi e FAQ per RSPP, datori di lavoro, dirigenti e preposti è disponibile su [Normativa sicurezza lavoro di 123Formazione](https://123formazione.com/normativa-sicurezza-lavoro).

## Contributi

Pull request benvenute per: correzione di refusi, aggiornamento delle "Note di modifiche successive", arricchimento dell’indice JSON con articoli ulteriori, traduzioni dei sommari. Mantenere lo schema YAML/JSON esistente e segnalare la fonte normativa.

## Licenza

- Testi e sintesi dei Titoli (`titoli/`): **CC BY-SA 4.0** — vedi `LICENSE-CC-BY-SA`.
- Indice JSON e codice di esempio (`data/`, snippet README): **MIT** — vedi `LICENSE-MIT`.

## Citazione

Vedi `CITATION.cff`.
