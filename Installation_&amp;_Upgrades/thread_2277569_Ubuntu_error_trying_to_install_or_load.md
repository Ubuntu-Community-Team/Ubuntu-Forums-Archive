---
title: "Ubuntu error trying to install or load"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by brian64 on 2015-05-09
I have created both a bootable CD and a USB drive and I am getting the error below.  The first time I tried, I made it to the screen where you can choose the "Something Else" option.  Not knowing what I needed from that screen, I looked for a way to "back up".  Not finding one, I just rebooted the computer.  Ever since, I get this error when I try to install or load Ubuntu.  Any Thoughts?

[IMG]http://i.imgur.com/11afKWm.jpg[/IMG]

---

### Post by dino99 on 2015-05-10
when a cdrom or usb installation is done , be sure that it has been well done: check the md5sum
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by brian64 on 2015-05-11
The installation was never done.  I get the error above.

---

### Post by ac7nj on 2015-05-11
I have seen this problem before: The root partition was full and the new update was not fully installed. If this is your problem reboot and you should have the option to select advanced. Once you select that option revert to a older recovery and log in as normal. If this works you will need to write down the failed file so you can remove it.

---

