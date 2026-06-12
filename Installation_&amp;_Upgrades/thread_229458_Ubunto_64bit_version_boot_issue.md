---
title: "Ubunto 64bit version boot issue"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by Nicoleise on 2006-08-04
Hi everyone. 

I'll make it nice and short:

Trying to run Ubunto to check it out, via the Live CD downloaded and burned. 

When I hit "Start or Install" it boots the kernel, and  then comes up with the following :

```

[40.364140] CR2 : 00000000e0100000
[40.364178] <0> Kernel Panic - not syncing : Attempted to kill init!
[40.364258]

```

And that's as far as it goes. 

I'm running a Pentium 4 HT cpu, 3.2 GHz @ 3.6 GHz. When I boot the system it - amongst other stuff - says "EM64T enabled processor detected". And downloading the AMD64 bit version, it because at the file description it says that the AMD64 bit version is for EM64T Xeons too. My cpu isn't a Xeon, but I figured the important thing was the 64 bit. Am I wrong about using this file?

It's possible that the fix lies it a boot parametre? In that case, which parametres should I attempt to use ?

System Specs :

[LIST]
[*]Intel Pentium4 HT EM64T Processor 3.6 GHz
[*]Intel 925X/XE Chipset
[*]Nvidia Geforce 6600GT 128 MB
[*]2560 MB DDR2 RAM, dual channel-symmetric
[*]2 x Western Digital 160 GB Harddrives, Raid mirrored. 
[*]All partions NTFS formattet.
[/LIST]

Any help would be greatly appreciated.  

Thanks, 
Nicoleise

---

### Post by Scwounch on 2006-08-22
I have the **exact** same problem.  I'm not sure about the specifics of what comes before the "<0>Kernel panic - not syncing: Attempted to kill init!" but the rest looks mostly unimportant.  I'm also using the AMD64 version, but on an Athlon64 3400+ processor.  Incidentally, I have the same video card as you do, Nicoleise.
I just want to try out the live boot thingy, so I can decide if I want to make the permanent switch, but even when I try verifying the CD, it gives me that kernel panic message.

---

### Post by Scwounch on 2006-08-25
Update:  I got it to work... sort of.  I pressed F6 at the Ubuntu menu you get when you boot from the CD.  I then added acpi=off to the argument string and pressed enter.  It took a while, but eventually started up Ubuntu.  Unfortunately, my USB mouse didn't work, so I couldn't do anything.  CTRL+ALT+BKSP logged me out and brought me to a login prompt.  I'd be golden now if I could just figure out how to get it to recognize my mouse (it's actually a Wacom tablet).

---

