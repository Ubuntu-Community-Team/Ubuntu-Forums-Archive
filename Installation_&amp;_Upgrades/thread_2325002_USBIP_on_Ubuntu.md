---
title: "USBIP on Ubuntu"
date: 2016-05-18
forum: Installation &amp; Upgrades
---

### Post by itsmehere2 on 2016-05-18
I am using Linux kernel version 3.19 Ubuntu Linux. I need  to install USB/IP in it and would like to bind/share USB devices so that I can connect to it from another machine.
I issued the below commands:


1. apt-get install usbip  -> says already installed
2. sudo modprobe usb-ip core ->Success
3. sudo modprobe usbip-host ->Success
4. sudo usbip -D ->Success


When I tried to bind the device suing the below command, I am getting an error :


"add 2-1.4 to match_busid failed."



I verified the bus ids using the command usbip_bind_driver command and its correct.


What could be wrong here?
Do I need to compile the usb/ip source? Docs say that usbip source is available in drivers/staging/usbip folder but I do not see any such folders there.
What are the exact steps for compiling usb/ip source if need be?
Any help is deeply appreciated.


[CENTER]
[/CENTER]

---

### Post by itsmehere2 on 2016-05-24
Any updates on this?

---

### Post by matthew02 on 2016-05-24
> **itsmehere2 said:**
> 4. sudo usbip -D ->Success
To run the usbip daemon, run the following as root:
```
usbipd -D
```


> **itsmehere2 said:**
> When I tried to bind the device suing the below command, I am getting an error :


"add 2-1.4 to match_busid failed."


I verified the bus ids using the command usbip_bind_driver command and its correct.

What command did you run to bind your device? The correct way is to run the following as root:
```
usbip bind -b *busid_of_device_to_bind*
```

---

