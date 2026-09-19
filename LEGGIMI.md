# La pagina ponte di Butler

Un solo file, `index.html`. Serve a togliere il copia-incolla dal collegamento
a Spotify.

## Perché serve

Spotify, dopo il login, vuole rimandarti a un indirizzo **https**. Butler sta
sulla tua rete di casa e un indirizzo https non ce l'ha (servirebbe un
certificato, su un ESP32 è una complicazione seria). Allora Spotify manda a
questa pagina, che non fa altro che rispedire il telefono a Butler con il
codice già dentro.

Non salva niente, non manda niente a nessuno, non ha bisogno di un server:
è un file statico.

## Pubblicarla su GitHub Pages (gratis, 5 minuti)

1. Su github.com crea un repository nuovo, per esempio `butler`, **pubblico**.
2. Carica questo `index.html` nella radice (tasto *Add file → Upload files*).
3. Settings → Pages → Source: **Deploy from a branch**, branch `main`, cartella `/ (root)`. Salva.
4. Dopo un minuto la pagina è su `https://TUONOME.github.io/butler/`.
   Aprila: deve dire "Manca il codice". È il comportamento giusto.

Se hai già un tuo sito, va bene uguale: basta che sia https.

## Poi, due incastri da fare bene

**Nel dashboard Spotify** (developer.spotify.com/dashboard → la tua app →
Settings → Redirect URIs) aggiungi l'indirizzo **identico**, barra finale
compresa:

```
https://TUONOME.github.io/butler/
```

**Su Butler**, dalla pagina di configurazione → Impostazioni → Pagina ponte,
incolla lo stesso indirizzo.

I due devono coincidere carattere per carattere, altrimenti Spotify rifiuta
con un errore sul redirect URI.

## Come si capisce che funziona

Tocchi "Accedi a Spotify", accetti, vedi mezzo secondo di "Un momento…" e
torni sulla pagina di Butler con scritto **Spotify collegato**.
