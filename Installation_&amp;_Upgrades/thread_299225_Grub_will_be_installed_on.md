---
title: "Grub will be installed on?"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by Ptah on 2006-11-13
First off hello everyone :-D ! My system contains (2) 160 sata hard drives raided together and (1) 160 another is being dedicated for ubuntu.  Where do I install Grub?   The default boot location is hd0 but I know this can not be correct based on a previous try. 

Just add additional information to help:

/dev/sda and /dev/sdb are my raided drives with windows xp
/dev/sdc is my ubuntu dedicated drive

I am very frustrated w/ this whole process.  I want to switch to linux but just cant get this right!

---

### Post by jpkotta on 2006-11-13
I'm not exactly sure how grub decides which drive to install on by default, but you can explicitly tell it which ones to install on.  See [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Ptah on 2006-11-13
Ok, my problem is how do I know which hard drive corresponds to hd0, hd1 or hd3.  I could be wrong but if I am please someone correct me sda=hd0, sdb=hd1 and sdc=hd3 or is mbr=hd0, sda-hd1, sdb=hd2 and sdc=hd3.  I am starting to see that ubuntu is not for new xp converts without taking a full 4 credit course!

---

### Post by Ptah on 2006-11-14
Last night I continued with the install allowing grub to be installed in the default location of hd0. Upon rebooting, pressing f12 for boot menu and selecting Ubuntu kernal.  I was promptly greeted with Error 25 in which I have no clue what is.  I am currently searching thr forums for answers but If anyone has dealt with please let me know what it is and how to correct it if possible.

---

### Post by jpkotta on 2006-11-14
As it says in the wiki page, the file /boot/grub/device.map gives the mapping from grub names to kernel names.

---

### Post by pr3@ch3r on 2006-11-14
you are correct in your assumption. Though with a raid Im not positive but I'll assume it will still be on sda. With SATA and SCSI your drives are associated as sd* and not hd* as hd* is reserved for ide type drives only. I'm not sure what Ubuntu Grubs install problem is but my windows box is currently jacked up and I install grub/rhe on a regular basis (I work at a Webhosting data center). This install is weird, and retarded. You would have normally said SDA on the install and you can try to go back and repair it, but I dont think it will work as mine has yet to but you can prove me wrong ;)

---

### Post by Ptah on 2006-11-14
I went back and repaired the mbr through recovery, then tried to reinstall again and I get nothing now.  It will not boot into ubuntu just windows.  I am starting to think its a setting somewhere that is keeping me from installing another OS.  I know it sound dumb but what else can it be.  I tried many different distros all with the same result.  Its off to the geek squad, maybe they can install it.

---

