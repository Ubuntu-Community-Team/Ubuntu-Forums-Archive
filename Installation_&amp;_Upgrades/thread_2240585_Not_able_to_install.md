---
title: "Not able to install"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by mahesh6 on 2014-08-21
Hi,


I have a bootable ubuntu usb, I am able to boot my laptop with this, but while installing the same on my laptop after the screen asking for options to install on top of windows or delete windows and install ubuntu its showing a black screen for a fraction of a second and restarting the system.

Please help me to get though this issue.

Thanks,
Mahesh

---

### Post by mastablasta on 2014-08-21
did you check to make sure the downloaded image is good? do you plan a dualboot? can you boot into the operating system (the "try it" option) and do installation from there?

also read this: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by mahesh6 on 2014-08-21
Hi mastablasta,

I am able to boot, I am able to use 'try' and successfully and able to work with it. I have tried to install from there but same things happening, its restarting the system after the screen for instillation options to select.


Thanks,
Mahesh

---

### Post by mastablasta on 2014-08-21
assuming the ISO download is good as per these checks: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

can you go into live session and launch boot repair tool. then create the boot info summary and post that here. also can you tell us what GPU chip you have? do you have hybrid graphics (e.g AMD/Intel, Intel/nVidia)? at this point we have no information from you on BIOS setup and hardware. usually when this happens live boot is also not possible or presents itself with blank screen.

A few things you could try: [http://ubuntuforums.org/showthread.php?t=2184839](http://ubuntuforums.org/showthread.php?t=2184839) disabling various windows only functions in UEFI

a few more: [http://askubuntu.com/questions/336824/black-screen-when-trying-to-install-ubuntu-12-04-2-on-asus-x502c](http://askubuntu.com/questions/336824/black-screen-when-trying-to-install-ubuntu-12-04-2-on-asus-x502c)
[http://askubuntu.com/questions/317184/screen-goes-blank-when-installing-ubuntu-on-asus-zenbook-ux31a](http://askubuntu.com/questions/317184/screen-goes-blank-when-installing-ubuntu-on-asus-zenbook-ux31a)

main article about UEFI: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I just give so many info since with limited information you gave it is hard to pinpoint where the issue is.

---

