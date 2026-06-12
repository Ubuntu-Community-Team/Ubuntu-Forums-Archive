---
title: "USB Device not recongnized"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Zevad on 2010-01-23
I am running ubuntu 9.04 on a dual boot system. I am trying to use my ONDA MT503HS USB modem with ubuntu as it is my only internet access being stationed over here in Italy. 
I have installed the linux software that came on cd with the device and the device works when i boot up windows on this computer and on my other computers without problems. I am copying and pasting the lsusb without the device and with the device. I am still new to Ubuntu and any help you could provide would be immensly appreciated !!

lsusb without device:

james@Laptop:~$ sudo lsusb
[sudo] password for james: 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:183e Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:1000  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and this is the lsusb with the device 

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 19d2:2000  
Bus 006 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:183e Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:1000  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

It is not showing up on desktop or fdisk or any other place that I can find. Will be checking back regurly if there is any other info you need will reply soon as I can.

Thanks again!!!

---

### Post by superdexter on 2010-02-28
Zevad: were you able to resolve your issue with the Onda MT503HS internet key?  I also am in Italy and trying to get the key to work.  

I have found some resources that have helped me make progress, but I have not yet had success.  I would share them with you if you like, but I noticed the thread is marked as [SOLVED] and was curious if you have resolved the issue.

I have not found any easy fix, the things that I have done to get the device mounded as TTYUSB0/1/2 included compiling source code on an Ubuntu 9.10 system.

---

