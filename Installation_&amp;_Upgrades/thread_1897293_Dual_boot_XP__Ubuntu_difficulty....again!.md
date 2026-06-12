---
title: "Dual boot XP / Ubuntu difficulty....again!"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by zipher on 2011-12-18
Hi there, Please can anyone help me sort out my difficulty.... bearing in mind that I cannot write or burn discs on my current facility, and that the only .iso image tool with graphical Gparted on it I own, is on a previously made Hardy Heron disc.

My system is suppposed to boot XP and Ubuntu. When I reloaded XP from microsift disc into its original slot on my partition table, I lost the ability to boot into the linux system.
I have tried chaning boot flags to various places but this is not helping.

I feel that careful editing of the windows Bootloader file may help... but how?

The current Windows Boot.ini file is as follows:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```


The boot flag is currently attached to the NTFS partition in which XP resides.

My partition table has two basic partitions, one as described above and the other is subdivided into several of various kinds for data storage, swaps,and general experimentation purposes.

Is there a windows tool with which I can display partition information?

Any other assitance greatfully received.

Thanks

---

### Post by mikewhatever on 2011-12-19
Perhaps you could try EasyBCD. [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

---

### Post by james2b on 2011-12-19
You may just need to re-install the grub 2 boot loader so you then have the choice for XP or Linux. That Easy BCD tool is only used for the Windows Vista and 7 booting process. There are some sites that show grub2 help [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
and here too; [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by darkod on 2011-12-19
You never mentioned which version of ubuntu are you running exactly?

It's much better to install grub to the MBR of the disk instead of trying to boot ubuntu with the windows bootloader. And don't move the boot flag around, windows depends on it to boot correctly. It needs to be on the XP partition.

But since you only have Hardy cd, installing grub on the MBR might not work using that cd because the recent versions of ubuntu come with grub2 and Hardy doesn't.

Another option is to create a bootable usb stick with the iso of the same version you have installed. If your computer can boot from usb you can boot in live mode and install grub to the MBR.

---

