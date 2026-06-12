---
title: "installing after windows 7"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2009-12-18
Have just changed from XP to Windows 7 and decided to reinstall Ubuntu 9.10 (64bit) as a dual boot.  Popped the CD containing the iso and selected install --- after awhile, got all kinda errors streaming across the screen.  Guess the CD could have gone bad but it is the same one I've used previously to install a dual boot with XP.  

Anything special about installing after Windows 7?

---

### Post by phillw on 2009-12-18
Hi,
Chances are, Win7 has used all of your disk area & you're going to have to use the Win7 partition manager to free up some space for your Ubuntu Area.

If you boot off the liveCD, drop to terminal and type

```
sudo fdisk -l
```

That'll tell you if you have any linux area(s) left.

If, as I suspect, you haven't - then just make some room - no need to allocate it, from within Win. Make sure Win boots happily. Then do the install from the LiveCD telling it to use the free space to install upon.

Phill

---

### Post by darkod on 2009-12-18
> **deeppow said:**
> Have just changed from XP to Windows 7 and decided to reinstall Ubuntu 9.10 (64bit) as a dual boot.  Popped the CD containing the iso and selected install --- after awhile, got all kinda errors streaming across the screen.  Guess the CD could have gone bad but it is the same one I've used previously to install a dual boot with XP.  

Anything special about installing after Windows 7?

Nothing really. I just started using ubuntu with the 9.10 version, never even installed it before, and it worked right away dual booting with win7 on both my netbook and desktop.
You might be right the cd going bad even if it's the same one. How about the cd drive going bad?

---

### Post by OrangeCrate on 2009-12-18
> **deeppow said:**
> Have just changed from XP to Windows 7 and decided to reinstall Ubuntu 9.10 (64bit) as a dual boot.  Popped the CD containing the iso and selected install --- after awhile, got all kinda errors streaming across the screen.  Guess the CD could have gone bad but it is the same one I've used previously to install a dual boot with XP.  

**Anything special about installing after Windows 7**?

Use these instructions, and you should be fine...

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by deeppow on 2009-12-18
A lot of free space available.

I'll remake the CD and see if that'll solve the problem.

---

### Post by phillw on 2009-12-18
> **deeppow said:**
> A lot of free space available.

I'll remake the CD and see if that'll solve the problem.

Free, as in unallocated - or free as in unused ? 
There is a small but very important difference between them.

Phill.

---

### Post by avtolle on 2009-12-18
> **phillw said:**
> Free, as in unallocated - or free as in unused ? 
There is a small but very important difference between them.

Phill.
+1

Also, it occurs to me to ask where the free space exists; within the Windows7 partition or outside it?

---

### Post by deeppow on 2009-12-18
unallocated  197 GB

---

### Post by deeppow on 2009-12-18
Looks like a bad CD.  Thanks for your replies and sorry for the inconvenience.

---

