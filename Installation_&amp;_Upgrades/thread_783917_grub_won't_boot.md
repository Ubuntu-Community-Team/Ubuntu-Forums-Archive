---
title: "grub won't boot"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by jjascarm on 2008-05-06
I just installed Ubuntu 8.04 onto my computer, I get to the grub menu but none of the operating systems listed there will boot. When I try to boot Ubuntu I get error 17, which I think means that the disk cannot be mounted. When I try to boot Windows XP I get error 22.
I have three hard drives: 80GB IDE which has XP on it, and two 320GB SATA drives, one is formatted as NTFS and I installed Ubuntu and Grub to the other one. This drive is SDB, the other 320GB drive is SDC, and the XP drive is SDA. 
Any help would be appreciated - I will need to temporarily change my configuration back to boot XP, but I should be able to get any further information by using the Live CD, which is what I am doing now.

Thanks in advance

---

### Post by jjascarm on 2008-05-06
Just had a couple of thoughts. I think the XP partition might not be booting because it is not the first hard drive and the swap command is not in the menu.lst file.
Following is the 'commands' section of my menu.lst file:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2dddc697-cb07-4ebb-9ea1-62d11ef85a4b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2dddc697-cb07-4ebb-9ea1-62d11ef85a4b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
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
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

Thanks again

---

### Post by Herman on 2008-05-06
One way to fix that would be to go into your BIOS and change [the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") so that your Windows XP hard drive is number1 hard drive, your Ubuntu hard drive will be number2 hard drive and your data hard drive will be number3.
You might need to [re-install GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") to your first hard drive.

---

### Post by didac on 2008-05-06
Is your Ubuntu hard disk the secondary or the master?

Try to boot manually. When grub loads, press any key and start a command prompt. There type 

```
find /boot/grub/stage1
```

Imagine it tells you "root (hd0,0)" that means partitions have changed after the installation. Anyway, whatever it says, type now:

```
root (hd0,0)
```

or whatever 'find' said. Press ENTER.

Now type

```
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2dddc697-cb07-4ebb-9ea1-62d11ef85a4b ro 
```

Press ENTER and type:

```
initrd /boot/initrd.img-2.6.24-16-generic
```

ENTER again and type:

```
boot
```

You should be booting by now. Remember to update your /boot/grub/menu.lst to reflect present partitions.

---

### Post by jjascarm on 2008-05-07
Got linux to boot from the menu after editing the mun and changing (hd1,0) to (hd0,0)

Thanks for you advice

---

### Post by bweinel on 2008-05-08
I had the same problem with the Hardy Heron installer on my PC hardware [one EIDE drive as drive 0 and two SCSI drives as drive 1 and drive 2.] The installer setup the Hardy Heron install on the EIDE drive, but setup menu.lst in grub to boot the root installation off the first SCSI drive (hd1,0) and not the EIDE drive (hd0,0). When I first booted I got 'error 17'. I had to go into the grub edit mode on boot up and change the root pointer from hd1,0 to hd0,0 in order to get it to boot the first time. Then once booted, use nano to edit the menu.lst in the grub subdirectory to fix the problem. I suspect from this thread my experience wasn't unique.

Cheers 
Bill

---

