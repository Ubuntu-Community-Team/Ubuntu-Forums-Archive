---
title: "Ubuntu 6.06 reboots after sucessful install"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by WesleyWex on 2006-07-09
I've installed Ubuntu 3 times in a row trying different HD configurations, and my PC restarts after grub loads, see details:

```
Searching for Boot Record from IDE-0..OK
GRUB Loading stage 1.5.


GRUB loading, please wait...
Press 'ESC' to enter the menu... 2
```

```
Booting 'Ubuntu, kernel 2.6.15-23-server'

root (hd0,4)
 Filesystem type is ext2fs, partition type 0x83
kernel  /vmlinuz-2.6.15-23-server root=/dev/mapper/Ubuntu-root ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x16b75f]
initrd  /initrd.img-2.6.15-23-server
   [Linux-initrd @ 0x7140000, 0x69f48c bytes]
savedefault
boot
```

At this point the machine restarts.

I'm using a AMD K6-II processor, 520 MHz, 128 MB RAM and 40 GB HD. I've tested the RAM using supplied MEMTEST and after 11 hours no errors were found.

Anyone knows what may be going on?

---

### Post by taurus on 2006-07-09
I think there is something wrong with the "root=/dev/mapper/Ubuntu-root" option!  It should be pointing to your actual root partition, something like /dev/hda4 (or whatever it is)...

---

### Post by WesleyWex on 2006-07-09
Well, I did nothing but follow the installer instructions, and I'm not an advanced unix user, can you tell me how can I change this now?

---

### Post by taurus on 2006-07-09
There are a few options.  When you are at the GRUB menu, you can hit letter e for edit.  Then, change the root to point it to whatever your root, /, partition is.  After your system is up, don't forget to modify /boot/grub/menu.lst again so you don't have to do it everytime you boot Ubuntu.  Another way is to boot the LiveCD and mount your harddrive with /boot partition.  Modify /boot/grub/menu.lst.  Unmount it, /boot, and reboot...

---

### Post by confused57 on 2006-07-09
See this thread:
[http://www.ubuntuforums.org/showthread.php?t=206384](http://www.ubuntuforums.org/showthread.php?t=206384)

Did you intend to do a server install?  If not, you might want to try the Dapper alternate CD or possibly Xubuntu alternate CD.

---

### Post by WesleyWex on 2006-07-10
It's weird but when I go to the edit screen everything is ok (path=/dev/hda1), and still the machine reboots.

And indeed, I've downloaded the wrong thing, but now I see Ubuntu doensn't want to be installed on my very old machine... first I had to manually configure X to recognize my serial mouse, and now the installer hangs on step 3 ([more details here]("http://www.ubuntuforums.org/showthread.php?t=212789")).

I guess I should try another linux distribution...

---

### Post by pirast on 2006-07-12
i have the same problem, /dev/mapper is correct, it is being used when activating lvm

---

### Post by pirast on 2006-07-13
its caused by the server kernel.

try to install the desktop kernel, it is available in linux-386

---

