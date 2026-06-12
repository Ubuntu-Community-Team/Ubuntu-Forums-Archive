---
title: "Install new 18.04 over 14.04 dual boot with w7"
date: 2019-10-11
forum: Installation &amp; Upgrades
---

### Post by hiloguy on 2019-10-11
I have well-endowed Dell D630 with 14.04 on the the 500 Gb HDD installed in the CD drive bay, and W7 on the main HDD, a 125 Gb SSD.  I want to upgrade the 14.04 to 18.04 and would like to install 18.04 fresh from a USB stick (ready to go).  If simply do the install selecting "replace existing OS," will the computer still dual boot when I'm done?  And if not, how do I do this?

---

### Post by yancek on 2019-10-11
Not sure how familiar you are with Linux drive/partition naming conventions.  You would first need to determine on which drive and which partition your current Ubuntu is installed.  You can get that info by booting the current install and from a terminal, enter the following command which should show all drives attached with partitions:

```
sudo fdisk -l
```

You should see multiple drives and partitions.  The ones with the ext4 filesystem will be your Ubuntu.  If you boot the current Ubuntu, you should be able to determine on which partition it is installed by using the df -h command from a terminal.  Tat would be the partition you want to install to.  If you are not sure, you could post the output of the above commands here and someone should be able to advise you.

I've never used the 'replace existing OS' option so I'm not sure that would work.  Usually best in these circumstances to use the manual (Something Else) option.  More control.

---

### Post by mörgæs on 2019-10-12
I run some more or less similar Latitude D6** and D8**. They are great hardware but a lighter Buntu (say Xubuntu or Lubuntu) is recommended.

---

### Post by Frogs Hair on 2019-10-12
I would first set the boot priority in the bios and try booting from the live DVD or USB. If the live option works including internet boot Windows go to disk management  delete the operating system and partition so the space is unallocated . Next ,  reboot with DVD or USB inserted and install on the unalloacated space. This had always worked on both my computers while using Win 7.

---

