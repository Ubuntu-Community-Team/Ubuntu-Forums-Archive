---
title: "windows 10"
date: 2016-03-20
forum: Installation &amp; Upgrades
---

### Post by wyndlass on 2016-03-20
i'm trying to dual install 15.10 x64 on my hp pavilon g7-2017us that was upgraded to win 10 from 7 but the ubuntu installer keeps wanting to format my hdd instead of giving me the option to install next to windows. using live flash drive made with nettbootin. what can i do to fix this? i have the core i3 6 gb ram and about 500 gb hdd. until amazon makes a linux specific kindle app i still need windoze for that. i tried the one thru wine but that quit letting me read my books. kept giving an error and closing down the app. i don't recall the exact error now.

---

### Post by yancek on 2016-03-20
Probably because you do not have any unallocated space on the drive and have windows using up the entire thing.  How many partitions do you have?  Are you using MBR or UEFI?  windows 10 defaults to UEFI but if it is an upgrade it may be MBR.  You could boot the Ubuntu flash drive and select the Try Ubuntu option.  When you get to a Desktop, open a terminal and run this command:  sudo gparted

Post the image output here.  Or you could run:  sudo fdisk -l and post that output here.  That's a Lower Case Letter L in the command.  If you don't have any unallocated space, you will need to shrink the largest partition and the best way to do that is from windows Disk Management.

---

### Post by Edison_James on 2016-03-20
Regarding the kindle app. You can read ebooks using the  Calibre app., it's a good app but it won't let you read books protected by DRM, (digital rights management technologies) Which in my case is over 80% of my kindle content. So I stay with windows for my ebooks.

---

### Post by jim_deadlock on 2016-03-21
> **Edison_James said:**
> Regarding the kindle app. You can read ebooks using the  Calibre app., it's a good app but it won't let you read books protected by DRM, (digital rights management technologies) Which in my case is over 80% of my kindle content. So I stay with windows for my ebooks.

Get the DeDRM plugin for Calibre: [https://apprenticealf.wordpress.com/2012/09/10/calibre-plugins-the-simplest-option-for-removing-most-ebook-drm/](https://apprenticealf.wordpress.com/2012/09/10/calibre-plugins-the-simplest-option-for-removing-most-ebook-drm/)

---

### Post by HermanAB on 2016-03-21
You need to defragment and resize the Windows partition first, so that there is an empty partition for Ubuntu to install onto.

---

### Post by wyndlass on 2016-03-27
```


ubuntu@ubuntu:~$ fdisk -l
fdisk: cannot open /dev/ram0: Permission denied
fdisk: cannot open /dev/ram1: Permission denied
fdisk: cannot open /dev/ram2: Permission denied
fdisk: cannot open /dev/ram3: Permission denied
fdisk: cannot open /dev/ram4: Permission denied
fdisk: cannot open /dev/ram5: Permission denied
fdisk: cannot open /dev/ram6: Permission denied
fdisk: cannot open /dev/ram7: Permission denied
fdisk: cannot open /dev/ram8: Permission denied
fdisk: cannot open /dev/ram9: Permission denied
fdisk: cannot open /dev/ram10: Permission denied
fdisk: cannot open /dev/ram11: Permission denied
fdisk: cannot open /dev/ram12: Permission denied
fdisk: cannot open /dev/ram13: Permission denied
fdisk: cannot open /dev/ram14: Permission denied
fdisk: cannot open /dev/ram15: Permission denied
fdisk: cannot open /dev/loop0: Permission denied
fdisk: cannot open /dev/sda: Permission denied
fdisk: cannot open /dev/sdb: Permission denied
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ fdisk -l

```




this is what i get, from fdisk.can't figure out how to get the screen shot to display in the message.

---

### Post by Rocky_Bennett on 2016-03-27
If I were the OP, I would download an ISO of Windows 10 then I would do a clean install of Windows 10. That would allow complete control of the hard drive and allow for a very easy partition set up. Without a clean install of Windows 10, Microsoft has that hard drive locked.

---

### Post by LostFarmer on 2016-03-27
Try with root privliages ' sudo fdisk -l '

---

### Post by wyndlass on 2016-04-01
i'll try that. thanks lostfarmer.

---

### Post by slickymaster on 2016-04-01
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by wyndlass on 2016-04-10
i decided to just format and dedicate the whole drive to willy. thanx guys.

---

