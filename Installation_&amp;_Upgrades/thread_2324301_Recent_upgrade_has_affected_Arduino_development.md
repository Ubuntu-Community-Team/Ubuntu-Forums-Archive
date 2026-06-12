---
title: "Recent upgrade has affected Arduino development"
date: 2016-05-12
forum: Installation &amp; Upgrades
---

### Post by biscayne2 on 2016-05-12
Hello,
         please forgive me if this is posted in the wrong place but right now I am a very unproductive Arduino developer. Ubuntu version is 12.04.1, Arduino IDE version is 1.6.5.
Until recently all was fine but when I tried to download a new version of my Arduino code this morning, it repeatedly failed, despite rebooting everything.

I applied 2 updates recently, details (from /var/log/apt/history.log) :

Start-Date: 2016-05-10  08:04:21
Commandline: aptdaemon role='role-commit-packages' sender=':1.136'
Install:
 linux-image-3.2.0-102-generic:i386 (3.2.0-102.142),
 linux-headers-3.2.0-102-generic:i386 (3.2.0-102.142),
 linux-headers-3.2.0-102:i386 (3.2.0-102.142),
 linux-headers-3.2.0-102-generic-pae:i386 (3.2.0-102.142)
Upgrade:
linux-headers-generic:i386 (3.2.0.101.117, 3.2.0.102.118),
linux-image-generic:i386 (3.2.0.101.117, 3.2.0.102.118),
linux-libc-dev:i386 (3.2.0-101.141, 3.2.0-102.142),
openssh-client:i386 (5.9p1-5ubuntu1.8, 5.9p1-5ubuntu1.9),
linux-headers-generic-pae:i386 (3.2.0.101.117, 3.2.0.102.118),
openssh-server:i386 (5.9p1-5ubuntu1.8, 5.9p1-5ubuntu1.9),
linux-generic:i386 (3.2.0.101.117, 3.2.0.102.118),
ssh-askpass-gnome:i386 (5.9p1-5ubuntu1.8, 5.9p1-5ubuntu1.9)
End-Date: 2016-05-10  09:23:22

Start-Date: 2016-05-12  06:56:39
Commandline: aptdaemon role='role-commit-packages' sender=':1.56'
Upgrade:
 icedtea-6-jre-cacao:i386 (6b38-1.13.10-0ubuntu0.12.04.1, 6b39-1.13.11-0ubuntu0.12.04.1),
 openjdk-6-jre-headless:i386 (6b38-1.13.10-0ubuntu0.12.04.1, 6b39-1.13.11-0ubuntu0.12.04.1),
 openjdk-6-jre:i386 (6b38-1.13.10-0ubuntu0.12.04.1, 6b39-1.13.11-0ubuntu0.12.04.1),
 icedtea-6-jre-jamvm:i386 (6b38-1.13.10-0ubuntu0.12.04.1, 6b39-1.13.11-0ubuntu0.12.04.1),
 openjdk-6-jre-lib:i386 (6b38-1.13.10-0ubuntu0.12.04.1, 6b39-1.13.11-0ubuntu0.12.04.1)
End-Date: 2016-05-12  07:00:46

and it seems to be after one of these that the problem began.

 I noticed that the 'RX' LED on the Arduino (MEGA 2560) board flashes about once every 4 seconds, which it did not do prior to the upgrades. The Arduino is connected via USB port /dev/ttyACM0.

I suspect that one of the updates has resulted in some system process continually accessing the port and this is interfering with the Arduino IDE's attempts to download via the same port.

I don't have a great deal of knowledge of the internal workings of Ubuntu (I am a real time programmer) but I suspect I will have to do one of the following:

1) find a configuration file that I can edit to stop some process accessing /dev/ttyACM0.
2) "roll back" the updates until I find out which one introduced the problem.

Any suggestions would be most welcome

TIA

Steve

Sorry if I wasted anyone's time. The problem had nothing to do with Ubuntu upgrades, it was an Arduino problem. I was trying to download a new version of my code post updates and erroneously concluded that it was the updates that caused the problem. Reverted to an old version of my code and it downloaded just fine. Just have to figure out why a c file that compiles OK upsets the downloader.

---

