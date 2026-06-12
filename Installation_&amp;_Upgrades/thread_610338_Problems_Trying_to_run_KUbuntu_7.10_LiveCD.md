---
title: "Problems Trying to run K/Ubuntu 7.10 LiveCD"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Kasa.Ramone on 2007-11-11
*First of all excuse me if my english isn't the best, i'm Argentinian.*

Well yesterday I got my CD's of K/Ubuntu from Canonical and everything was okey.
I put the CD of Ubuntu on my DVD-RW Drive and wait for my computer to boot from it. It show me a splash screen to pick up the language,vga,etc.
I configured it to "español" language, and selected the option "Start or install Ubuntu". It began to load.. The ubuntu logo and the orange progress bar appeared, but when it finished loading a "weird screen" appeared, It was like a lot of Multi-colors lines, i waited for a minute and reset.
Tried again but this time setting the resolution with Vga=792, got same results and the same for vga=791.
Tried adding "noapic nolapic", but same thing happened.
Even tried on Safe mode , but nothing..
The Cd can't be corrupted they are from canonical , and i tried with the 2 ubuntu Cd's and the 2 Kubuntu Cd's. (both x86)
The Dvd-Rw Drive works fine, and my ram isn't buggy.
I let you the description of my pc:
Processor: Intel pentium 4 HT 3.0ghz
Ram:512 DDR PC3200
HDD: Samsung 160Gb SATA-II (I heard about problems with Sata, but it's a live cd and I'm Not installing it yet)
Onboard Video Card : Intel Graphics Controller 82865G 96mb & Intel Graphics Extreme 2 16mb
Monitor: Samsung SyncMaster 794v 17'

I'm Running winXP on it, but i want to get on the linux world (Free/libre and Open Software are great for me because i'm trying to get in the world of programming) and ubuntu sounds fine for me.
It's not an option formating or resizing partitions because it's the Computer of my whole family.
So while i'm trying to get some cash to buy another Hard Disk Drive to put ubuntu on it  i would like to test it on the LiveCD, so Alternate install for now it's not an option either.

Hope you can help me.

P.D: I tried also to get with the Hotkeys in the console , to change the resolution, but nothing happens.

---

### Post by gupta_sumesh63 on 2007-11-13
Try this. Hope it helps.
While booting open the Bios menu by pressing delete.
Change all the settings in Bios to default.
Ensure that your first booting device is your DVD-ROM.
Save and exit.
Put your Ubuntu Live CD in the first booting device(as shown in your Bios setting (if you have seperate CD and DVD ROMS))and Reboot.
Installation went flawlessly after I did this.
Hope it corrects your problem too.
Its a Hardware communication bug in Gutsy I think.
I could resolve it by going through the above procedures.

---

