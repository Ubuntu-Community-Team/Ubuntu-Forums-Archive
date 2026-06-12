---
title: "KDE 4.2 drop shadow glitch"
date: 2009-02-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by inportb on 2009-02-19
I've been seeing this effect after upgrading to KDE 4.2, and I've heard that it may be due to some bugs in the xserver-xorg-video-radeon driver. This does not occur in Enlightenment using Bling or Ecomorph. I have not tried Gnome/Compiz/Metacity, but guess that since Ecomorph works fine Compiz should too.

I'm using the AMD/ATI RS690M (Radeon X1250) chipset and the latest radeon update (1:6.11.0-1ubuntu1) hasn't fixed the issue... so I'm going to ask around. Has anyone else seen this issue, is there a launchpad entry, and does a workaround exist?

Anyway, I have drop shadows disabled atm because they look ugly.

---

### Post by Sand &amp; Mercury on 2009-02-19
Hm, that's a new one. Works fine for me, though I'm using the open source driver.

---

### Post by inportb on 2009-02-19
That's interesting. So this might be a KDE bug or it might just be that our hardware are different?

---

### Post by inportb on 2009-02-22
Hm. Well, I suppose I'll be opening a bug report for this. What package should this be filed against?

---

### Post by Sand &amp; Mercury on 2009-02-22
> **inportb said:**
> Hm. Well, I suppose I'll be opening a bug report for this. What package should this be filed against?
Perhaps KWin?

I actually got some corruption today myself. It was while I was playing Gens, in OpenGL mode... but it was different to yours, the entire drop shadow started playing up. But disabling compositing (Alt+Shift+F12) and enabling it again fixed them.

---

### Post by inportb on 2009-02-22
Well... here goes: [lpbug]333106[/lpbug] :)

---

### Post by vishalrao on 2009-02-22
i see a black border around the desktop folder widget since updating post-feature-freeze this weekend. im guessing (from reading kde dev blogs) its because they've uploaded qt 4.5 rc1 when kde 4.2 was coded to work around qt 4.4 bugs so we'll see glitches when 4.5 is in there. edit: but it looks like they might be patching away to work around the issues...

---

### Post by inportb on 2009-02-23
Well, this drop shadow madness has been around for a month or so. We'll see :p

---

### Post by emerson999 on 2009-02-23
The qt change might explain why I received a massive slowdown on upgrading after not doing so the past couple weeks. The kwin effects work, but they're 'really' laggy now. Where, before, I was often pretty impressed by how much faster kde 4.2 felt than previous versions I'd tried.

Anyone know which graphic system backend they compiled qt with?

---

