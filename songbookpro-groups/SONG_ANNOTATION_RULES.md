# Príprava piesní pre SongBookPro

Tento dokument určuje spoločný formát piesní v priečinku
`songbookpro-groups/`. Vzorom je
[`Jahve On zjavuje sa nám.cho`](Jahve%20On%20zjavuje%20sa%20n%C3%A1m.cho)
a oficiálna
[dokumentácia ChordPro pre SongBookPro](https://songbook-pro.com/docs/manual/chordpro/).

## Základný princíp

Každá pripravená pieseň má dve vrstvy:

1. **Krátka mapa hore** – orientácia počas hrania.
2. **Podrobné poznámky dole** – spev, dynamika a vedenie pre prípravu
   a skúšku.

Tieto vrstvy sa čiastočne opakujú zámerne. Mapa slúži na rýchly pohľad
počas piesne, podrobný rozpis vysvetľuje prevedenie. Pri pridaní mapy sa
podrobné poznámky nesmú odstrániť ani zlúčiť do nejasného súhrnu.

Počas hrania sa kapela drží dohodnutej mapy. Odchýlku od nej dáva včas
najavo jeden určený vedúci. Poznámky nie sú určené na priebežné čítanie
každej vety počas hrania.

## Ciele

- Jedným pohľadom ukázať poradie sekcií a počet opakovaní.
- Zachovať podrobné pokyny pre skúšku.
- Používať zrozumiteľné slovenské pomenovania.
- Udržať súbor kompaktný a čitateľný na mobile aj tablete.
- Používať iba syntax podporovanú SongBookPro.
- Nemeniť text ani akordy pri úprave poznámok.

## Kompletná šablóna

```text
{title: Názov piesne}
{artist: Interpret}
{key: G}
{tempo: 120}

{textcolor: #757575}
R – S×2 – R – S – R×3 – I – P1×4 – P2×2 – R×4
{textcolor}

{start_of_chorus: Refrén}
[G]Text refrénu...
{end_of_chorus}

{start_of_verse: Sloha}
[Em]Text slohy...
{end_of_verse}

{comment: Inštrumentál · gitara}
[Em | D | C | D]

{sob: Prechod 1}
[Em]Text prvého prechodu...
{eob}

{sob: Prechod 2}
[C]Text druhého prechodu...
{eob}

{comment: Spev a dynamika}
Ak nie je uvedené inak, spievajú všetci.
1. Refrén · jemne
2. Sloha 2× · Kamil · jemne
3. Refrén · jemne
4. Sloha · Kamil + Lydka · postupne zosilňovať
5. Refrén 3× · naplno
6. Inštrumentál · gitara
7. Prechod 1 4× · postupne zosilňovať
8. Prechod 2 2× · naplno
9. Refrén 3× · naplno
10. Záver · 4. refrén ako dohra
```

Hodnoty v šablóne sú iba ukážka. Každá pieseň musí použiť svoje
skutočné poradie, obsadenie a dynamiku.

## Metadáta

Na začiatku použiť dostupné údaje:

```text
{title: Názov piesne}
{artist: Interpret}
{key: G}
{tempo: 120}
{time: 4/4}
```

`title` a `key` sú základ. `artist`, `tempo`, `time` a `capo` pridať iba
vtedy, keď sú známe alebo potvrdené. Interpreta, tóninu ani tempo nehádať
podľa podobnej piesne.

## Krátka mapa

Mapu umiestniť hneď pod metadáta. Je to prvá informácia, ktorú hudobník
potrebuje počas hrania.

```text
{textcolor: #757575}
R – S×2 – R – S – R×3 – I – P1×4 – P2×2 – R×4
{textcolor}
```

Používané skratky:

- `S`, `S1`, `S2` – sloha;
- `R` – refrén;
- `I` – inštrumentál;
- `P`, `P1`, `P2` – prechod;
- `D` – dohra;
- `×2`, `×3`, `×4` – počet opakovaní.

Používať znak `×`, nie písmeno `x`. Medzi sekciami používať pomlčku
`–`. Mapa má zostať na jednom riadku, ak sa zmestí na bežnom zariadení.

Sivú farbu po mape vždy resetovať prázdnou direktívou `{textcolor}`.
SongBookPro podporuje `textcolor` iba ako samostatnú direktívu a farbí
nasledujúci úsek. Nepoužívať ju na pokus o zafarbenie časti jedného riadka.

## Sekcie piesne

Používať podporované ChordPro bloky:

```text
{start_of_verse: Sloha 1}
...
{end_of_verse}

{start_of_chorus: Refrén}
...
{end_of_chorus}

{sob: Prechod 1}
...
{eob}
```

`sob` a `eob` sú skrátené direktívy pre blok bridge. Viditeľný názov
sekcie zapisujeme po slovensky ako `Prechod`.

Pre inštrumentál alebo dohru bez vlastného bloku použiť `comment`:

```text
{comment: Inštrumentál · gitara}
{comment: Dohra}
```

Názvy sekcií musia zodpovedať mape aj podrobným poznámkam. Spievanú
samostatnú časť nenazývať `Medzihra`; použiť `Prechod`. `Medzihra` alebo
`Inštrumentál` označuje časť bez spevu.

## Podrobné poznámky

Podrobný blok patrí pod text a akordy. Nadpis:

```text
{comment: Spev a dynamika}
```

Každý krok mapy má vlastný očíslovaný riadok v rovnakom poradí. Na
začiatku uviesť spoločné pravidlo:

```text
Ak nie je uvedené inak, spievajú všetci.
```

Potom pri jednotlivých krokoch zapisovať iba výnimky a potrebnú dynamiku.
Netreba opakovať `Spev: všetci` na každom riadku.

Vhodné slovenské pomenovania:

- `Kamil` – spieva iba Kamil;
- `Kamil + Lydka` – spievajú obaja; neoznačovať to ako duet alebo sprievodný
  spev, ak ich presné roly neboli dohodnuté;
- `všetci` – všetci určení speváci;
- `jemne` – tlmené, komorné prevedenie;
- `stredne` – stredná intenzita;
- `naplno` – plná intenzita dohodnutého obsadenia;
- `postupne zosilňovať` – postupný rast intenzity;
- `postupne stíšiť` – postupné ubratie intenzity;
- `dohra` – záverečná časť piesne;
- `na gesto` – zmenu alebo koniec určí vedúci.

Používať slová, ktorým rozumie celá kapela. Anglické pokyny ako
`lead`, `build`, `full band` alebo `outro` nepridávať, ak ich kapela bežne
nepoužíva.

## Pevné a otvorené časti

Pevná časť má presný počet opakovaní:

```text
7. Prechod 1 4× · postupne zosilňovať
```

Otvorená časť má dohodnuté minimum a jasný spôsob ukončenia:

```text
7. Prechod 1 · najmenej 2× · ďalšie opakovanie a koniec na gesto
```

Ak vedúci nedá iný pokyn, kapela pokračuje podľa pevnej mapy. Otvorené
miesta používať iba tam, kde ich kapela nacvičila.

## Akordy a text

Akordy zostávajú priamo v texte:

```text
[G]Text piesne pokračuje [D]tu.
```

Pri úprave mapy alebo poznámok:

- nemeniť akordy;
- neposúvať ich na iné slabiky;
- neopravovať text piesne bez výslovnej požiadavky;
- nemeniť existujúci zápis akordového sledu iba kvôli formátovaniu;
- zachovať aktuálne používateľské zmeny v súbore.

## Postup pri príprave ďalšej piesne

1. Prečítať celý existujúci `.cho` súbor.
2. Zachytiť metadáta, všetky sekcie, opakovania a existujúce poznámky.
3. Z existujúceho poradia vytvoriť jednu krátku mapu pod metadátami.
4. Zjednotiť viditeľné slovenské názvy sekcií.
5. Dole vytvoriť alebo zachovať blok `Spev a dynamika`.
6. Zachovať jeden riadok poznámok pre každý krok mapy.
7. Nevymýšľať spevákov, dynamiku, tempo ani počty opakovaní. Chýbajúce
   rozhodnutia označiť na doplnenie alebo sa opýtať.
8. Overiť súlad mapy, sekcií a podrobných poznámok.
9. Skontrolovať zobrazenie v SongBookPro na zariadení používanom kapelou.

## Kontrolný zoznam

- [ ] Názov a tónina sú hore.
- [ ] Ostatné metadáta pochádzajú z potvrdeného zdroja.
- [ ] Sivá mapa je hneď pod metadátami a zostáva kompaktná.
- [ ] Každá skratka v mape zodpovedá existujúcej sekcii.
- [ ] Počty opakovaní súhlasia v mape aj poznámkach.
- [ ] Všetky bloky sekcií sú správne ukončené.
- [ ] Každá zmena `textcolor` je resetovaná.
- [ ] Podrobné poznámky zostali zachované pod piesňou.
- [ ] Speváci a dynamika nie sú doplnení odhadom.
- [ ] Použité výrazy sú zrozumiteľné celej kapele.
- [ ] Text a akordy zostali pri úprave anotácií nezmenené.
- [ ] Pieseň bola skontrolovaná v SongBookPro.
