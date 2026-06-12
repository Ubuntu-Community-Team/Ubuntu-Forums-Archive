---
title: "Reinstall Gutsy to XP dual boot?"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by isomeme on 2007-11-22
I'm installed Gutsy as a dual-boot next to XP on my home system recently.  All went well.  Yesterday, something went badly wrong during a set of software installs and upgrades on Ubuntu, and now when I start Ubuntu, I end up with a screen full of noise, and a partially visible text box warning about "low video mode" in the lower right.  Booting recovery mode doesn't change this.

Given that I fumbled around a bit in my initial days with Ubuntu, I'm thinking it might make sense to reinstall it.  I still have the ISO installer CD, of course.  But I'm not sure it's safe, or the right course of action, to just boot that again.  I don't know if it's "smart" enough to recognize that the disk is already partitioned, grub already installed on the boot sector, and so forth.  I worry about it trashing things, or just not overlaying the existing Ubuntu installation correctly.

Does anyone have advice on how I should proceed?

---

### Post by kellemes on 2007-11-22
Just boot the disk and from the installer (partition-editor) you get a fine view on your partition-scheme..
From here you can decide if you want to delete the (ubuntu)partitions and start over or simply use the excisting partition-scheme.
Grub (the bootloader) will simply install itself where it used to be without issues, well normally speaking that is.
Anyway, it's safe to run the livecd.. it won't touch your system.

In general it's always safe to create backups of the most important data when (re)installing OS's so you've been warned.. :popcorn:

---

### Post by isomeme on 2007-11-22
Yeah, don't worry, I'm quite sufficiently scared already. :P  Thanks for the info.  Anybody else who has words of wisdom, I'd love to hear them; I probably won't be trying this until tomorrow, since today is Eat Until You Explode Day here in the USA.

---

### Post by kellemes on 2007-11-23
> **isomeme said:**
> Yeah, don't worry, I'm quite sufficiently scared already. :P  Thanks for the info.  Anybody else who has words of wisdom, I'd love to hear them; I probably won't be trying this until tomorrow, since today is Eat Until You Explode Day here in the USA.

Well, I'm from Holland, so nothing to celebrate here..  :popcorn:
Hope you didn't explode.

---

### Post by seasom on 2007-11-23
when i installed ubuntu for the first time like 2 days ago i put it on a 5 gig partition.  it inevitably got messed up to the point where i couldnt fix it, so i just deleted the partition & reinstalled and it worked fine.

i'm not sure whether your dual booting situation is the same.

incidentally, when i deleted the partition i put ubuntu on, the computer was no longer able to boot up into windows even (it kept trying to load something called grub), but after reinstalling ubuntu i was able to boot into windows again just fine.

not sure if any of that helps

---

