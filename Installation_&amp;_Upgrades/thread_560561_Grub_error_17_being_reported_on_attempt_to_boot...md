---
title: "Grub error 17 being reported on attempt to boot.."
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by lewac on 2007-09-26
This problem occurred AFTER booting into winY2K on a multi-OS machine. It seems like win2000 "knows" about grub but my thoughts were just how did it access it? Well it certainly did because the menu.lst file under ubuntu here was modified!

So. After working on this thing for several hours (I'm fairly new to linux) and NOT finding a direct solution here (or anywhere else) I decided to post my solution. But first off I'd made a copy of the entire first sector of the first listed drive on my system (hd0)... uhh..  Its always a good idea to back your MBR (and backing the entire first sector is even better) after installing/deleting OS's or modifying partitions in any way. However restoring that did not work because grub "looks for" menu.lst where it expects to find it. And it DID find it because (almost) the proper title lines were displayed for subsequent OS selections.

Note that "live CD Super Grub" did NOT fix the problem (but maybe because I'm not sure what I was doing in there).

It was suggested in here somewhere to boot from the ubuntu live CD which was what I did first. Then I examined the "mounts" and they were all okay thus no problems existed within the structure of the various partitions themselves (the easiest way here is to use the GUI). This was simple so I browsed to the menu.lst file and had a gander at it. I kept a copy of the original and compared it to the current one installed and found that the boot partition being referenced was now INCORRECT.

So to fix it on this machine I did the following:

First I opened a terminal...
Then I entered the following (to enable root access):

 sudo gedit /media/disk/boot/grub/menu.lst

This launched gedit displaying menu.lst. I then modified the grub "root" command to match my previous copy of menu.lst. In my case win2000 had somehow modified the original configuration FROM "root (hd0,4" TO "root (hd2,4" !!!

So changing the "2" BACK TO a "0" under all the title sections that mentioned ubuntu fixed the problem (after SAVING the changes of course).

---

### Post by thefriend on 2007-09-26
Hello Lewac

Do you have an USB device connected to your Computer?
If yes then unconnect it boot the computer and reconnect the USB device.

That may resolve your problem.

Greetings 

Andy

---

### Post by Pumalite on 2007-09-26
Get a Knoppix: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html) (mounts oartitions automatically)
Boot from it, got to terminal and post:
sudo fdisk -lu
The, from appropriate partition(look in /media and /mnt) post:
cat /boot/grub/menu.lst

---

