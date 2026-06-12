---
title: "iso based install for feisty?"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by john_spiral on 2007-04-16
Hi,

has anyone tried the below hd-media install files?

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)

---

### Post by pinkertime on 2007-04-26
Hi john,

I have tried it without success.

I have also tried a different approach using the minimal cd downloaded from [here]("https://help.ubuntu.com/community/Installation/MinimalCD"), with a partial success.

Once downloaded, mount the mini.iso file:

```
 mount mini.iso /mnt/iso/ -t iso9660 -o ro,loop=/dev/loop0 
```

Then copy the content of the /mnt/iso/ directory into a partition (e.g. /dev/hda6 mounted in /media/hda6/):

```
 cp /mnt/iso/* /media/hda6/boot/  
```

Finally, add these lines in the grub file configuration /boot/grub/menu.lst:

```
 
title		feisty minimal CD (on /dev/hda6)
root		(hd0,5)
kernel		/boot/linux vga=normal ramdisk_size=14972 root=/dev/hda6  
initrd		/boot/initrd.gz
savedefault
boot
 
```

Then reboot choosing "feisty minimal CD (on /dev/hda6)" at the grub menu and follow the installation instructions.
I'm able to set up correctly the network and download the base packages. The problem is that this procedure hangs during the loading of the hard disk module. I don't understand if this is a hardware problem (mine) or this procedure is wrong. Any idea? :confused:

---

### Post by john_spiral on 2007-04-26
Hi,

try the method detailed on the below HOWTO:

[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

Post any problems on the same thread.

---

