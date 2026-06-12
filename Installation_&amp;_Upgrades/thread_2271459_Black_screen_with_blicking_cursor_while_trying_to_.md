---
title: "Black screen with blicking cursor while trying to boot up"
date: 2015-03-30
forum: Installation &amp; Upgrades
---

### Post by devraj3 on 2015-03-30
Hi,
I am relatively new to the forums. Here is the problem:
I had Win7 ultimate edition running on core 2 duo with an nVidia 9300M GS GPU. I had Ubuntu Lynx running on top of it. Since my windows got corrupted (it just wouldn't work and act all jittery. Some dlls went missing I suppose :p ), I have been running Ubuntu only from the bootloader. Yesterday, I tried removing the entire arrangement and install Ubuntu 14.0 as the sole OS. Created a bootable USB stick and tried booting from the BIOS. That was the first time that the screen got stuck at the black screen with the blinking cursor. I later realized that the image was for AMD so I downloaded one for Intel and tried the same but it just won't get past the black screen. I tried various versions of Ubuntu, upto version 10 and tried various USB sticks but to no avail. Now, the laptop just wouldn't start-up even without any bootable media present. I tried removing all USB and drives from the list of boot-order and it still wouldn't load. I basically tried everything but to no avail. Any help would be massively appreciated. :(

---

### Post by Bashing-om on 2015-03-30
devraj3; Hi ! Welcome to the forum ..

Appears now that there is no longer any boot code for bios to hand off to. I think it is best to back up, regroup, and start all over.
I will bet that it is a graphics card issue... Once you have a verified liveDVD(USB) try and boot the install media to "try ubuntu" with the 'nomodeset' boot parameter:
See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter

verify the .iso image file;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

and verify the burn:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

With this known good medium in hand
[INDENT][INDENT][INDENT]we make forward progress
[/INDENT][/INDENT][/INDENT]

---

