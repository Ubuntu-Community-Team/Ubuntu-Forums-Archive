---
title: "Install Ubuntu on an Acer Aspire 7520"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by thommy on 2007-09-30
Hello, before installing ubuntu on the above mentioned laptop I wanted to test the live-CD first, but it failed! Instead starting the X-server I received the following syslog messages:
ubuntu kernel: 1123600 calling WQBA, and: wmi_add device=c1f01c00. After that the screen changed to the terminal mode. I typed 'startx'. After having typed 'ENTER', the following messages came:
xauth creating new authority file /home/ubuntu.serverauth 8524 (twice!)
X warning process set to priority -1 instead of requested priority 0
Fatal server error
server is already active for display 0. If thist server is no longer running, remove /tmp.X0-lock and start again.
Has anybody an idea, what is going wrong, and is it possible to install Ubuntu anyway?:confused:
Thanks for help in advance. Greetings, thommy

---

### Post by overdrank on 2007-09-30
> **thommy said:**
> Hello, before installing ubuntu on the above mentioned laptop I wanted to test the live-CD first, but it failed! Instead starting the X-server I received the following syslog messages:
ubuntu kernel: 1123600 calling WQBA, and: wmi_add device=c1f01c00. After that the screen changed to the terminal mode. I typed 'startx'. After having typed 'ENTER', the following messages came:
xauth creating new authority file /home/ubuntu.serverauth 8524 (twice!)
X warning process set to priority -1 instead of requested priority 0
Fatal server error
server is already active for display 0. If thist server is no longer running, remove /tmp.X0-lock and start again.
Has anybody an idea, what is going wrong, and is it possible to install Ubuntu anyway?:confused:
Thanks for help in advance. Greetings, thommy

HI and welcome, could you give us some specs on the system like cpu, memory, video card? Also you may want to look at these links to check how the cd was burned ( if indeed you burned the cd) and to run a checksum on the cd. 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Pumalite on 2007-09-30
Try the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'

[http://ubuntuforums.org/showthread.php?t=545401](http://ubuntuforums.org/showthread.php?t=545401)

---

### Post by thommy on 2007-09-30
Hi, here are the infos of the hardware:
CPU: AMD Athlon dual core 64bit
RAM: 1024 MB
Harddisk: 160GB
Graphic-card: nVIDIA GEFORCE GO 7800.
The DVD is a supplement of the german magazine 'easylinux', the CD is an original edition of canonical! Both discs do not work and in both cases I received the same error messages. The DVD I used for insatalling an my laptop (hp pavillion dv8000 series -- intel centrino core duo, 1024MB RAM, 2x100GB hdd, graphic: same as above), and on my sisters laptop (hp pavillion dv5000 series -- AMD athlon 64bit, graphic: nVIDIA, 512MB RAM, 80GB hdd). With both laptops the DVD caused no problems at all!! I used the text-based installation.
Sorry for having forgotten these infos!!
Thanks for your patience and help. Greetings, thommy

---

### Post by Pumalite on 2007-09-30
Better download a new iso (disk could have been damaged) and follow these guidelines: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
(maybe you need to clean the lens in your CD-ROM)

---

