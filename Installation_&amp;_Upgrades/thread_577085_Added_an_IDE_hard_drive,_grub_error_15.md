---
title: "Added an IDE hard drive, grub error 15"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by Laynix on 2007-10-15
I've added an IDE hard drive to my system,  before GRUB loads I get:
"GRUB loading, please wait...
Error 15"
If I unplug the new hard drive I can load Ubuntu normally.
My IDE drive configuration looks like this:
IDE P M: new drive, formatted ext3
IDE P S: Windows
IDE S M: DVD-RW
IDE S S: Ubuntu

---

### Post by Pumalite on 2007-10-15
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Laynix on 2007-10-15
Well, I don't have a typo in my grub config, since it works when I don't have the other hard drive installed.
What is happening here?  Is the hard drive that I have added acting as my Windows drive as far as GRUB is concerned?

---

### Post by Pumalite on 2007-10-15
Boot from Live CD.

[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by Laynix on 2007-10-15
sudo fdisk -lu

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63   312576704   156288321   83  Linux

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/hdb2       204796620   312576704    53890042+   b  W95 FAT32

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1              63    53721359    26860648+  83  Linux
/dev/hdd2        53721360   488392064   217335352+   5  Extended
/dev/hdd5        53721423    57914324     2096451   82  Linux swap / Solaris
/dev/hdd6        57914388   488392064   215238838+  83  Linux

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   625137344   312568641   83  Linux

cat /boot/grub/menu.lst

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b45f3a60-aeed-436a-9bfd-b31f23d27305 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b45f3a60-aeed-436a-9bfd-b31f23d27305 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.17-12-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=UUID=b45f3a60-aeed-436a-9bfd-b31f23d27305 ro quiet splash
initrd          /boot/initrd.img-2.6.17-12-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=UUID=b45f3a60-aeed-436a-9bfd-b31f23d27305 ro single
initrd          /boot/initrd.img-2.6.17-12-generic

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=b45f3a60-aeed-436a-9bfd-b31f23d27305 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=b45f3a60-aeed-436a-9bfd-b31f23d27305 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Laynix on 2007-10-15
I'm thinking that if I change (hd1,0) to (hd3,0) for Ubuntu (hdd) and (hd0,0) to (hd1,0) for Windows (hdb) it will solve this problem.  Is this correct?

---

### Post by Laynix on 2007-10-15
Hmm.. is it hd(0,0) for the first hard disk or for hda?  My guess is the first drive.

---

### Post by PacketCollision on 2007-10-15
Yeah, make those changes and everything should work.

---

### Post by meierfra on 2007-10-15
(hd0,0) is for the first partition on the first drive


Since hdd seems to be the third drive you will have to use (hd2,0) for Ubuntu.


And for windows you have to use (hd1,0). But since windows likes to be on the first drive, you need to use "map"  to convince windows  that it is one the first drive even if it isn't:


title  Windows NT/2000/XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

---

### Post by Laynix on 2007-10-15
Ah, that sounds good, I'll give it a try.

---

### Post by Laynix on 2007-10-15
I made the changes and still ended up with error 15, then I changed chainloader     +1 to chainloader(hd1,0)+1 and still have the error.

---

### Post by Laynix on 2007-10-15
What is the minimum I need to have in grub to list my Ubuntu and Windows partitions?

---

### Post by meierfra on 2007-10-16
Sorry, I should have thought about that right away.  You also  need to reinstall grub:

In a terminal in the live cd:

sudo grub

at the grub prompt :

find /boot/grub/stage1

(This should return something of the form  (hdx,y), probably (hd2,0) ) 

root (hdx,y)

setup (hd0)

quit

If you did not get (hd2,0)  as response to find /boot/grub/stage1, you will also have to modify your menu.lst accordingly.

---

### Post by Laynix on 2007-10-16
(hd2,0) was the response but I'm still getting grub error 15.

---

### Post by meierfra on 2007-10-16
did you do 

root (hd2,0)

setup (hd0)

at the grub prompt?

---

### Post by Laynix on 2007-10-16
Yes, I typed that exactly.

---

### Post by Laynix on 2007-10-16
This is my menu.lst:

default 0

timeout 10

title Ubuntu
root (hd2,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=b45f3a60-aeed-436a-9bfd-b31f23d27305 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by meierfra on 2007-10-16
I don't  understand what is going on. Since you never get to the grub menu, editing menu.lst should  do  no good.

Can you change the boot order in the bios? That might  make a difference.

---

### Post by Laynix on 2007-10-16
Oh, I thought that editing the menu.lst settings was all that I needed to do really...

I changed BIOS to boot from HDD-2 and I was able to get the GRUB menu to show.  Windows loads fine, but now if I choose Ubuntu it returns: Error 15: File not found  Press any key to continue...

---

### Post by Laynix on 2007-10-16
Does this have anything to do with the device.map file?

---

### Post by meierfra on 2007-10-16
O.K now that you get the grub menu, editing the  menu.lst should be all you need to do.

But before you change the menu.lst do this:

at the grub menu at boot up, select "ubuntu" but  instead of pressing enter press "e"

Press "c" and type "find /boot/grub/stage1"

Again you will get an  (hdx,0) response.

Press Esc

select the row "root (hd2,0)" and press "e".

Change it to  "root (hdx,0)"

press "enter" and then  "b"

This should boot you into "ubuntu". If this worked change "(hd2,0)" in the menu.lst to "(hdx,0)"

---

### Post by Laynix on 2007-10-16
Great success!
I had to change (hd2,0) to (hd0,0).  I checked the menu.lst file again, and it still shows Ubuntu as (hd2,0).  I restarted and had to go through the steps again.  Should I now just edit the menu.lst file to show (hd0,0)?

---

### Post by meierfra on 2007-10-16
Yes.

---

### Post by Laynix on 2007-10-16
Ah, good.  It is working fine now.  Thank you for your much needed help!

---

### Post by meierfra on 2007-10-16
> Thank you for your much needed help!

You are welcome.


> Does this have anything to do with the device.map file?

It could be that some of our earlier trouble have been caused by  the device map. Actually I still don't understand why you got "error 15" after the "grub reinstall" and before you changed the boot order.


Just  to please my curiosity could you post  your current fdisk and device.map:

sudo fdisk -l

and 

cat /boot/grub/device.map

from a ubuntu terminal.

---

### Post by Laynix on 2007-10-16
sudo fdisk -l:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19457   156288321   83  Linux

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/hdb2           12749       19457    53890042+   b  W95 FAT32

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        3344    26860648+  83  Linux
/dev/hdd2            3345       30401   217335352+   5  Extended
/dev/hdd5            3345        3605     2096451   82  Linux swap / Solaris
/dev/hdd6            3606       30401   215238838+  83  Linux

sudo cat /boot/grub/device.map:

(hd0)   /dev/hda
(hd1)   /dev/hdd
(hd2)   /dev/sda

It doesn't make a whole lot of sense to be, unless the device.map doesn't affect the grub menu and the devices are listed backwards in the fdisk list.

---

### Post by meierfra on 2007-10-16
Doesn't make any sense to me either. I hoped I would learn something so that I wouldn't  send people of to a wild goose chase again the next time I try to help somebody in a similar situation.

 Oh well and good night.

---

### Post by meierfra on 2007-10-16
I think I figured out why the device map doesn't  match the menu.lst:

The device.map is only used during the grub-install. Grub was installed  via the live-cd, which did not use  the device.map from the ubuntu partition, but generated its own. 

Also for anybody who reads this to solve a similar grub problem: Hermanzone has some good  advice how to handle  grub problems after adding a new hard drive:

[Hermanzone device/map]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map")

and 

[http://ubuntuforums.org/showthread.php?t=351974]("http://ubuntuforums.org/showthread.php?t=351974")

---

### Post by jimbo99 on 2007-10-16
Grub can easily get messed up.  This is not something the average user should ever ever even look at.  I've had my share of dealings with grub.  Believe me, it gets worse if you fail to plug in the drives into the same headers (as in SATA headers) as you had them originally.  I've disassembled my computer to clean it on many occasions; a clean computer lives longer.  When putting the HDDs back (in my case I have 3 SATA drives) I've received the same errors.  If you go about pulling the drives and just starting with this drive or that drive your bios can be changed for you without your input, primarily the option for which drive is the boot drive.

So, you can wind up making things worse if you don't put things back exactly and if you don't examine your bios to ensure that the boot drive is the exact drive you had before.

When you do your kernel updates you probably will encounter this issue again.  It is just a defect in the update procedure.  It tries to run the grub setup and can incorrectly detect which drive is the boot drive and set you back to this same issue.

Every time I do the kernel update I have to boot with my live cd and then modify the menu.lst file manually to tell it which one is the one I have the boot files on.  Otherwise I get these same errors.

Nothing I can do will change it, so I am very careful that when I'm presented with the option to do the kernel update; I ensure I have enough time to take out to modify the menu.lst file.  Normally that means finding my ubuntu live cd before hand, remembering the commands to mount the drives, and then using the terminal to go to the appropriate location to edit the file.  I have this down now but in the past it took me a long time to get it back up and running because of all these things.

I'm hoping that in Ubuntu 7.10 they will have resolved these issues but I'm not counting on it.

I know some of this has to do with which drive is set as the boot drive in bios and how the drives are connected to the headers.  I'm sure it gets more complex when you have USB drives, IDE drives, and SATA drives in the same mix.

I do think someone needs to take a real serious look at the whole grub and boot loader process because it does have flaws that need to be eliminated so that the average mom and pop never have to deal with it, sort of how when you add a drive to a windows box it doesn't mess up your boot process.  Sure you still have to partition it and format it but at least the added drive doesn't keep your computer from booting into the OS.

Anyway, my 2 cents.  Lesson 1 is don't start fiddling with the bios nor with pulling drives; instead first examine the bios and ensure you drives are attached to the computer in the same order they were when the system was last working properly.

---

