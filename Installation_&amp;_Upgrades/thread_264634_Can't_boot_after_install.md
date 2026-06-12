---
title: "Can't boot after install"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by ryanst on 2006-09-24
Hi all,

Here are the basics:  
Using the Dapper Alternate install CD
P4 2.6GHz, 512 MB Ram
80GB HD, formatted ext3 with a part left for swap, no windows
two 200GB drives set up as software raid1 through the installer
Nvidia 128 MB graphics card
Hauppage WinTV PVR 150
Some Nic card
SB Audigy 4
DVD-ROM & DVD-RW


So, the install goes perfectly.  I remove the CD and reboot and I get the following:

...
Uncompressing Linux... Ok. Booting the kernel.
[17179570.466666] PCI: Cannot allocate resource region 0 of device 0000:00:00:0
mdadm: /dev/mda has been started with 2 drives.
mounting /dev/hda1 on /root failed: Device or resource busy.
{bunch more failures}

BusyBox {some other stuff}

/bin/sh: can't access tty; job control turned off
#
----------------------------

What the crap is going on?  I'm absolutely by no means an avid linux USER, but i've installed it sucessfully at least 30 times with other distros (for which i gave up on using in case you're wondering) and I have never had a problem (except for that solvable one with FC2).

I would love to get this installed... I want to watch some TV.

Thanks!

Ryan

---

### Post by pradeepadapa on 2006-09-25
hi,
     did u connect the 2 hdd's while installing ubuntu on one hdd nd did u allocate the swap size of 1GB or MORE(bec it is required to allocate the swap apace double to ur RAM size).nd also u can select at the time of installation in which hdd u want t install frm the ubuntu installer, just see it, nd u can once again reinstall in the same drive, nd if grub is corrupted u can reinstall the GRUB frm the live cd.

bye.

---

### Post by ryanst on 2006-09-25
Hi, all the hardware installation was done before installing.  through my 4 or 5 installation attempts I've tried partitionning myself and letting ubuntu do it itself.

I should also mention that on previous attempts I had windows installed (with exactly the same result) except that I could sucessfully boot windows using grub.

---

