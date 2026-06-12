---
title: "Trying to install 3 Os'S with Grub Ubuntu"
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by banjo04414 on 2005-09-01
Win XP and FC4. I have no problem with Ubuntu and WinXP with dual boot. However, when I tried to install FC4, it's Grub bootloader only sees FC4 and WinXP I was able to rescue Ubuntu and WinXP by getting to the command prompt and restoring Grub thru menu.lst. Now I've lost FC4. I can restore that but then I'll lose Ubuntu.

 I've tried editing Grub, but if in Ubuntu it can't "parse" the bootup for FC4 if selected. And vice-verus if I have FC4 enabled. My menu.lst looks like this;

title        Ubuntu, kernel 2.6.10-5-i386
root       (hd0,1)
kernel    /boot/vmlinuz-2.6.10-5-i386 root=/dev/hdb3 ro quiet splash
initrd     /boot/initrd.img-2.6.10-5-i386
savedefault
boot

title        Ubuntu, kernel 2.6.10-5-i386 (Recovery Mode)
root        (hd1,0)
kernel     /boot/vmlinuz-2.6.10-5-i386 root=/dev/hdb3 ro single
initrd       /boot/initrd.img-2.6.10-5-i386
savedefault
boot


Title        Ubuntu, kernel memtest86+
root        (hd1,2)
kernel     /boot/memtset86+.bin
           Other Linux System

title        Fedora Core (2.6.11-1.i369_FC4)
root        (hd1,0)
kernel     /boot/vmlinuz-2.6.11-1-i369_FC4 ro root=LABEL=/1 rhgb quiet
initrd      /boot/initrd-2.6.11-1-i369_FC4.img
savedefault
boot
chainloader +1

            Other

title        Microsft Windows XP
root       (hd0,0)
savedefault
makeactive
chainloader +1       


 I know what you think...the i369 is a mistake. No, that came right from FC4 menu.lst. Any ideas about how you would edit grub (the one with Ubuntu) to make FC4 work. My bro just installed FC4 on his station and I was trying to install it on mine so we could fool around with it in our spare time. FC4 didnt see Ubuntu during install. I've got Ubuntu running pretty good and don't want to start over after all the up-dates I've done to it.Thanks for any help.

---

### Post by essexman on 2005-09-01
[QUOTE=banjo04414] My menu.lst looks like this;

title        Ubuntu, kernel 2.6.10-5-i386
root       (hd0,1)
kernel    /boot/vmlinuz-2.6.10-5-i386 root=/dev/hdb3 ro quiet splash
initrd     /boot/initrd.img-2.6.10-5-i386
savedefault
boot

title        Ubuntu, kernel 2.6.10-5-i386 (Recovery Mode)
root        (hd1,0)
kernel     /boot/vmlinuz-2.6.10-5-i386 root=/dev/hdb3 ro single
initrd       /boot/initrd.img-2.6.10-5-i386
savedefault
boot


Title        Ubuntu, kernel memtest86+
root        (hd1,2)
kernel     /boot/memtset86+.bin
           Other Linux System

title        Fedora Core (2.6.11-1.i369_FC4)
root        (hd1,0)
kernel     /boot/vmlinuz-2.6.11-1-i369_FC4 ro root=LABEL=/1 rhgb quiet
initrd      /boot/initrd-2.6.11-1-i369_FC4.img
savedefault
boot
chainloader +1

            Other

title        Microsft Windows XP
root       (hd0,0)
savedefault
makeactive
chainloader +1       

[/QUOTE]

The trick is in the grub drive numbering system. The key lines are the root (hdX,Y) lines.

The X is the drive order, starting with 0 and the Y is the partition order for that drive, starting with 0.

eg (hd0,1) is the second partition on the first drive. (hd5,4) is the fifth partition on the sixth drive.

The next lines in the menu block (ie kernel     /boot/vmlinuz-2.6.11-1-i369_FC4 ro root=LABEL=/1 rhgb quiet) are telling grub where in the 'root' to find the kernel image to 'boot' from.

You will need to adjust the root entries in the menu.list to match the partitions where you distro installations sit.  This will be the same from Fedora or Ubuntu.

---

### Post by essexman on 2005-09-01
[QUOTE=essexman]The trick is in the grub drive numbering system. The key lines are the root (hdX,Y) lines.

The X is the drive order, starting with 0 and the Y is the partition order for that drive, starting with 0.

eg (hd0,1) is the second partition on the first drive. (hd5,4) is the fifth partition on the sixth drive.

