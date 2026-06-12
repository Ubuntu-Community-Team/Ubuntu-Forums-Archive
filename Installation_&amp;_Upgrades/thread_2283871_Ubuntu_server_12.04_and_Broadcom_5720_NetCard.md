---
title: "Ubuntu server 12.04 and Broadcom 5720 NetCard"
date: 2015-06-25
forum: Installation &amp; Upgrades
---

### Post by hiroshiman on 2015-06-25
Hi, 

[FONT=Helvetica Neue]I have recently installed an Ubuntu Server 12.04 LTS on a R720 Dell Server equipped with a BroadCom 5720 Network Card.
[/FONT]
[FONT=Helvetica Neue]However after configuring interfaces, no connection was available and mii-tool returned a "no link" status. Modinfo bnx2 revealed that driver supports BCM5706/5708/5709/5716 but not 5720.
[/FONT]
[FONT=Helvetica Neue]To make it work, I have to set the eth interface at 100Mb Speed and Half Duplex or it won't negotiate, and that's quite unconvenient.
[/FONT]
[FONT=Helvetica Neue]I tried to install the driver provided by broadcom from tg3 sources files as it was explained but after make clean and make install, restarting the machine, bnx2 doesn't seem to be upgraded.
[/FONT]
[FONT=Helvetica Neue]What am I doing wrong ?[/FONT]

---

### Post by dino99 on 2015-06-25
Looks like you need to download the broadcom driver 'linux-3.137hip'  from [https://www.broadcom.com/support/?gid=9](https://www.broadcom.com/support/?gid=9) (tg3)

DRIVER INFORMATION
To determine the driver version used in your PC, please select your OS below for instructions:
Linux	
At the command prompt type insmod bcm5700 or insmod bcm4400 depending on your chipset
At the command prompt enter grep -i version /proc/net/nicinfo/eth*.info
[https://www.broadcom.com/application/ethernet_nic.php](https://www.broadcom.com/application/ethernet_nic.php)

---

### Post by hiroshiman on 2015-06-29
Hey, found out that the Ubuntu 12.04 certified kernel version for Dell R720 servers was 3.2.0 and our kernel is in 3.13.0, maybe it could be the source of the issue.

I haven't tested it yet on the server because I don't have easy access on it but upgrading kernel to 3.2.0, installing tg3 driver should probably do it.

I'll give an update as soon as I can make the upgrade.

---

