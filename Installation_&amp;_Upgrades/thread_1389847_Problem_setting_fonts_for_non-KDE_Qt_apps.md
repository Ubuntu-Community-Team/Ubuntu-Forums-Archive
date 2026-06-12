---
title: "Problem setting fonts for non-KDE Qt apps"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by QuantumCaffeine on 2010-01-24
Having been a GNOME user 'til now, I thought it was time to try KDE for a while. Things are going well so far, but I can't find a way to change the font non-KDE Qt apps (e.g. LyX) use. (They don't currently match the KDE-native ones.) qtconfig seemed like the place to go, but it's only willing to change the theme, not the font; it gives the following console error messages:

```
QPainter::begin: Cannot paint on a null pixmap
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::setPen: Painter not active
QPainter::setBrush: Painter not active
QPainter::setBrush: Painter not active
QPainter::setPen: Painter not active
QPainter::setPen: Painter not active
QPainter::setPen: Painter not active
QPainter::end: Painter not active, aborted
```

I also tried logging into XFCE and running qtconfig from there: it seemed to work, but the changes only apply outside of KDE. (So LyX now uses the right theme and font everywhere except in KDE.)

What am I doing wrong? (Is there a config file somewhere I can edit to get the job done?)

Cheers in advance,

QC

---

