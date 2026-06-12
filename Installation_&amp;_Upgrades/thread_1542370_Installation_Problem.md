---
title: "Installation Problem"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by hyperAura on 2010-07-30
Hi, I have a laptop which I bought originally with Windows Vista which came with two hard drives.    Later on I did install Ubuntu and then Windows 7 all on the same hard drive where I had Windows Vista installed.    Today I decided to install Backtrace-Linux over Windows Vista partition and for some reason I can't see the rest OS's in the GRUB loader.    I'm guessing that so long I have been using the Vista boot loader and that I've messed it up real bad.    Is there any way to fix this problem? Thanks!

---

### Post by hyperAura on 2010-07-31
This is how my grub 1.5 looks like at the moment. The only Windows entry is the one for windows vista recovery partition. There are missing entries for Windows 7 and Ubuntu 10.04.


[HTML]splashimage=c19999aa-5aa1-48a6-a67a-e84e9444d561/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.30.9
uuid        c19999aa-5aa1-48a6-a67a-e84e9444d561
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=c19999aa-5aa1-48a6-a67a-e84e9444d561 ro quiet splash 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid        c19999aa-5aa1-48a6-a67a-e84e9444d561
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=c19999aa-5aa1-48a6-a67a-e84e9444d561 ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        c19999aa-5aa1-48a6-a67a-e84e9444d561
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1[/HTML]

---

### Post by hyperAura on 2010-08-02
hi guys, I tried adding more entries to menu.lst file for the Ubuntu and Windows 7 OS's, by pointing to the partitions that I believe they are installed. I believe I got the partitions right since when I don't I get a message that the partition does not exist.. The problem is that each time I select to boot to one of these OS's it gets stuck on the black screen where it says Starting up.. Anyone wants to add something that might help? Thanks

---

### Post by varunendra on 2010-08-02
Forget about menu.lst. With my little experience I can say that Grub legacy is not able to boot Ubuntu 10.04. Lucid requires Grub2 which it originally comes with. I may be wrong though but that's what I've found in one of my experiments (link below).

Anyway, the solution is quite easy. You only need to restore Grub2 (assuming your Lucid and Win 7 are intact in their places):

[LIST=1]
[*]Restore Grub2 in the MBR using a Live CD as told [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"), or as I did it in my experiment [here]("http://ubuntuforums.org/showpost.php?p=9513103&postcount=10") **(recommended**, only change sda and sda1 in the linked page example to the hard-disk and its partition where your 10.04 is installed**)**. Its installation directory would be where it was originally installed previously (i.e., where 10.04 is installed).
[*]Update grub after successful installation. It will automatically add your BackTrack installation to the list. ```
sudo update-grub
```
[/LIST]

If you still have any difficulties, please download, run and post the output of [Boot Info Script]("http://bootinfoscript.sourceforge.net/") (courtesy- forum member Meierfra).

---

