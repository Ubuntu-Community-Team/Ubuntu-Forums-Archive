---
title: "installing ubuntu 6.10 and grub to an external harddrive"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by presbp on 2007-01-24
Ok so I partitioned out my 300GB external harddrive to where I have my root  ( / drive) set to 11GB and my swap partition set to 270MB.  In the installer my internal harddrive in the drop-down menu says it is sda and the external drive is sdb.  The only thing I don't know what to do now is where to install GRUB.  I didn't format the drive because I have all of my backup files on my external drive and I don't want to install GRUB on my Windows internal hard drive and I don't want to install GRUB on the partition where I have my backup files.  So when it asks me where to install GRUB I chose (/dev/sdb2) and it told me GRUB returned a fatal error and couldn't install there.  
      Do I just have to choose /dev/sdb as the place to install GRUB if I don't want it on my internal drive?  I just did a clean reinstall of Windows XP Pro and just got all of my programs reinstalled and all of my files back on there.  So I do not want any trace of Ubuntu or GRUB on my internal drive and I would prefer not to have GRUB on the partition where my Windows backup files are.  
       One more question, when I had WIndows XP installed recently I partitioned the internal drive to allow 12 GB of it to be Ubuntu's.  My Windows got messed up so I had to format the drive and reinstall Windows completely.. but in the partitioner area it shows my internal harddrive as having like 180GBs of free space (I have a 250GB drive) and then it has 7 or so MBs of unallocated space.  Is that from where GRUB was installed last time??

Thanks you guys.  I really like the community support..  Help for Windows issues usually requires much more searching and getting half-answers from Microsoft knowledgebase.

---

