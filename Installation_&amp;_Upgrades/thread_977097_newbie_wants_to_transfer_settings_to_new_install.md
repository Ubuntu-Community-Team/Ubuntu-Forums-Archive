---
title: "newbie wants to transfer settings to new install"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by KnavishClout on 2008-11-09
Hello, all!  I just recently finished getting my Ubuntu PC set up EXACTALLY how I want it (what with the right themes and everything) and then I came into posession of a nice new hard drive.  Is there any way to "save" my settings from this install so that when I install it again on the new hard drive, I won't have to track down everything again?  

I'm very new to linux so I prefer to use GUI whenever possible, so if you're giving me any code please be very specific and assume I'm an idiot, because when it comes to linux, I am!  

Thanks!

---

### Post by logos34 on 2008-11-09
Why don't you just clone/image the whole installation to the new disk?

DD command is the easiest way--if you copy the entire hard disk it will even transfer the MBR code:

>  Cloning an entire hard disk: 

   **  dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror **

/dev/sda is the source. /dev/sdb is the target. [COLOR=red]Do not reverse the intended source and target.[/COLOR] It happens. Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)Admittedly it's not the quickest way since it copies unused disk space as well, but can't be beat for simplicity.  There's also [Gparted copy/move option]("http://gparted.sourceforge.net/larry/move/move.htm").  If you want speed, use [Partimage]("http://www.partimage.org/Partimage-manual_Usage")--copies only used sectors.  But you'll have to reinstall Grub on the new hard disk (see link my sig).

---

