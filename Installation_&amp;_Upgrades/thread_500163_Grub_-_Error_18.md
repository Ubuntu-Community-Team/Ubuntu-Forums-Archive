---
title: "Grub - Error 18"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by Goodfox on 2007-07-13
[SIZE="1"](Sorry if this is in the wrong section, but I just installed Ubuntu so this seems like the best place to ask).[/SIZE]

I've just installed Ubuntu 7.04 into a 40gb partition to dual boot with Windows XP.

I've used Ubuntu before and had it working fine, but this time when I installed it, after restarting I keep getting the Error 18 message, so I can't even get onto my Windows partition.
I've googled it and searched around this site for help, but I can't find anything that I can do / understand :/.

When I was installing, nothing seemed to appear about Grub this time (I'm pretty sure there was something last time though, but it was a long time ago).

Is there any way to sort this out without risking anything on my hard drive. If it means reinstalling Ubuntu, is there any way to overwrite or remove the existing install before putting on a new one.

Thanks for any help.

---

### Post by merlinus on 2007-07-13
[FONT=Helvetica,Arial,sans-serif]Grub error 18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Perhaps if you post hardware specs, etc., something may come to mind....

-merlin
[/FONT]

---

### Post by Goodfox on 2007-07-13
I've got 512k RAM, and Ubuntu is installed onto an 80gb hard drive if that helps.

---

### Post by Pumalite on 2007-07-13
[http://ubuntuforums.org/archive/index.php/t-77042.html](http://ubuntuforums.org/archive/index.php/t-77042.html)

[http://www.linuxforums.org/forum/installation/49437-grub-error-18-a.html](http://www.linuxforums.org/forum/installation/49437-grub-error-18-a.html)

[http://www.linuxforums.org/forum/debian-linux-help/52256-first-time-trying-linux-grub-error-18-a.html](http://www.linuxforums.org/forum/debian-linux-help/52256-first-time-trying-linux-grub-error-18-a.html)

---

### Post by Goodfox on 2007-07-13
Thanks Pumalite, but I still don't understand how I'm supposed to go about making the partition without access to Windows or Ubuntu (I'm stuck posting this from the Live CD at the minute) and what to do then.

I'm not really having one of my better days today (I don't know what it is, but I'm having trouble understanding anything I read at the minute), so I could really do with it spelling out step by step, so I know I'm playing it safe.

---

### Post by Pumalite on 2007-07-13
If you read all three links that I gave you could realize that one of the solutions is start fresh. Run DBAN ([http://dban.sourceforge.net/](http://dban.sourceforge.net/)). Then run Gparted ([http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)). Do the partitioning as you wish. If you are dual booting, install windblows first, then Ubuntu. Alternate CD gives better results (text mode, avoids graphical interface problems) If 256 MB RAM or less>Alternate Xubuntu CD. If dual booting with Vista in the same drive: partition from WITHIN Vista. If you can dedicate an entire disk to Ubuntu even better (and easier): choose Guided>Use Entire Disk.

---

