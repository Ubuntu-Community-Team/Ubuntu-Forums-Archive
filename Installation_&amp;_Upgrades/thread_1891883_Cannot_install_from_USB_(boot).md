---
title: "Cannot install from USB (boot)"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by iondoarion on 2011-12-06
Hi,

I'm trying to install Ubuntu 11.04 (64bit) from my USB memory stick and I can't manage to make it bootable.

**Current OS:** Win 7 Ultimate (64);
**ISO image** from [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/) -> ubuntu-11.04-desktop-i386.iso (intel cpu);

I've tried with usb-creator and with Universal-USB-Installer without any success.

I selected in BIOS the first bootable device (as I should) to be the USB, but it won't work.](*,)

[COLOR="Blue"]Boot -> UEFI (enabled) -> Boot option #1 [UEFI: Corsair...]; Boot option #2 [P1: SlimtypeDVD...]; Boot option #3 [P0: WDC...][/COLOR]


**Can you please give me an advice?**

TYVM

---

### Post by zvacet on 2011-12-10
See if [this]("http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid") is of any help to you.

---

### Post by iondoarion on 2011-12-10
> **zvacet said:**
> See if [this]("http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid") is of any help to you.

HI,

Thank you for the answer. 

At that time I couldn't burn any CDs. In the end I managed to burn some CDs and got back to 11.04. I don't know why when I've installed (or at least tryed) 11.10 everytime I got a different error :)) SO finally I gave it up (I am beginner and for learning, I think that 11.04 is the perfect choice).

I cannot try that now, so unfortunately I cannot write a feedback for someone that would have the same problem.

TYVM! ;)


Take care!

---

### Post by zvacet on 2011-12-10
You can upgrade from 11.04 to 11.10 if you want to.

---

### Post by critin on 2011-12-11
You might try reformatting the flash and installing the iso again.  Sometimes something just doesn't stick the first time.  (It's happened to me.)

---

### Post by james2b on 2011-12-11
Did you format FAT32 on your USB flash drive and follow all the instructions carfully? See this; [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) Also some older system BIOS need to have legacy USB enabled first, and boot device order to include "Removable". When I created mine at the end of the process was a script or batch file was run to make the USB flash drive boot capable.

---

### Post by iondoarion on 2011-12-11
> **james2b said:**
> Did you format FAT32 on your USB flash drive and follow all the instructions carfully? See this; [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) Also some older system BIOS need to have legacy USB enabled first, and boot device order to include "Removable". When I created mine at the end of the process was a script or batch file was run to make the USB flash drive boot capable.

I could have done something wrong but belive me I've done it so maaany times lately that I even dream it (that really happened).

TY for the link and the suggestion, I'll keep that in mind next time I'll install it.

> **critin said:**
> You might try reformatting the flash and installing the iso again.  Sometimes something just doesn't stick the first time.  (It's happened to me.)

I've done that sooo many times :) but it didn't seem to work. Next time  when I'll re-install I'll put my ambition to work and shall not give up  until I have installed Ubuntu from the flash :grin:

---

### Post by iondoarion on 2011-12-11
> **zvacet said:**
> You can upgrade from 11.04 to 11.10 if you want to.

I've read some posts (and there were quite a few) that it is a problematic task to be done. It's obvious that there are more people complaining than people praising (because they are more motivated to do so - for solving an issue or just being frustrated)  but since I am at the beginning I think I'll just wait a bit until I have learned more before going forward with the update. For the moment I had enough reinstalls and I need a time of stability :lol:

---

### Post by arkster on 2011-12-11
You need to use a different formatting utility to format the usb key to fat32. I suffered from the same thing until someone suggested to use the 'hp usb disk storage format tool'. Do a search online and use that and then use the startup disk creator or unetbootin.

---

