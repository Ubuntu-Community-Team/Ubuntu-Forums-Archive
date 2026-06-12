---
title: "Installation hangs"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by pointfive on 2008-11-28
Hi. I'm attempting to install Hardy Heron (32bit) on an old Pentium 4 2.8GHz Dell with 256 MB RAM. The installation seems to hang after the linux kernel is loaded, showing the heron background. The CD drive is spinning & reading the whole time, and the mouse pointer is semi-responsive, but it never advances beyond this point. Thinking maybe the computer/drive was just slow, I let it run for 2 hours, but came back to a blank (no signal to monitor) screen.

I checked the disk (plus I've installed Ubuntu 6 times to other computers with this disk) and it's good... and I've tried 2 different CD drives in this computer. Same result. No feedback or progress bar; nothing to indicate where the process is hanging or failing.

Please help so I don't have to resort to installing XP on my girlfriend's parents' computer! Thanks!

---

### Post by Coreigh on 2008-11-28
Does the LiveCD work? Can you run the computer by booting from the CD?
 I can't really tell from your post but does it hang when you try to run the LiveCD before you start the install or are you installing right from the CD startup screen?

---

### Post by JockVSJock on 2008-11-28
I'm having the same time of issue too, upgrading from Ubuntu 7.04 to Ubuntu 8.04. 

When I try to install, I'm getting as far as the partition part and then it seems to freeze up my laptop (Avertech). 

I'll try to run the live disk again, however wanted to say I'm having the same issue too...

---

### Post by pointfive on 2008-11-28
> **Coreigh said:**
> Does the LiveCD work? Can you run the computer by booting from the CD?
 I can't really tell from your post but does it hang when you try to run the LiveCD before you start the install or are you installing right from the CD startup screen?

I tried booting from the CD as well and it hangs similarly. (Though again, this disk has worked on other machines.) So, neither works.

---

### Post by Coreigh on 2008-11-28
I have had similar experiences. Usually this is a problem relating to hardware. In my case one was ACPI (power management) on an older machine, not likely with your P4. The other was a video problem. I got around it by using VGA or a safe graphics mode. I am not familiar with the 8.10 release but previous releases had this as an option from the startup screen. Either right on the menu or in one of the F keys, F4 I think. The other thing is that 256MB is pretty thin for memory but I wouldn't think it was thin enough to prevent Ubuntu from running.

---

### Post by JockVSJock on 2008-11-30
Is there anyway to install the ISO from Ubuntu itself?  I currently have Ubuntu 7.04 on the laptop. 

When I mount the iso, I see a few executables like wubi and umenu and there is also an install directory too.  

Tried to search this forum and my query keeps timing out. 

thanks

---

### Post by pointfive on 2008-12-06
> **Coreigh said:**
> I got around it by using VGA or a safe graphics mode.
This did the trick for me... safe graphics mode. Thanks!

---

