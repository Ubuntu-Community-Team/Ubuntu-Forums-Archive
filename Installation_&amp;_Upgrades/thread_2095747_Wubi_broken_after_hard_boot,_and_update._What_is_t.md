---
title: "Wubi broken after hard boot, and update. What is the culprit?"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by rylangrayston on 2012-12-17
I was in Ubuntu freshly updated 12.?? (wubi install in windows 7) 
ubuntu froz... i hard booted and now at start up if i select ubuntu i get :
Try (hd0,0) : NTFS5; No wubildr
Try (hd0,1) : NTFS5: error: "prefix" is not set.

then I am dumped into grub prompt.

I did chkdsk /r  from windows 
didnt find anything but an error in an old video file.
and windows has done a clean shut down.

same errors occur 

In windows both my root.disk and root.swap files are in the ubuntu\disks\   dir.
one thing i notice is that Ubuntu\disks\boot\grub\   is completely empty including hidden files.

un like many installs I installed wubi on a different partition than my windows drive c
Its installed on drive E 

What can i try next?

I have been through the following form already ... and some others
[http://ubuntuforums.org/showthread.php?p=10180438](http://ubuntuforums.org/showthread.php?p=10180438)

---

### Post by bcbc on 2012-12-17
The \ubuntu\disks\boot\grub directory is always empty - it's an artifact from an older release.

If you've run chkdsk on the drive where you installed, then you probably need to fsck the root.disk and this can only be done from a live CD/USB. [https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)

---

