---
title: "re-install OS on dual boot setup"
date: 2014-05-16
forum: Installation &amp; Upgrades
---

### Post by windowsfree on 2014-05-16
I have a dual boot setup, with Ubuntu 14.04 and Win 7.  If I want to reinstall Ubuntu, is it easiest to go into Windows, format the partition that linux and the swap file are on and reinstall via live USB or is there an easier way?

Thanks!

---

### Post by oldfred on 2014-05-16
Do not use use Windows, use gparted. Only use Windows for shrinking Windows NTFS partiiton and then immediately reboot so it can run chkdsk and update to its new size.

Make sure you have backed up everything you want to save.

Be sure to install Windows boot loader back into MBR first,or you will not be able to boot as grub is in MBR. Best to have a Windows repair CD or flash drive.

If just reinstalling, use Something else and choose the existing / (root) as your new / partition. If you want to totally erase then tick the reformat option.

So not use any of the auto install options, unless you have deleted partitions and have unallocated space. And even then I suggest Something Else. 

There is an issue on over installs, where it will say overwriting Ubuntu, but erases entire hard drive. Only Something else lets you totally control partitions.

---

### Post by pfeiffep on 2014-05-16
I think going into Windows is not required. 
You should be able to install via live USB and choose something else ... this should provide you the opportunity of choosing to overwrite your Ubuntu 14.04 existing installation. Be certain to choose the correct place for Grub install.

---

### Post by windowsfree on 2014-05-16
Thanks, I hope to do this on the weekend.

---

### Post by windowsfree on 2014-05-19
I did as you suggested pfeiffep and all went well.  Thanks.

---

