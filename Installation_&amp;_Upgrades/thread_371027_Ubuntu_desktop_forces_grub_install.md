---
title: "Ubuntu desktop forces grub install"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by elints on 2007-02-26
I have several os's on my system including Kubuntu.  The Ubuntu desktop install insists upon installing Grub. I have tried to install grub everywhere except hd0 and have the installs fail on the Grub install.

Is there anyway to not install grub from the desktop install?

TIA

---

### Post by entropyfoe on 2007-02-28
I am looking into the same issue.
I have read that if you use the alternate install disk (text installer instead of graphical installer), you are offered the option of no grub installation.

I already have grub installed (for Mepis and XP) and dont want to mess it up with the less visually appealing grub screen.

I have downloaded the alternate install iso, and will experiment with it.
-Jay

It worked, though the alternate install was a bit opaque, ( I winged it with no documentation or homework), I was able to install Edgy with no Grub.  I went in and edited menu.lst and after 2 attempts, I finally got it exactly right, and it boots - no messing up Grub and the XP installation etc.

---

