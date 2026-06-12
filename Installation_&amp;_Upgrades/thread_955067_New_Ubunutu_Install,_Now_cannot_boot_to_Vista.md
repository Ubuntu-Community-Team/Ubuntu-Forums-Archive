---
title: "New Ubunutu Install, Now cannot boot to Vista"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by wrwarwick on 2008-10-21
I just finished installing ubuntu on a second hard drive, and now I am unable to access Vista. While installing ubuntu, during step 7 I selected to have grub installed on the disk with Vista - I am wondering if this completely wiped the Vista boot information from the drive.

When grub does load I can select Vista goes blank for about a second and then grub comes back up. I have tried searching but cannot seem to find anything on this issue.

Thanks for any help.

---

### Post by wrwarwick on 2008-10-21
Update - I ran a repair on Vista and I can now boot into windows, but I have no grub loaded. The boot process goes straight into windows. Also, in windows it does not recognize the other hdd, although I can see it in computer management.

---

### Post by Ng Oon-Ee on 2008-10-21
I'll start from the non-recognition of the hard drive, the reason for this is that your hard drive is formatted to ext3 instead of fat/ntfs. You can google for various tools which allow a windows PC to access an ext3/ext2 partition/hard drive.

Which leads me to my second point, is this a separate hard drive or a separate partition? I've only worked with single hard drive/multi-partition systems, and in my experience GRUB will by default add a chain-loader to load Vista/XP up. Perhaps, since your Vista now works, you could retry the install with default options for the GRUB part of it?

---

### Post by louieb on 2008-10-21
Need a couple of things in order to trouble shoot.

1st  the partition table
open applications>accessories> terminal
copy and paste the output of
```
sudo fdisk -l
``` lowercase L at the end 

2nd the GRUB configuration file. 
In the Places menu find your Ubuntu install a paste the content of [B]
 /boot/grub/menu.lst[/B]

See you just altered the MBR to boot Visa. You can do the above from the Ubuntu live CD.

---

### Post by wrwarwick on 2008-10-21
Thanks for all the quick help - but it seems to be working now. After I was able to boot back into Vista (and reapply the cracks - stupid activation!) I installed the EasyBCD program and followed one of the guides online. I am now able to boot into both Vista and Ubuntu!

---

### Post by Ng Oon-Ee on 2008-10-21
Glad to hear that. Cheers :)

---

