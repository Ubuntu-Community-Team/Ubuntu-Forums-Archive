---
title: "dual boot problem"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by elj4176 on 2006-12-14
Been using ubuntu for awhile now and like it. I just got a new HP 64X2 
(dv9074) notebook w/ 2 100 GB sata drives with windows MCE.  I have installed 6.06 amd64 alternate version (6.10 wouln't install) and following this guide 

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) 

 and have modfied the ntbootloader to include an Ubuntu option.
The problem is that when I choose Ubuntu Grub doesn't load anything. The screen clears and it says 'Grub' at the top and that's it. Nothing else happens and hitting enter does nothing.
Booting into mce works fine still. 
I used GParted to partition the second sata drive with 3 partitions as in the guide above (ext3 mounted as '/' and bootable, swap, and fat32 ('osshare'). When asked to install Grub to the mbr I said 'no' and installed Grub to 'hd1'. Should it have been 'sd1'?
It looks like Grub is trying to boot but it isn't working. 

Any help would be appreciated. I'd hate to be stuck w/mce instead of mythtv on this machine.

Thanks!

---

### Post by elj4176 on 2006-12-14
a little more info. I booted into a liveCD and ran grub from the console.
I did 'find /boot/grub/stage1' and it reported '(hd1,0)' 
So I then did 'find /vmlinuz' and it also reported '(hd1,0)'.
 I then did 'root (hd1,0)' and then 'makeactive (hd1,0)' and rebooted. Selected 'Ubuntu Linux' from the boot screen and got the same result. 'GRUB  '
Tried to press 'c' to see what grub was trying to do but nothing and after a few other keypressed the notebook began beeping at me for every key pressed.

I used the following command to allow windows to boot into linux:

dd if=/dev/sdb1 of=/mnt/osshare/ubuntu.bin bs=512 count=1

booted into windows and copied that file onto my c:\ 
then I edited boot.ini to include this line:

c:\ubuntu.bin="Ubuntu Linux"

saved and rebooted.

---

