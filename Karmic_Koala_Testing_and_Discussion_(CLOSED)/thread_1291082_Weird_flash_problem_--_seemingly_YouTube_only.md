---
title: "Weird flash problem -- seemingly YouTube only"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Cuddles McKitten on 2009-10-14
I've got a 64 bit system and had flash working pretty well in Jaunty.  In Karmic it seems to work fine except for YouTube videos.  For some reason, it takes about thirty clicks to get them to actually play and then I don't have the ability to pause or move the position slider.  Does anyone know why my flash seems to be biased against only one website?

---

### Post by durand on 2009-10-14
I seem to have the same problem when I'm using Opera but not with Midori or Firefox.

---

### Post by Saneless on 2009-10-14
It's not just youtube.

Uninstall the flash plugin package, go to adobe's site, download the "alpha" 64 bit plugin, and put it in the /usr/lib directories of each browser you're trying to use.  I think it's something like /usr/lib/mozilla/plugins for Firefox, but this is off the top of my head.. it makes sense once you're in there.

If the file already exists, overwrite it.

---

### Post by zika on 2009-10-14
> **Saneless said:**
> It's not just youtube.

Uninstall the flash plugin package, go to adobe's site, download the "alpha" 64 bit plugin, and put it in the /usr/lib directories of each browser you're trying to use.  I think it's something like /usr/lib/mozilla/plugins for Firefox, but this is off the top of my head.. it makes sense once you're in there.

If the file already exists, overwrite it.Hate to repeat myself but ---> +1 Put it in ~/.mozilla/plugins where it belongs and put it with Your permissions not with sudo. Create plugins directory if it doesn't exist. That is the proper place for user-installed plugins.

---

### Post by NRDNick on 2009-10-14
edit: oops nevermind, disreguard

---

### Post by Cuddles McKitten on 2009-10-14
> **Saneless said:**
> It's not just youtube.

Uninstall the flash plugin package, go to adobe's site, download the "alpha" 64 bit plugin, and put it in the /usr/lib directories of each browser you're trying to use.  I think it's something like /usr/lib/mozilla/plugins for Firefox, but this is off the top of my head.. it makes sense once you're in there.

If the file already exists, overwrite it.

That makes the videos work, but Firefox crashes fairly often.  I guess I'll just live with the ersatz flash in the repos.

---

