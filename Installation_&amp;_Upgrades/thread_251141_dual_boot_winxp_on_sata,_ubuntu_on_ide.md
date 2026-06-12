---
title: "dual boot: winxp on sata, ubuntu on ide"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by thizzlefry on 2006-09-05
SOOO I have been tryin to get this dual boot to work all weekend. I installed Windows xp on my 320gb sata drive. Then installed ubuntu 6.06 on my 120gb ide drive. Now it just boots straight into linux and i can't even go into windows. How can I make it so I can choose? Please anyone help me... I'm anxious to get my dual-boot system up and running....

---

### Post by mxreader on 2006-09-05
Did you select to dual boot and allow Ubuntu to place Grub on the MBR?

Usually the IDE is the first drive, and the SATA is the second. So I would put XP on the IDE first, then let Ubuntu install on the SATA.

But I am only a newbie, others here may help you further.  I myself am having trouble with this setup and Ubuntu does not boot up after the install.  But Grub comes up first and lets me choose which OS to boot, so I can at least choose XP.

---

### Post by confused57 on 2006-09-05
Boot into Ubuntu, open a terminal(Applications---Accessories--Terminal), enter(or copy & paste one line at a time, press enter after each line):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```

then copy & paste the following entire entry at the very end of the file:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

If this doesn't boot your Windows, enter the output of:
```
sudo fdisk -l
```
The -l is a small "L"

---

### Post by thizzlefry on 2006-09-05
Another question I wanted to ask is if I had to setup the partitions in a certain way.... I set it up with /, /boot, /home, swap... I'm not sure if I installed it to the MBR because I don't understand how to do that, I didn't see any options like that during the manual partition setup in the ubuntu 6.06 install. thanks again.

---

### Post by thizzlefry on 2006-09-05
anyone please give me any suggestions. thank you.

---

### Post by confused57 on 2006-09-05
> **thizzlefry said:**
> Another question I wanted to ask is if I had to setup the partitions in a certain way.... I set it up with /, /boot, /home, swap... I'm not sure if I installed it to the MBR because I don't understand how to do that, I didn't see any options like that during the manual partition setup in the ubuntu 6.06 install. thanks again.
Did you get the dualboot working?  I'm no partitioning expert, but from what I've read it doesn't matter if you have a boot partition...if you've already made it, shouldn't be a problem.
I don't think there is an advantage to setting up a boot partition, but a separate home partition is a good idea.  All I set up is a /, home, and swap partitions, the default Ubuntu installation sets up swap as a logical partition.

Usually, when there is a combination of IDE and SATA drives, grub seems to automatically install itself to the IDE drive.
The dualboot instructions I gave you earlier came from this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by almrking on 2006-09-05
Did you alter your /boot/grub/menu.lst entry for windows like confused57 proposed? That is what I did to get a suse 10.1 dual boot working. As far as where Grub was installed, it probably was installed in the mbr of hd0, unless you specified otherwise.

---

### Post by thizzlefry on 2006-09-06
I put what confused57 said in the terminal and now when I boot I saw Windows XP in the menu. But when I went to it I got the error message "NTLDR is missing" press ctrl + alt + del to restart. What should I do? thanks again for all of your help guys.:-|

And here is my sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7649    61440561   83  Linux
/dev/hda2            9562       14593    40419540   83  Linux
/dev/hda3            7650        9561    15358140   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS

---

### Post by sinppet on 2006-09-06
Does it matter what postition of the IDE drive ubuntu is installed? My kubutntu install is on the primary slave.

---

### Post by kopilo on 2006-09-06
A tempoary fix would be to swap the drive that is loaded first in your bios.

Such as if you swap it to the windows drive it will pick up on the windows boot loader and if you set it to the linux drive it will load up in linux.

I gather you mean each os is installed on seperate disks? This in my honest opinion is the best way to go. (This is the setup I have at the moment and it works fine).

Also I don't know if this will work, but I can boot straight into windows or unix from the latest boot loader that comes with ubuntu 6.06 amd 64.

However I enabled my linux machine to be able to see the ntfs drive before I tried booting up in it.

[http://www.ubuntuforums.org/showthread.php?t=77367](http://www.ubuntuforums.org/showthread.php?t=77367)

note, where it says '/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0'

make sure that 'hda1' is actually the right drive to be loading, it might be 'sda1' instead, in which case it should read something like this;
/dev/**sda1** /media/windows ntfs nls=utf8,umask=0222 0 0

Hope this helps. :-k

---

### Post by thizzlefry on 2006-09-06
i entered the command line:
"/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0"

at the end of the fstab file and I still get the same error message when trying to boot to windows "NTLDR is missing." Although now there is a drive on my desktop titled windows and it is in fact my windows directory. Thanks for the help guys. I'm almost there I can feel it!!! ](*,)

---

### Post by kopilo on 2006-09-06
Well at least you have access to your windows partition... read only. >_>

Anyway I did some google searching and came accross [this]("http://www.mail-archive.com/haifux@haifux.org/msg02303.html")
I have no idea if that will help but the person sounds like they are experiencing the same issues as you.

---

### Post by thizzlefry on 2006-09-06
This looks like a viable solution to my problem. I am going to try that as soon as I get home. Thank you kopilo for the extended research on my problem. I hope this is my solution!

---

### Post by confused57 on 2006-09-06
You might want to open a terminal and post the output of:
```
cat /boot/grub/menu.lst
```

Post the entry to boot Ubuntu, here's what mine looks like:

```
title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot
```

and you might want to post the output of:
```
cat /boot/grub/device.map
```

---

### Post by thizzlefry on 2006-09-06
title           Ubuntu, kernel 2.6.15-26-amd64-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title              Windows XP
rootnoverify               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

and the other command

(hd0)   /dev/hda
(hd1)   /dev/sda

---

### Post by thizzlefry on 2006-09-06
I also just wanted to add that I tried to drag the NTLDR file from the windows cd onto that drive that was created on my ubuntu desktop but it gave me and error that I didn't have permission or something. :???:

---

### Post by almrking on 2006-09-06
As kopilo said, you can change the boot order in bios. I left that out of my first post. Thats what I did.

---

### Post by thizzlefry on 2006-09-06
ok well I managed to copy the ntldr file through recovery console and did fixboot but it still says "NTLDR is missing." This is very very dissappointing..... :(

---

### Post by confused57 on 2006-09-06
I found this for repairing ntldr:
[http://hardware.mcse.ms/archive10-2005-1-136823.html](http://hardware.mcse.ms/archive10-2005-1-136823.html)

[http://www.computerhope.com/issues/ch000465.htm#b](http://www.computerhope.com/issues/ch000465.htm#b)

---

### Post by kopilo on 2006-09-07
The only differences I have is with my menu.lst

> **thizzlefry said:**
> 
### END DEBIAN AUTOMAGIC KERNELS LIST

title              Windows XP
rootnoverify               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

and the other command

(hd0)   /dev/hda
(hd1)   /dev/sda


My menu.lst
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

[Here is the grub manuals entry on rootnoverify]("http://www.gnu.org/software/grub/manual/html_node/rootnoverify.html")

---

