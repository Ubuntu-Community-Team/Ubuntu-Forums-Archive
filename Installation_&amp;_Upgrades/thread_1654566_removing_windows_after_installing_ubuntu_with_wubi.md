---
title: "removing windows after installing ubuntu with wubi"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by akshatgoel on 2010-12-28
Hi all,

I just installed Ubuntu from Windows using wubi.exe.

Now, i wanted to remove windows from my system completely, and clean my startup.
My startup currently shows me the options Windows 7 and Ubuntu.

Please help me out.

Thanks
Akshat Goel

---

### Post by Rubi1200 on 2010-12-28
Hi and welcome to the forums :)

I am not sure I understand what you want to do.

> I just installed Ubuntu from Windows using wubi.exe.
Great, I hope you enjoy trying it out :)

> Now, i wanted to remove windows from my system completely, and clean my startup.
If you remove Windows from your hard-drive, you will also remove Ubuntu.

I assume this is not what you want?

You currently have Ubuntu installed inside Windows. If you would like to migrate the Wubi install to its own partition on the hard-drive, see here:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by akshatgoel on 2010-12-28
Now is there any way so that i can remove Windows..but still keep Ubuntu? 
If this is not possible then please tell me why it is not?

---

### Post by szrobert on 2010-12-28
Hi. The best thing to do, IMHO, is to reinstall ubuntu (from an usb stick for a fast install). But ... if you want to keep the actual instalation then ... boot from the ubuntu installation disk, go to system/admin/gparted and delete the windows partition, enlarge the ubuntu partition then reboot computer. After this step, is a good idea  to make from command line an sudo update-grub2 .... in this way the grub will know that is no more an windows os installed

---

