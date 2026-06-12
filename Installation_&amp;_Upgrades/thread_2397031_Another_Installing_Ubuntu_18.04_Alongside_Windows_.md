---
title: "Another Installing Ubuntu 18.04 Alongside Windows 10 - Error Grub Failed"
date: 2018-07-24
forum: Installation &amp; Upgrades
---

### Post by roadrawts on 2018-07-24
I can't get Ubuntu to install to dual boot along with Windows 10 so that GRUB is working.  I've tried both Ubuntu 18.04 and then 16.04.  In the 16.04 install it stated that it was installing GRUB.  And yet it's not there.  I'm running on an Acer Aspire E15.  I've changed from UEFI to Legacy but Legacy states no OS to load.  UEFI just loads Windows 10.  Every time I find a 'fix' on the internet the instructions don't match my version of gParted or anything else. I'm using the latest version of gParted.  Getting very frustrated.  Would really appreciate some help.  
At least in your post you got the message the Grub Failed.  I don't get that.

---

### Post by jeremy31 on 2018-07-24
Moved to it's own thread, post results for ```
sudo parted -l
```

---

### Post by yancek on 2018-07-24
Acer requires you to set 'trust' in the BIOS to install another OS.  Check your user manual or look for it online to find out how to do that.  Read the Ubuntu documentation at the link below on dual booting windows/Ubuntu UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-07-24
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

You should also update UEFI from Acer.

---

### Post by roadrawts on 2018-07-24
Followed the directions above.  Will try and reinstall in the morning and see if it works.  Thanks for the help so far.

---

