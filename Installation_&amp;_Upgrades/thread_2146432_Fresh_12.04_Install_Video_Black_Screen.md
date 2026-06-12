---
title: "Fresh 12.04 Install Video Black Screen"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by aginzuj on 2013-05-18
I did a fresh install of Ubuntu 12.04 on an old Acer E360 with an Nvidia graphics chipset.  It ran fine from the CD prior to installation, but after the install completed all I get is a black screen when booting up.  I went to a terminal screen (ctl-alt-F2) and tried installing the nvidia-current driver but that didn't help.  The X server seems to be running.  This machine used to run 11.10 just fine.  

Should I go back and install 11.1?

---

### Post by aginzuj on 2013-05-19
This is now solved.  I added the following to /etc/modprobe.d/blacklist.conf

blacklist vga16f 
 blacklist rivafb  
blacklist rivatv  
blacklist nouveau  
blacklist lbm-nouveau  
blacklist nvidiafb  
blacklist nvidia-173  
blacklist nvidia-96

Then sudo apt-get install nvidia-current

Apparently the nvidia driver is incompatible with the nouveau driver.

I got this from [http://ubuntuforums.org/showthread.php?t=2014164&p=12069625#post12069625](http://ubuntuforums.org/showthread.php?t=2014164&p=12069625#post12069625)

---

### Post by jamesisin on 2013-05-19
Excellent news and nice sleuthing.  Be sure to mark your thread as solved.

---

