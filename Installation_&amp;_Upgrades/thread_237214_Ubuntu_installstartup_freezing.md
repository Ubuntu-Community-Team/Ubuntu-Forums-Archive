---
title: "Ubuntu install/startup freezing"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by hAvAAck on 2006-08-15
I've tried to install Ubuntu 10 times now but it seems to freeze in the same place each time.
Twice I've gotten 
**Kernel panic - not syncing: Attempted to kill Init**
Once I've gotten
**Udevd[4675] exited with preempt_count 1**
I also managed to get a 
**Kernel Panic - not syncing: Fatal exception in interrupt**
and other times it just froze in the same place without an error message. 
I get to the point where it is loading hardware drivers
The number before any of these messages is [17179675.152000] if that means anything :???: 

I have a Dell Dimension Desktop 2350
Pentium 4 2.2 Ghz
1024 RAM
With 2 HDs and a total of 3 paritions (ignoring Dell's little 31MB partitions on each)

Any suggestions on what I should do? I searched for "Kernel Panic" and saw a thread where people were using BIOS to disable some USB support but I'm not sure how I should approach this.
Thanks for your time!
hAvAAck

---

### Post by hAvAAck on 2006-08-16
Update, I MD5summed the CD and there were no errors :(

---

### Post by LeMeun on 2006-08-16
can't say it'll help but i got some issue w kernel panic while starting Ubuntu live-cd on my laptop. Here is what i did:

on the splash screen press F6 and to the boot options just after "ramdisk_size" add "acpi=off" leave the rest of the boot option intact.

It works for me, hope it could help!

Try also framebuffer=false if it doesn't work with the acpi

If it's for install only use the alternate version sometime it solves all the troubles.

LeMeun;)

---

### Post by hAvAAck on 2006-08-16
Thanks for the advice, but it's still a no go :(
I got one more Kernel Panic and a
**<6> agpgart: AGP aperture is 128M at 0xd0000000**

Right after it says "loading hardware drivers" it looks like a line says something to the effect of "RNG not detected" but I might be mistaken, however I cannot scroll up to see what it actually says.
I'm stuck :(

I read on the pages [https://wiki.ubuntu.com/CommonProblemsInstall](https://wiki.ubuntu.com/CommonProblemsInstall) and [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) and I nothing struck me as something I should do to try to get this to work. I mean, my answer may be in there and I didn't recognize it because I'm such a newbie, but it just didn't pop out at me. I'm wondering if my hardware just isn't compatable?

---

### Post by hAvAAck on 2006-08-16
Ah sorry for double posting, but update. I got the LIVE cd to boot but I didn't install because I'm confused about something. I have my onboard video card disabled because I use a PCI slot card. I was wondering if this would cause problems, and apparently it does. When I re-enabled the onboard video controller in BIOS Ubuntu booted all the way up so that I was in its console with icons on the screen and everything.

What will Ubuntu do when I install if I have to run off of the onboard video card in order for me to see installation, but I really just want to use the PCI slot card during normal operation?
Thanks for all the help

edit: There might be a little more background in [this](http://www.ubuntuforums.org/showthread.php?t=237141) thread about my video card ridiculousness. I'm sorry if I'm coming off as frantic, I'm really not :D

---

