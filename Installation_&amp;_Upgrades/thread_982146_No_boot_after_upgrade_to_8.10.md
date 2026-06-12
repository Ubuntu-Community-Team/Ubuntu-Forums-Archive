---
title: "No boot after upgrade to 8.10"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by adrcamp98 on 2008-11-14
Dear All,


After an upgrade from 8.04 to 8.10, my computer cannot complete the boot. It stops incomplete.At the beginning of the boot, I pressed Ctrl+Alt+F1, having the following message:

ERROR: Driver 'pcspkr' is already registered, aborting...



I believe this is the cause for the problem. 


Does anyone have any clue?





Thanks and regards,

Adrcamp98

---

### Post by pennacook on 2008-11-14
can you post some details about your setup? Hardware, etc?

---

### Post by adrcamp98 on 2008-11-14
Hi,

thats my computer:


Motherboard: MSI 915G Combo

Intel Prescott 3.2
1024 DDRII RAM

HD Maxtor




thanks


adrcamp98

---

### Post by pennacook on 2008-11-14
well the pcspkr error can be worked around at least:

sudo rmmod pcspkr
sudo sh -c 'echo blacklist pcspkr >> /etc/modprobe.d/blacklist'

---

### Post by adrcamp98 on 2008-11-14
> **pennacook said:**
> well the pcspkr error can be worked around at least:

sudo rmmod pcspkr
sudo sh -c 'echo blacklist pcspkr >> /etc/modprobe.d/blacklist'
Ok!

I will try and, later on, post the results.

Thanks a lot!

---

### Post by adrcamp98 on 2008-11-14
'Module pcspkr does not exist in  /proc/modules'


is response for your commands.


Any clue?


thanks,

adrcamp98

---

### Post by pennacook on 2008-11-14
From looking around the error on pcspkr is reportedly harmless. What video card do you have? 

```
lspci |grep VGA
```

---

### Post by adrcamp98 on 2008-11-14
Don't have any.


Tks

---

### Post by pennacook on 2008-11-14
how about a full lspci then to see what video card it thinks it has ;)

---

### Post by adrcamp98 on 2008-11-15
after lspci, I've got a page full with:

USB controler: Intel Corporation
...
...
...
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00: 1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC interface bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE Interface Intel Corporation 82801FB/FW ICH6/ICH6W) SATA Controller 9rev03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev03)
02:01.0 Communication Controller : Conexant HSF 56k HSFi Modem (rev01)
02:04.0 RAID bus controller: VIA Technologies, Inc.. VT6410 ATA133 RAID controller (rev06)
02:06.0 Ethernet controller : REaltek Semiconductor Co., Ltd. RTL- 8169 Gigabit Ethernet (rev 10)




that's all after lspci.


Tks again,


Adrcamp98



ps do you think it's a video card problem/incompatibility?

---

### Post by adrcamp98 on 2008-11-16
I will put what I have after selecting the 8.10 (the upgrade) version at the boot options:

* Starting anac(h)ronistic cron anacron           [OK]
* Starting deferred execution scheduler atd       [OK]
* Starting periodic command scheduler crond       [OK]
* Checking battery state...                       [OK]
* Running local boot scripts (/etc/rc.local)      [OK]





and thats all! The next line the cursor is blinking.



Thanks again,


adrcamp8

---

