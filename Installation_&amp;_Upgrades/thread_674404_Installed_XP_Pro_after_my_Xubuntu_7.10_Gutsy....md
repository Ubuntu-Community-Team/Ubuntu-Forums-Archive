---
title: "Installed XP Pro after my Xubuntu 7.10 Gutsy..."
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by taikuodo on 2008-01-21
Hi, I had Xubuntu 7.10 on my laptop. Now I installed XP Pro on the remaining partition.

Now when it starts up, it no longer says grub starting up, it just skips to windows XP Pro, leaving me with no dual boot screen.

Whats up with that?

Thanks for any help in advance.

---

### Post by PurposeOfReason on 2008-01-21
Installing XP overrode your MBR and took grub with it. You'll need to read this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by taikuodo on 2008-01-21
I installed Xubuntu from a USB Flash drive (alternate iso).

Should I just reinstall Xubuntu (would that fix the problem?) Or is there a way to reinstall grub without a LIVE cd?

---

### Post by PurposeOfReason on 2008-01-21
> **taikuodo said:**
> I installed Xubuntu from a USB Flash drive (alternate iso).

Should I just reinstall Xubuntu (would that fix the problem?) Or is there a way to reinstall grub without a LIVE cd?
If the flash drive also installed grub then that would fix the problem, but you would overwrite your old installation or you can do a grub install on a flash drive:
[http://www.freesoftwaremagazine.com/articles/grub_intro/](http://www.freesoftwaremagazine.com/articles/grub_intro/)

---

### Post by Craigus on 2008-01-21
Get the supergrub disk:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

