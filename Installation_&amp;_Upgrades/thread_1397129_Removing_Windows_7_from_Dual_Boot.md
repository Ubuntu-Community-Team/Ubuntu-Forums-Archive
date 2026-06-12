---
title: "Removing Windows 7 from Dual Boot"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by mikeody on 2010-02-02
Am running Karmic and Windows7 dual booting with separate hard drives.
I want to remove Windows 7 and leave Karmic on it's single drive.
I am concerned that I will cause a boot problem if I just 'unplug' the Windows 7 drive.
Can anyone help please ?

---

### Post by raymondh on 2010-02-02
where is GRUB2 installed? 

if grub2 is installed in the Karmic HD, and you have problems after removing the windows HD, you can try to update grub2.  In terminal,

```
sudo update-grub2
```

if grub2 is installed in the windows HD, you will then have to re-install GRUB2 in the MBR of the Karmic HD.  [Instructions here, number 13]("http://ubuntuforums.org/showthread.php?t=1195275").

Regards,

Raymond

---

### Post by mikeody on 2010-02-03
Sorry all,
I have asked this question before and got plenty of advice - thanks - must be going mad !
For now I will show the thread as solved. Thanks again.

---

