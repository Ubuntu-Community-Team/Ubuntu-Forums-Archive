---
title: "Partion Problem XP"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Kwisniew on 2008-02-20
I have a 320G hard drive with Windows XP installed. I have used Ubuntu on other PC's so I went to install on the XP system, wanted dual boot.  I set the partition to be 270G thinking this would be the XP partition and Ubunto would be left with the extra 30G, about. I did the Ubuntu install of CD, however when I reset the system and go to bring up XP the system just says "Starting". I can't boot XP, Ubuntu works fine.  Did I lose the XP boot....my files are still there....any help would be great.
Thanks Kevin

---

### Post by agim on 2008-02-20
your menu.lst file should look something like this

default 1

timeout 10

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet
boot

find where your windows partition is (hd 0,1 or whatever) and make sure its actual location and its location in menu.lst are the same.

I wouldn't panic if you can still read your windows files.

---

### Post by agim on 2008-02-20
Important! Make sure you make a backup of menu.lst before changing anything.

---

### Post by Kwisniew on 2008-02-20
Thanks, not sure where the menu.lst file is? This would cause XP
not to load?


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a77ca80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   564668684   282334311    7  HPFS/NTFS
/dev/sda2       564668685   622550879    28941097+  83  Linux
/dev/sda3       622550880   625137344     1293232+   5  Extended
/dev/sda5       622550943   625137344     1293201   82  Linux swap / Solaris

---

### Post by agim on 2008-02-20
It may be having trouble finding Windows. Although usually you get a OS not found error.
If it isn't grub (linux's boot loader) then you may need to try this.

[http://www.uluga.ubuntuforums.org/showthread.php?t=654278](http://www.uluga.ubuntuforums.org/showthread.php?t=654278)

For now, paste the menu.lst file here.
You can access this by typing this command in a terminal.

gedit /boot/grub/menu.lst

---

### Post by Kwisniew on 2008-02-20
Yes, this is the boot menu, the grub, got it. i see where it put the Windows XP at the bottem. It just never seems to start?


title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9804d7e2-9d9f-4904-83ee-2aae113d0c87 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9804d7e2-9d9f-4904-83ee-2aae113d0c87 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +

---

### Post by agim on 2008-02-20
In that case you may have to use your XP rescue disk. Maybe somebody else here will have more info.

---

### Post by Partyboi2 on 2008-02-20
Your xp entry you posted is this:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +
make sure there is a 1 after the + on the chainloader line
so
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Kwisniew on 2008-02-20
That was my bad, I have the +1, still looking at other options. I can't believe
XP would be blown away. Although UNIX is my heart.

---

### Post by Partyboi2 on 2008-02-20
try using [supergrub]("http://supergrub.forjamari.linex.org/")

---

### Post by froy02 on 2008-02-21
Boot into Ubuntu and go to Places->Computer and check if you can find your Windows partition from there.  Right click on it and choose mount.  You would then see your windows files.  If you have data that you need to save you can then copy it to a USB stick.  

I noticed that your windows partition does not start at 1 but it starts at 63.  Try chainloader +63 in your menu.lst.

---

### Post by Kwisniew on 2008-02-24
We can close this one, I had to rebuild Windows but this time I created 4 partitions
before installing Windows or Ubnutu. This solved the problem and I can dual boot.
Trying to reduce the Windows partition is bad, the whole OS is bad....thank
god for Ubuntu!

---

