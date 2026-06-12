---
title: "Cannot Reformat Drive for Dual Boot"
date: 2014-01-06
forum: Installation &amp; Upgrades
---

### Post by tomasrey88 on 2014-01-06
Hi,

I have a virus on my computer so I have to reformat the drive and install a Ubuntu/Windows & dual boot. However, the problem is that when I insert my Windows 7 upgrade disk, it wants to reformat and reinstall Windows 7 only in the Windows partition. It won't recognize and reformat the Ubuntu partitions. What should I do? 

I'm not very tech savvy, so detailed step by step instructions would be most appreciated. 

Thanks,

---

### Post by nerdtron on 2014-01-07
You don't have to format the partitions of Ubuntu. Just reinstall windows as usual and let it format the Windows partition. Once you boot into windows 7 open the disk partition manager and you'll see there the partition for ubuntu. Right-click on the partition and choose format.

Also, you don't have to format the partition on windows if you are going to install ubuntu again. After installing windows 7, run Ubuntu live mode and start the installation, ubuntu will detect all you partitions and you should choose the correct partition where you want to install ubuntu.

---

### Post by tomasrey88 on 2014-01-07
Thanks! Doh! (I should've realized that, but didn't. I am still in that Windows paradigm and did not realize that Ubuntu could reformat when reinstalling, too.)

---

### Post by Bucky Ball on 2014-01-07
Windows can reformat and partition when installing, too. 

You can boot from a LiveDVD or USB and wipe the whole drive using Gparted if you want, then start again. 

Just to clarify, what do you have on your computer at the moment? With the Win installer, you should see the existing Win install. Simply delete it and install Window to it again. This leaves Ubuntu intact (if it's installed).

If Ubuntu is already installed, then once Win7 is installed, boot from the Ubuntu Live media, open a terminal and:

```
sudo grub-install /dev/sda
```

Reboot and that should show you a selection of Win and Ubuntu to boot. Should. If Ubuntu not installed, install Win then install Ubuntu.

(PS: Partitions need to be unmounted to reformat. That's why running from a Live USB or disk is the go.)

---

