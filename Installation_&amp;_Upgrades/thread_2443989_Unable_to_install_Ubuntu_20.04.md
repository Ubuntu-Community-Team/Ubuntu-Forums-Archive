---
title: "Unable to install Ubuntu 20.04"
date: 2020-05-23
forum: Installation &amp; Upgrades
---

### Post by prasadchalasani2 on 2020-05-23
[ATTACH=CONFIG]285970[/ATTACH][ATTACH=CONFIG]285971[/ATTACH][ATTACH=CONFIG]285969[/ATTACH]

Hi, I'm unable to install Ubuntu 20.04. Problem occurs when installing bootloader. I'm attaching the images of occurred error.

Please help me.

---

### Post by dino99 on 2020-05-23
is /dev/sda been previously formated ? which kind of installation is it ?

 [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by yancek on 2020-05-23
There are a number of reasons you could get that error but it won't be possible to help without more information.  Start by indicating the manufacturer and age of the  computer.  Also, does or did this machine have any other OS installed and if so, what was it?  Which installation option did you use?  You don't indicate any other OS so did you use the Erase disk and install Ubuntu option?

---

### Post by prasadchalasani2 on 2020-05-29
Thanks for the replies. I kinda busy with work sorry for delayed response . It's Lenovo G580 2014 with a ssd wd 240gb green and 500gb hdd. Previously solus 4 was installed and I messed up with boot 000 sector I think and  I do not know exactly what I have done. I tried to install a fresh ubuntu 20.04 with option Erase entire disk. 

Please help me
Thanks

---

### Post by yancek on 2020-05-29
In the first image, you show and EFI partitiion which is mounted at /target/boot, that's wrong as it needs to be /boot/efi as the mount point.
You root filesystem partition is mounted at /target which is also wrong, it should be / so the first thing to do is to change those mount points or try to reinstall with the correct mount points.

---