The next lines in the menu block (ie kernel     /boot/vmlinuz-2.6.11-1-i369_FC4 ro root=LABEL=/1 rhgb quiet) are telling grub where in the 'root' to find the kernel image to 'boot' from.

You will need to adjust the root entries in the menu.list to match the partitions where you distro installations sit.  This will be the same from Fedora or Ubuntu.[/QUOTE]
 And try removing the chainloader line from the Fedora menue, as this only needs to be on the windows menu to reach the windows loader

---

### Post by banjo04414 on 2005-09-01
I thought it might be that. Unfournately, I'm confused about the way  Linux numbers it's partitions. I ran QtParted and tried what it showed as partition drive numbers. Then I tried whay Ubuntu had,ie: (hd0,1). Then what was in menu.lst for FC4. (hd1,0). I also agree chainloader probably doesn't need to be there. I put that in as when I had Mandriva LE installed with Ubuntu, it had it in the menu.lst.

 The numbers in QT are :

  Number       Partition       Type     Status     Size        Used Space   Start   End   Label
   01              /dev/hdb1    EXT3                 15,99GB       7.64GB      .03GB  15.93   /1
   02              /dev/hdb2    Extended           12.46GB         NA          15.93   28.39
      |_ 03       /dev/hdb5    EXT3                  12.46           670.18      15.93   28.39
   04              /dev/hdb4    EXT3                  12.44           669.01      28.39   40,83
   05             /dev/hdb3     EXT3                  33.70            3.73         40.83   74.53  /

 All these are on hdb. Now I thought that hd0,0 was assigned to Win partition. That hd1,0 was the beginning of Linux partition.??? But, QtParted shows hda1 and hdb1 respectively. I always thought hd0 was the 1st hd, hd1 was the 2nd? Told you I was confused. Ant suggestions? Thanks.

---

### Post by banjo04414 on 2005-09-02
Finally resolved my problems late last night. First, it was (hd1,0) for the boot-up partition Grub was looking for. That got me the first part of the  boot-up,ie: title, root  portion. Then my kernel went into a "panic" on the kernel and initrd part. After screwing around well into the night, as there were so many "errors" I began to think it had to do where the kernel image was booting from. The answer came that it was using the orginal image that it installed when I first put the system on the HD. After looking at my tables from QtParted, I decided to remove the "root=LABEL=/1 rhgb quiet" and replace it with "root=/dev/hdb1." (hdb,1) showed as the partition Where it was installed on QtParted. Worked like a charm. So simple but so compilicated at the same time.
Also, a simple error on my part. The kernel is 2.3.11-1..1369 not - i369. Bad typo error on my part! So with modifications to the the menu.lst it now booths like it should.
 Many thanks to the people that helped me out. That is why Ubuntu is 1st class IMO.

---

### Post by essexman on 2005-09-02
[QUOTE=banjo04414]Finally resolved my problems late last night. First, it was (hd1,0) for the boot-up partition Grub was looking for. That got me the first part of the  boot-up,ie: title, root  portion. Then my kernel went into a "panic" on the kernel and initrd part. After screwing around well into the night, as there were so many "errors" I began to think it had to do where the kernel image was booting from. The answer came that it was using the orginal image that it installed when I first put the system on the HD. After looking at my tables from QtParted, I decided to remove the "root=LABEL=/1 rhgb quiet" and replace it with "root=/dev/hdb1." (hdb,1) showed as the partition Where it was installed on QtParted. Worked like a charm. So simple but so compilicated at the same time.
Also, a simple error on my part. The kernel is 2.3.11-1..1369 not - i369. Bad typo error on my part! So with modifications to the the menu.lst it now booths like it should.
 Many thanks to the people that helped me out. That is why Ubuntu is 1st class IMO.[/QUOTE]

Glad to hear you are up and running.

It is confusing and probably going to stay this way for some time as Grub is starting to become the predominant bootloader for linux.

Linux numbers/orders drives with a letter, starting with 'a' like this:

> hda hdb hdc

Linux the tags on a number to number the partitions like this:

> hda1 hdb8 hdd7

Grub has its own numbering/order system and drives are identified with a number, starting with 0, then a comma, the a number to identify the partition.  this is surrounded with brackets.

> (hd0,0) (hd3,9) etc

For a tech person with fifty servers each with ten partitions on four disks this is all vitally important.

However, there is a growing number of linux users like you and me who only have two, three, maybe four partitions, this is confusing and will need to be simplified.

Grub has a lot more functionality than just booting into a kernel and I can recommend that more people read the [manual](http://www.gnu.org/software/grub/manual/)  It is not the easiest thing to read, but very useful

---

