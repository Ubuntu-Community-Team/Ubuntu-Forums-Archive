---
title: "Grub hanging on dual-boot re-install--HELP?"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-07-02
I had a dual boot XP/Breezy install which I then upgraded to Dapper. After having some problems within Dapper I decided to download the Dapper ISO (386-Desktop) and reinstall it. I took note of all my partitions so that I could set it up the same way with the fresh install. 

The way my system was set up previously was that the NT bootloader gave me a choice between XP Home and Ubuntu. When I chose Ubuntu it would then take me to GRUB from which I could boot into linux. 

I ran through the CD install process (including manually setting up my partitions the same as before) and all went well and when I restarted, the NT bootloader gave me the same two choices, but when I pick Ubuntu Linux it shows 'GRUB.' but then just hangs with a blinking cursor. I'm not sure if it's a problem with GRUB not being installed properly (I saw nothing about GRUB during the installation, although I might have missed it.) The grub folder appears to have all the proper files in it, so I'm stumped.

I'm not sure how to re-install GRUB from the Dapper CD. I've tried replacing the grub folder with a copy of my old grub folder (which I backed up) but this doesn't do anything- it still shows 'GRUB' and hangs.

I haven't changed the location of any partitions (ie. the /boot partition is on the same drive as the windows boot partition).

Everything appears to be the same as before but it just hangs after it goes to run GRUB. Anybody got any ideas? 

Is there a 3rd part multiboot app that I can use instead of this?

---

### Post by richardq on 2006-07-03
I've since downloaded the 'alternate' 386 iso and tried installing that. It re-installed grub during the rescue process but grub still hangs as soon as I select it from the NT bootloader menu. Again, it just says 'GRUB' with a flashing cursor, and does nothing else.

Is there a way to bypass the nt bootloader and boot ubuntu directly (a boot cd maybe? I don't have a floppy drive).

---

### Post by wifiabc on 2006-07-03
Hi,
You can try taking a look at this. I followed these instructions for my multiboot.
[http://www.justlinux.com/forum/showthread.php?t=130715]("http://www.justlinux.com/forum/showthread.php?t=130715")

---

### Post by rpdillon on 2006-07-04
Having the same problem, but totally different setup.  I'm on amd64 with Kubuntu and just upgraded some core packages (like kernel and maybe grub, not sure) and now the system simply hangs when it would usually load grub.

I get the BIOS info screen, with "GRUB " at the bottom and a flashing cursor.

I've booted into a system with the alternate CD (I'm running RAID0) and mounted the md0 and md1 partitions and checked the menu.lst...everything looks OK.  I reinstalled grub to the MBR of (hd0,0) and that didn't do anything for me either.  I even made the old kernel the default (instead of 2.6.15-25, I switched back to 2.6.15-23) which used to work, still nothing.

What's really annoying me is that I can usually troubrlshoot this kind of stuff on my own just fine, but if GRUB won't give me any error messages, I'm kind of lost.

Does anyone have any info about what error causes the flashing "GRUB"?

Thanks,
Rick

---

