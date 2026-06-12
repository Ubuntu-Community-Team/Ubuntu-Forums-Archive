---
title: "Is GRUB Necessery?"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by robcarr2 on 2006-05-09
Is there absolotly no way to load ubuntu without grub? as when I try to install grub i get errors with grub, but whenever I install ubuntu and try to load ubuntu it says there was an error loading the operating system while im still on the black screen.

I am installaing to an external hard drive that is plugged into my usb port, could this have anything to do with the errors?

I have tried installing from an official ubuntu cd and the downloaded iso but not having much luck

---

### Post by RavenOfOdin on 2006-05-09
Maybe this can help:

[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

---

### Post by az on 2006-05-09
[QUOTE=robcarr2]

I am installaing to an external hard drive that is plugged into my usb port, could this have anything to do with the errors?
[/QUOTE]
Yes.  Grub does not use the linux kernel, but what the bios can tell it about your devices.  If your bios cannot see the usb drive, then grub cannot see it either.

---

### Post by robcarr2 on 2006-05-09
[QUOTE=RavenOfOdin]Maybe this can help:

[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)[/QUOTE]

Thanks for that, I believe that is what I need to do, I am having problems with it at the moment on step 4 were your on the repair console, I have tried choosing each part1 of each disc and it always says there is no record or something like that, and wont let me mount anything because there is no such file or directory.

Not to sure what the problem is but atleast I am a bit further in the right direction now, if anyone has any suggestions as to why this isnt working please put them forward :)

---

