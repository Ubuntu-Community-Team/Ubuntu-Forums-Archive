---
title: "Terminal Transparency?"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nixie Pixel on 2009-02-12
Hi there...silly question, but I seem to recall that setting transparency in the profile preferences for my terminal in earlier versions of Ubuntu allowed me to see applications and other items under the terminal window.  In Jaunty all I see is the desktop background.  I can't find any info about how to change this, can someone point me in the right direction?

Thanks!

---

### Post by Gourgi on 2009-02-12
edit-> profile prefs -> Background -> transparent

---

### Post by Nixie Pixel on 2009-02-12
Thanks, but what I mean is when I do that now all I see is the wallpaper from my desktop.  When I did it in older versions of Ubuntu I could see through to applications like Firefox, in case I wanted to read something while typing in the terminal.

---

### Post by cariboo on 2009-02-12
You need to have compiz running to have transparent terminals.

Jim

---

### Post by tawmas on 2009-02-13
> **cariboo907 said:**
> You need to have compiz running to have transparent terminals.

Jim

Or you can enable compositing in metacity if you don't like to have compiz on... You need to edit the gconf key composiing_manager under apps > metacity > general to do that.

---

### Post by blazemore on 2009-02-13
You need some kind of compositing to enable "true" transparency.

Otherwise it takes a shot of the desktop underneath, and sets that as the background (it's not very elegant)

---

