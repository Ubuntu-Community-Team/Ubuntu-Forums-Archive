---
title: "Annoying error each bootup"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by plethorex on 2008-03-21
Alright, I just installed the x64 version of 8.04 using Wubi.  I installed on a second hard drive, which is completely it's own entity from my main, Windows drive.  After installing Ubuntu (which works flawlessly for the first time!) I was greeted by an error at the grub menu.  Each time I boot to Ubuntu I have to manually change the command line to read hd(1,0) as it always reverts back to hd(0,0) (which is my Windows HD) when I boot.

It's an inconvenience at best, but it is still an issue.  Any fix for this?

---

### Post by wolfen69 on 2008-03-21
see this [http://ubuntuforums.org/showthread.php?t=726488&highlight=grub+order](http://ubuntuforums.org/showthread.php?t=726488&highlight=grub+order) this is for making xp the default, so just do the opposite.

btw, if you have a second hard drive, why did you use wubi to install ubuntu? during a regular install, just point ubuntu to install on the second drive and you're all set, with ubuntu being the default startup OS in grub.

---

### Post by pieisgood4589 on 2008-03-21
> **wolfen69 said:**
> see this [http://ubuntuforums.org/showthread.php?t=726488&highlight=grub+order](http://ubuntuforums.org/showthread.php?t=726488&highlight=grub+order) this is for making xp the default, so just do the opposite.

btw, if you have a second hard drive, why did you use wubi to install ubuntu? during a regular install, just point ubuntu to install on the second drive and you're all set, with ubuntu being the default startup OS in grub.

Heh, good suggestion. Keep in mind that Wubi is still in beta stages, so there are bound to be bugs.

---

### Post by plethorex on 2008-03-21
> **wolfen69 said:**
> btw, if you have a second hard drive, why did you use wubi to install ubuntu? during a regular install, just point ubuntu to install on the second drive and you're all set, with ubuntu being the default startup OS in grub.

Each time I've tried to install Ubuntu via CD it's been a complete disaster.  For 7.10, I was couldn't even get past the beginning installation menu without it crashing to a black screen.  The error was that my video card wasn't supported, and through a million work-arounds I could it up and running.  The Wubi installation was the first tool I used that actually worked, so I've stuck with it.  Maybe I'll burn up a new disc...

---

### Post by wolfen69 on 2008-03-21
you could always try Hardy Heron when it comes out next month.

---

