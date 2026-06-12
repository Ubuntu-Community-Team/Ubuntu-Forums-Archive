---
title: "after Gutsy -&gt; Hardy upgrade, OpenOffice writer doesn't show handles on images"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by jejones3141 on 2008-05-05
I've upgraded my wife's computer (an AMD Athlon 64) from Gutsy Gibbon to Hardy Heron. Today she fired up Open Office to create some documents with images, which she has done in the past with no trouble. Now, inserted images don't display the green squares that let one adjust image size.

My computer, also an Athlon 64, which has Hardy Heron freshly installed, does not have this trouble; inserted images show up with their handles visible. I therefore place this message under Installation & Upgrades. Is there a known fix for this problem (and, of course, if it exists, what is it)?

---

### Post by jejones3141 on 2008-05-11
OK... I tried logging on to my wife's computer as me, and running OpenOffice. An inserted image had its little green handles as expected.

Therefore, it's something about the user-specific configuration, right? So I looked at her home directory and renamed .openoffice and .openoffice.org2 so OpenOffice wouldn't see them and would presumably create whatever the initial default .openoffice.org2 is for her.

Fired up OpenOffice writer, and inserted an image: no green handle boxes.

Is there some other per-user configuration that I'm overlooking?

---

### Post by jejones3141 on 2008-05-17
There is another configuration file I'm missing, but it's not where I was looking. 

The thread on Human Icons for OpenOffice shows someone with exactly the same symptoms caused by that icon set.

I experimented, and having my wife log in with GNOME rather than KDE did the trick; therefore, it's something about the KDE configuration that's the problem.

The immediate pressure is off, because she can once again resize images under OpenOffice, and I can track down the setting that does the trick more at my leisure, and post here when I find it. Somehow she is getting a broken set of icons, perhaps an old one that's since been fixed, when she logs in under KDE.

---

