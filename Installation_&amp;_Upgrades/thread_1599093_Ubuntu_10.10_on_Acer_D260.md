---
title: "Ubuntu 10.10 on Acer D260"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by cokebotle on 2010-10-17
I'm trying to install on my Japanese Acer D260, however the installation keeps hanging. After selecting my keyboard (Japan), the installation continues doing something until it says "Ready when you are" on the bottom of the window. But there is no button, or anything, and it just hangs. I don't have it connected to the internet, but I tried to set up my WiFi network, but it didn't seem to help.

What could be the problem? Thanks!

Edit: It seems like the installer hangs on the following part of the installation (been stuck with this as the last text for the past 20+ minutes) - 

ubuntu CRON[10848]: (root) CMD (   cd / && run-parts  - - report /etc/cron.hourly)

And this was installed by first connecting to my WiFi, and then running the installer.

---

### Post by edoardo on 2010-10-26
I suggest you re-download the iso and re-create the usb stick, allowing isolinux to format it

---

I have just installed Ubuntu 10.10 Maverick on a UK-spec Acer Aspire D260.
Installed from a usb stick, created in windows from the 10.10 desktop install iso 

decide to shrink the ntfs partition (sda3) and install in a sd5 ext4 within a logical partition, also left swap available .

All I tried worked out of the box
ethernet
wifi (proprietary driver)
sound out
trackpad included 2 finger scrolling 
suspend / resume (closing the lid).
fn keys for brightness/volume adjustment

not yet tried:
mic
webcam
card reader

---

### Post by m1k3_ on 2011-01-15
Hi there! I tried to install Ubuntu NE 10.10 but it seems like it doesn't work. It run the Live USB but, after select everything, when it start to install just stop, and do nothing. Am I doing something wrong?

I post it here because is the same minis-model. :-P

Thanks! I'm so grateful for all the help you can give :-)

---

