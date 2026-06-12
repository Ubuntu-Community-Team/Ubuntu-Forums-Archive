---
title: "grub2 discover less hard drives and shows &quot;no such device error&quot;"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by kismet-sl on 2010-09-15
Dear All,

I have just installed Ubuntu 10.04 on my system which has the following hard drives setup:
 - motherboard controller:
/dev/sda
/dev/sdb
 - motherboard SATA Raid controller (configured in SATA mode)
/dev/sdc

I have installed linux on /dev/sdc2 boot I had to install the grub2 on /dev/sdb which is the one that was actually booting the system. (I found that, because at the beginning I installed grub2 on /dev/sda but it was not loaded at all during the bootstrap of the machine)

The result is that when the system boostrap it end up to "grub rescue>" shell reporting that 
```

error: no such device: <UUID>

```
The strange part is that from the "grub rescue" only the ls command works, while help, dump, lsmod, or insmod return the message "Unkwon command"

On the "grub rescue" i found that ls report only 
```

(hd0) (hd0,1) (hd1,1) (hd1,5) (fd0)

```
but the grub configuration states that the root is on (hd2,2) so **it seems that the problem is that (hd2) the drive with the uuid shown by the error message is not recognize by grub, do you have any idea?**

Thank you!

---

### Post by dino99 on 2010-09-15
open a console then run:

sudo grub-mkconfig
sudo update-grub

look at this thread too: [http://ubuntuforums.org/showthread.php?t=1574605](http://ubuntuforums.org/showthread.php?t=1574605)

---

### Post by kismet-sl on 2010-09-15
I have done what you suggested by starting the system with Ubuntu Install CD in LiveCD mode, then I opened a console and I executed the following command:
```

sudo mkdir /mnt
sudo mount /dev/sdc2 /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt 

```

Then from the chroot environment I executed the command that you suggested:
```

sudo grub-mkconfig
sudo update-grub

```

I rebooted but I received the same error message from grub2.
```

error: no such device: 96574346-f4cc-42a0-b7cf-a0f095a6b096

```
(exactly the uuid of /dev/sdc)

I think it is worth to note that my system has the following setup:
/dev/sdc 232.88G 
/dev/sdc1 - extended
/dev/sdc5 - NTFS UUID=8678C11778C106C1
 
/dev/sda 232.88G 
/dev/sda1 - NTFS, 58.89G UUID=4ED0BBD8D0BBC48D

 
/dev/sdb 189.92G 
/dev/sdb1 - NTFS, 117.19G UUID=C4C41EADC41EA1AA
/dev/sdb2 - ext4, 27.94G UUID=96574346-f4cc-42a0-b7cf-a0f095a6b096
/dev/sdb6 - ext4, 42.88G UUID=cb7.....
/dev/sdb5 - swap, 2G 

but the ls command (executed from the grub rescue shell) reports only 
```

(hd0) (hd0,1) (hd1) (hd1,5) (fd0)

```

which I can hardly map to my actual system configuration.

I have also tried to execute (from the grub rescue shell) the commands
```

set root=(hd0,1)
chainloader +1

```
for booting up windows but it received the error unknown command "chainloader"

P.S.: I have notice that /dev/sdXY the X changes between reboot so I have perform grub-install on all the /dev/sdX

Thank you!

---

