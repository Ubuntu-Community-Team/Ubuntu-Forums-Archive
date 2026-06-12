---
title: "restore to older vim colors"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by skewray on 2012-11-21
I just upgraded from Karmic to Natty (on my way up).  The new default color scheme for context highlighting used in vim just doesn't work for me against a black background.  For example, comments are too dark to see.  Does anyone know what the name of the default color scheme was under Karmic?  And the line in the .vimrc to set it?

---

### Post by drmrgd on 2012-11-21
> **skewray said:**
> I just upgraded from Karmic to Natty (on my way up).  The new default color scheme for context highlighting used in vim just doesn't work for me against a black background.  For example, comments are too dark to see.  Does anyone know what the name of the default color scheme was under Karmic?  And the line in the .vimrc to set it?

I don't know the default color scheme.  But, as a temp workaround, you can add this to your .vimrc to compensate for the darkbackground:

```
set background=dark
```

That, while still ugly in my opinion, will help with the dark blue colors for comments and such.  I grabbed a pack of color schemes a while ago and have settled on 'molokai' recently as a fairly nice color scheme for bash, R, and perl scripting.

---

### Post by skewray on 2012-11-22
"set background=dark" does fix the problem.  Thank you.  I suspect that under KDE, vim somehow knew the background color, but under LXDE vim doesn't get the information.  I switched after the upgrade when KDE would not allow two terminal windows to both have menu bars.

---

