---
title: "[SOLVED] Grub error 21"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by ngadacz on 2007-08-05
Hello All,

I have been trying to fix this for a number of days, and cannot seem to get my new ubuntu install to work. When I boot I get this Grub Error 21.

Here is my configuration:
- primary hard drive is windows vista.
- second hard drive I formatted and want it to be all ubuntu.

I have read a number of forum post and cannot seem to get the correct syntax for Grub to work.
 when I open grub in a comand window I type in this:

grub> root (hd
 Possible disks are:  hd0 hd1
grub> root (hd1)
grub> setup (hd0)
Error 17: Cannot mount selected partition
grub> 

other forum posts said to include this information:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3737    30013440    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


I would like to use Grub and have the choice to boot into vista or into ubuntu. I have spend a few days on this. I also download supergrub to try and fix this error, I can boot this cd and then say "boot partition", If I go and boot partition 0 which is vista, it will boot fine. If I try to boot partition 1 which is ubuntu, it does nothing and will not boot. 

If anyone could help, I would be very grateful.

Thanks in advance.

Nicholas

---

### Post by merlinus on 2007-08-05
```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute your results for (hdx,x).  In your case, it may be root (hd1,0).

-merlin

---

### Post by ngadacz on 2007-08-05
Hello,

Thanks for your help, This is what I did:

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>

Then I reboot, take out the live CD and I still get

GRUB loading stage1.5

GRUB loading, please wait...
Error 21

My question is, it there any way this could be a problem with my hardware? This computer is an older computer, do I have to have any special jumper setting on my harddrive? I think one drive is master and one is slave. Is that correct?

Or is there any other way I can boot into Ubuntu? using SuperGrub I can still boot into Vista.

Again thanks for any help.

Nicholas

---

### Post by confused57 on 2007-08-05
You might try going into your bios setup and check the settings for your slave drive ide controller...try changing  it to "auto", if it isn't already.  Yes, your hard drive jumper would need to be set to "Cable Select" or "Slave" postion.

---

### Post by ngadacz on 2007-08-05
hello,

My bios does not have a setting for the second harddrive. The pin setting are for slave. Do I have to change this to be cable select? 

What is error 21? Is there any other boot configuration I can use to make this easier? I have one 30 gig drive, which is vista. Then one 20 gig drive which I want to be Ubuntu. If I have to make my first drive 3/4 vista, then 1/4 Ubuntu I would be open to that. However I really don't understand what is going on here. Is there a way to have just the grub files on a very small partition on the first hard drive.

Any suggestions would be a great help. Thanks in advance.

Nicholas

---

### Post by logos34 on 2007-08-05
use the ubuntu live cd to access /boot/grub/menu.lst and /boot/grub/device.map.  Post them if you could.  

When you reinstalled grub in post #3, the ubuntu disk was second in the bios hard disk boot order (the grub shell said root was at hd1,0), and 'setup (hd1)' put grub on the MBR of that disk.  Yet if you are now booting to grub on that disk it becomes hd0, so grub will return an error because root is at hd0,0--not hd1,0.  That may be the problem, I could be wrong.

Or maybe you need to try cable select as suggested above.

---

### Post by logos34 on 2007-08-05
by the way here's error 21:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

---

### Post by sumone on 2007-08-05
Hi

I have just been through a similar process with a new Dell Dimension 9200. This came with Vista pre-loaded onto two 250GB SATA drives. I installed a Western Digital IDE drive with an IDE SATA converter. However installing Ubuntu Feisty produced various grub errors. To get round the problem I booted using the live CD and then disconnected both new SATA drives. Ubuntu can be installed onto the remaining hard drive. I haver to hit F12 on boot up to select the Ubuntu disk otherwise it defaults to Vista. However everything does work

Good Luck, hope your problems fixed soon.

---

### Post by ngadacz on 2007-08-05
Hello here is my menu.lst
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=90d4c9ae-27ed-4ae2-9380-f2f4600b4f84 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=90d4c9ae-27ed-4ae2-9380-f2f4600b4f84 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

and my device.map

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

Thanks again for your help.

Nicholas

---

### Post by logos34 on 2007-08-05
try this: 

With the ubuntu disk set first in the bios, boot to the grub menu screen.  On the first kernel hit 'e' to edit, then 'e' again on the 'root' line.  Change from (hd1,0) to (hd0,0).  Hit enter to save change, and 'b' to boot.  

Post back if that allows you to boot into ubuntu.

---

### Post by ngadacz on 2007-08-05
I cannot find a setting in my bios to allow me to boot into the Ubuntu partition. I know I can open up the computer and unplug my Vista drive and only plug in my Ubuntu one, however this is not what I want, I really want to have a dual boot machine. 

I have a dell precision 420, do you think my machine will just not let me have a dual boot computer, one OS on each of the 2 drives?

Thanks again,

Nicholas

---

### Post by logos34 on 2007-08-06
in your bios there is the device boot order, which is normally set up like this:

1. removable/floppy (if applicable)
2. cdrom/dvd
3. hard disk

But there is also a hard disk subsection listing both of your disks in the order they should boot.

---

### Post by ngadacz on 2007-08-08
Hello,

You were right, this was just a BIOS setting error. There are 2 different area's one for boot order one for harddrives, the area for my second harddrive was blank, i now put in "Auto detect".

Grub comes up fine and I can boot into either Vista or Ubuntu.

Thanks for everyone's help.

Nicholas

---

