---
title: "GRUB fails to detest windows XP on the same sata disk"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by Naturally on 2006-12-29
Hi,

I am trying to install Ubuntu 6.06.1 LTS on a Asus MB+P4 3.4 GHz+3 GB RAM.

I disconnected all the Hard disks and connected only the main SATA that I wanted to use for windows XP and Ubuntu. Below is the fdisk -l result:

> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38244   204796620    7  HPFS/NTFS
/dev/sda3           38245       50993   102406342+  83  Linux
/dev/sda4           50994       60801    78782760    5  Extended
/dev/sda5           50994       60673    77754568+   b  W95 FAT32
/dev/sda6           60674       60801     1028128+  82  Linux swap / Solaris


I installed windows on sda1, and created a primary partitian of 200 GB for windows software. I then added sda3 for ubuntu and defined sda6 as a swap area and sda5 as FAT32 to use for files that will be shared between windows xp and Ubuntu.

Windows worked fine, I then started the live CD and installed Ubuntu. I expected a message from the installer and GRUB load manager telling me about xp. No luck. After install, it rebooted to Ubuntu. Windows is completely inaccessible.

During startup, I pressed ESC during GRUB startup, and GRUB did not see windows XP.

All my data is safe since this is a new Hard disk and the other hard disks are disconnected, so I do not need to recover data. What am I doing wrong and how can I repair it.

I do not mind re-installing all if this is the way.

Any help will be greatly appreciated.

---

### Post by d3v1ant_0n3 on 2006-12-29
I have no idea about your problem, but can I just say that the typo in the thread title is the funniest I've seen all week:D

---

### Post by bulldog on 2006-12-29
Add a windows entry at your menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
gksudo gedit /boot/grub/menu.lst
```
Add the following entry at the bottom of your menu.lst
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
chainloader	+1
```

---

### Post by Naturally on 2006-12-29
> **d3v1ant_0n3 said:**
> I have no idea about your problem, but can I just say that the typo in the thread title is the funniest I've seen all week:D



:rolleyes: Fruedian slip. Should have been GRUB detests windows .... :)

---

### Post by Naturally on 2006-12-29
> **bulldog said:**
> Add a windows entry at your menu.lst

Thank you so much bulldog.

Problem solved and both OS's work fine alongside each other.

Thanks and God bless. =D> =D> =D> =D> =D>

---

