---
title: "Can't boot to live cd, corrupt video"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by Gaelic Vyk on 2008-07-31
Hi everyone, I'm having problems with my new computer booting into ubuntu. I've tried 7.04, 8.04, and 8.10alpha3. What happens is this: I get the ubuntu boot menu from the cd, select boot to the live cd, it does its progress bar thing, and then I get evil red and green snow all over the screen. It does this with all 3 versions I've tried. I even installed 8.04 inside windows and tried booting to it with the same results. 

Computer specs:
EVGA 650i Ultra mobo, no onboard video, all bios settings stock
Intel Q6600 proc
2GB ram
nvidia 7600gs vid card, dual monitors
80GB hdd

Any help would be appreciated! :confused:

---

### Post by Sef on 2008-07-31
Have you tried installing with the alternate cd?  (Just click the box below [Start Download]("http://www.ubuntu.com/getubuntu/download").)  The alternate cd has a text-based and is fairly easy to install.  The only tricky part could be the manual partitioning if you need to do that.

---

### Post by Kevbert on 2008-07-31
Please perform a memory test using the menu item on one of the CDs.  Even though windows may seem to work (but you may occasionally get unexpected problems) its possibly a memory problem.
The other thing is, are you performing a hash check on your downloaded ISO files, burning at the slowest speed.  What software are you using to burn the CDs ? The recommended software for windows is [[COLOR="Red"]Infra Recorder[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto").  After you need to perform a CD check via its menu.

---

### Post by Gaelic Vyk on 2008-08-01
I did a memtest and actually found a bad stick. Still didnt fix the problem though. I installed it inside windows and rebooted to ubuntu. When it booted to the corruptness I switched it over to a command line, apt-get update, got the nvidia driver, xserver reconfigure, rebooted, still corrupt. looked at the xorg.conf with nano and there's still not even a video driver listed. no nvidia, no vesa, nothing. 

Any more suggestions?

---

### Post by Dynamo_Joe on 2008-08-01
When booting from the LiveCD, press "F4" and it will bring up  additional boot options. Select "Boot in safe graphics mode" and press enter. 

This will get you into the graphical environment. Once you have finished your installation, you can then tinker with the Nvidia drivers (or try to install them). 

Personally, on my GF6200A card, I just used the default drivers as I don't need any fancy desktop effects or play games anymore (sorry, old age is catching up with me fast). 

Have fun!

---

