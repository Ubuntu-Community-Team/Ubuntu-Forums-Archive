---
title: "Daul Boot - Error no Such Device - Setting Partition To"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by eljc2 on 2015-01-04
I have Xubuntu and Windows 7 dual boot. When I try to boot Windows I get the following message:
[I]
Error: no such device [long number]

Setting partition type to 0x7

Press any key to continue...[/I]

Windows 7 then loads without problems. Is there a way of stopping this error message? Perhaps making the grub point to the right partition first time around? If you have seen this message before, please direct me to the appropriate thread.

---

### Post by yancek on 2015-01-04
More information is needed and you can get it by booting Xubuntu and going to the site below and downloading boot repair and selecting the option to Create Bootinfo Summary and posting that output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

> *Error: no such device [long number]*

That means it is looking for a UUID which doesn't exist.  Use sudo blkid in a terminal to find the correct UUID for whichever partition it is referring to.  That info will be in the Bootinfo Summary.

---

### Post by eljc2 on 2015-01-04
Thanks for the reply, yancek

My bootinfo summary is here

[http://paste.ubuntu.com/9673493/](http://paste.ubuntu.com/9673493/)

---

### Post by yancek on 2015-01-04
Your actual windows filesystem is on the sda1 partition.  If you look at the bootinfo output you will see the UUID listed under the blkid output for that partition is:

> /dev/sda1        8ADED77DDED7604D                       ntfs  

If you then scroll down to the contents of the grub.cfg file, you will see the entry for windows on sda1 has a UUID of:  

> F430478C304754B0

If the first UUID number above is the one you see on booting, replace it with the second one in the grub.cfg entry for windows and reboot to see if you get the error.  You actually might try just running:  sudo update-grub before doing this to see if that helps.

---

### Post by fantab on 2015-01-04
Yancek could be right... it could be the case of corrupted UUID entry... 
If editing UUID does not help, then perhaps [reinstalling Grub]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") is a good idea.

---

### Post by eljc2 on 2015-01-07
update-grub seems to have done the trick.

Thanks!

---

