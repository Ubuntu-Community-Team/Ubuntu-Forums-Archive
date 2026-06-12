---
title: "Grub error 18 with XP &amp; ubuntu dual boot"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by Kasten on 2008-06-13
First let me start off my telling you how I installed everything.  I installed xp pro on a 60GB HDD and made an NTFS 38GB in size and installed windows there.  After I got xp going I installed ubuntu 8.04 made a swap partition 1024MB in size then an ext3 for the rest of the space on the HDD. Installed fine and booted back in ubuntu and install all the newest updates. Rebooted again and went into ubuntu again. I rebooted again and picked xp from the grub memu and it booted fine. All seemed well. I turned the pc off and then back on and then it came to the screen on booting

GRUB loading stage1.5.

GRUB loading, please wait...
Error 18

Becuase this is an older pc I thought the hardware maybe bad but it passed a full memory test, advanced DFT HDD scan, and the mobo capacitors looked good too. So I googled the problem because it must be software. I found that a BIOS update can sometimes fix this. Tried that but no go. A lot of posts were also saying changing your HDD settings in the bios to LBA worked but this dell bios does not have this option. It has AUTO, some really small setting that show the capacity from 21MB to 200MB and USER settings for entering the cylinders, heads, and sectors in manualy but not an LBA option.

Ok so I booted the ubuntu 8.04 live CD to reinstalled grub did it by running these commands from the terminal.

sudo grub
root (hd0,2)
setup (hd0)
quit
exit

I rebooted and I was able to get into windows xp and ubuntu again. Ok so here is the weird thing. It boot just fine along as I just reboot. If I cold boot the pc it just gets the error 18 again. Just to make sure something didn't just go wrong I reinstall grub again and I didn't matter what OS I shut down in it gets the error 18 when I cold boot the pc.

Any ideas? I was thinking it has to doing something with the mobo. Its an older pc but the specs are not to bad for an extra pc. 1.4GHZ P4, 512MB of RamBus memory, 64MB nvidia card. Is there anther boot loader I can try? I'm a Linux newbie so I need something that is step by step. Tank you.

---

### Post by dstew on 2008-06-13
If it only happens with a cold boot, it might be that some setting of BIOS or the disk is not being retained when the power is off. Is maybe your CMOS battery dying? It doesn't sound like the classical error 18 that is caused by the BIOS cylinder limit, since a warm reboot works OK.

You can try the Lilo boot loader as an alternative to grub.

---

