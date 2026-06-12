---
title: "HP Proliant FANs"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by pambuhl on 2005-03-04
Hello,
Did anybody install Ubuntu on one of the Proliant DLxxx servers and found a way to reduce the FAN noise (I know it depends on the loading of hpasm)?
I tried to use the script for Debian but it is only working for 2.4 kernels.


Thanks

Patrick

---

### Post by bist on 2005-05-28
I have the same problem. I tried to convert the rpm hpasm driver to a deb package but it didn't work..

It seemed to install but the driver does not load

---

### Post by magicfab on 2006-09-18
Have you had any luck with this ?

I tried and succeeded installing HPASM via the rpm to deb script at:
[http://debian.catsanddogs.com/component/option,com_remository/Itemid,27/func,fileinfo/id,3/](http://debian.catsanddogs.com/component/option,com_remository/Itemid,27/func,fileinfo/id,3/)

I read somewhere that the fakeroot package is needed.

One the script ended, I followed instructions to install some missing packages, but hwen trying to start hpasm after that I get:
exec: 1: 10: not found

I am trying this on a Proliant ML370 system with Edgy Eft (6.10) knot 3.

Thanks for any pointers..! I really want that fan noise down and some way to check on the system' s health.

---

### Post by jadajada on 2006-10-05
Have you figured this one out? I am getting the same error. I am on Debian Sarge though, but the problem seem to be the same...

---

### Post by Pixxa on 2007-04-19
Sorry to bump old topic, im having this error too now :( any info how to solve it?

---

### Post by Ashfire908 on 2007-08-20
On the Compaq ProLiant ML370 G2, you can change the fan speed down. Depending on your BIOS firmware version, the settings will be low and normal or normal and high. the default is the highest setting (i recommend upgrading the bios as it adds more settings and one of the two updates i did made the array init twice as fast). i have not found a way to slow the fan via Ubuntu. i recommend having arrayprobe and/or cpqarrayd because on the lower setting I've gotten overtemp warnings on the array, but it's most likely due to the fact it runs in a very small room.

EDIT: found a related topic: [http://ubuntuforums.org/showthread.php?t=218909](http://ubuntuforums.org/showthread.php?t=218909)

---

