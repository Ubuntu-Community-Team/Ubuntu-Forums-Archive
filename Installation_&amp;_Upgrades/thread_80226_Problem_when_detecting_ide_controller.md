---
title: "Problem when detecting ide controller"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by Theman711 on 2005-10-21
Hi I've just recently tried to install Kubuntu 5.10 on my desktop and I just reformatted yesterday. I have already made a separate partition for Kubuntu. When it's detecting during install it always freezes around 83% when its loading module for ide drive linux ata disk. I installed this on a friends machine and had no problems, it only stayed at 83% on theirs for a few seconds so I know its just this computer. Does anyone know how to solve this issue?

Config - Intel celeron 1.7ghz
- ATA hard disc

---

### Post by misGnomer on 2005-10-25
Have you tried starting the installation using any of the boot time kernel arguments which can be used to get around BIOS bugs or IRQ conflicts and such?

When the install CD loads, hit F1 (and F2 etc.) to read more about these boot time arguments. Commonly used ones include "noapic", "acpi=off", "pci=biosirq" and "irqpoll".

Many of the generic kernel parameters used by Knoppix also apply to Ubuntu:

[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://download.linuxtag.org/knoppix/knoppix-cheatcodes.txt](http://download.linuxtag.org/knoppix/knoppix-cheatcodes.txt)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

You could also try using the expert install mode which allows you to select specific IDE driver.

You could try disabling DMA (either in BIOS or through boot parameter; "ide=nodma"?)

You could try hooking your CD-ROM to another IDE channel (if both CD and HD are on the same one currently).

If none of that helps, you should give more details about your setup, like the model of the IDE controller, and tell what the "dmesg" command tells is happening behind the scenes when the conflict happens (if you manage to switch to console mode before of after the freeze).

Good luck!

---

### Post by personman on 2005-11-18
I'm having the same problem.  The install freezes while trying to recognize the hardware.  It's at 83% every time and it says it's looking for IDE controllers.  Did anyone find a solution for this?

---

### Post by gsus777 on 2005-11-20
I had the same issue and solved it by using "expert" mode and when getting prompted for hdparm entering "-d 1 /dev/hda1". This turns DMA on. In some dvd drives this is required to work with the linux driver. Benq and Plextor are affected, others I don't know.

---

### Post by floobit on 2006-02-21
I have a benq, and had a similar issue.  my install froze on 'ide-cd' for 'Linux ATAPI CD-ROM' (86%).  After hearing about the dma issue, I used the following boot option as detailed by another thread that I can't find now.  apparently, it's the same as hdparm -d1 /dev/hda:

cdrom-detect/cdrom_hdparm=-d1

I chose this option because when installing in expert mode, I was not asked for any "hdparm" arguments, only arguments for each driver module it wanted to load.  after typing hdparm -d1 /dev/hda at every module prompt that looked related to ide or cd-rom, it didn't accept my arguments (red square saying "not valid arguments").  

however, the boot option did not fix the freezing.  any ideas?

AMD64, 160 Seagate SATA, Benq 1620 with latest firmware update. ATI x200, weird ATI chipset, uhhhh...XC cube (aopen)

---

### Post by saschaz on 2006-02-23
I had the same problem with my ACER Travelmate 529 TXV.

Look in this thread for my solution:

[http://ubuntuforums.org/showthread.php?t=128987](http://ubuntuforums.org/showthread.php?t=128987)

---

### Post by floobit on 2006-02-25
hm.  that didn't work.  any other ideas?

---

