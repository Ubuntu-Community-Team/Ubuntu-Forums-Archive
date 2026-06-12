---
title: "Ubuntu 10.10 locks up PC"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by Claude Rebeck on 2010-12-29
I am on Ubuntu7.10, When I install Ubuntu 10.10, all looks OK, but after a minute or so the computer locks up. Mouse and keyboard do not function.
I suspect that my computer does not have the memory or Hard drive space needed.
My computer is a Compaq Presario memory 1024MB and Hard Drive 160GB
The installation disk warns that 4.6GB is required.

Am I correct, and which memory or drive needs to be made bigger?

---

### Post by sikander3786 on 2010-12-29
In order to find which graphics card is there, please post the output of this command.

Applications > Accessories > Terminal:

```
lspci | grep VGA
```

And, is compiz enabled?

When the computer locks, do you remember any specific application running then? Does it lock up after a specific period of time or just random?

Regarding your partition problem, post the output of this one as well.

```
sudo fdisk -lu
```

Run this command from Terminal and see if there is something informative.

```
dmesg
```

---

### Post by Joe of loath on 2010-12-29
Your amount of memory is relatively low by modern standards, but will run Ubuntu fine. How much free space is there on your Ubuntu 10.10 partition, and have you run diagnostics utilities like memtest86 to check that your hardware isn't faulty?

---

### Post by Claude Rebeck on 2010-12-29
> **Joe of loath said:**
> Your amount of memory is relatively low by modern standards, but will run Ubuntu fine. How much free space is there on your Ubuntu 10.10 partition, and have you run diagnostics utilities like memtest86 to check that your hardware isn't faulty?

Ubuntu has the entire computer

---

### Post by Claude Rebeck on 2010-12-29
> **sikander3786 said:**
> In order to find which graphics card is there, please post the output of this command.

Applications > Accessories > Terminal:

```
lspci | grep VGA
```And, is compiz enabled?

When the computer locks, do you remember any specific application running then? Does it lock up after a specific period of time or just random?

Regarding your partition problem, post the output of this one as well.

```
sudo fdisk -lu
```Run this command from Terminal and see if there is something informative.

```
dmesg
```


Cant get to "Terminal"  no mouse, no keyboard!!

---

### Post by Claude Rebeck on 2010-12-29
> **sikander3786 said:**
> In order to find which graphics card is there, please post the output of this command.

Applications > Accessories > Terminal:

```
lspci | grep VGA
```And, is compiz enabled?

When the computer locks, do you remember any specific application running then? Does it lock up after a specific period of time or just random?

Regarding your partition problem, post the output of this one as well.

```
sudo fdisk -lu
```Run this command from Terminal and see if there is something informative.

```
dmesg
```

No access to enter anything.  I reinstalled Ubuntu 7.10 and all is fine.

---

### Post by Joe of loath on 2010-12-29
Do it from the live CD, or from your 7.10 installation (which is not really a good idea to keep using, since it's horribly out of date and not supported any more).

---

### Post by jstarner on 2011-08-29
I have been running ubuntu for years but i put 10.10 on my acer aspire everyone seems to be fine. but locked up and doesnt have to be anything running.. i pull logged 
Anyone tell me how to fix it.. it seems to me a Nxvideo error of some sort but i could be wrong please help

NXVIDEO:01/input/input8
[   15.148576] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   15.148611] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.227401] ppdev: user-space parallel port driver
[   15.240062] Skipping EDID probe due to cached edid
[   15.962448] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.000136] Skipping EDID probe due to cached edid
[   16.136079] Skipping EDID probe due to cached edid
[   16.668066] Skipping EDID probe due to cached edid
[   16.700055] Skipping EDID probe due to cached edid
[   16.736063] Skipping EDID probe due to cached edid
[   16.772055] Skipping EDID probe due to cached edid
[   18.522253] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.112023] eth1: no IPv6 routers present
[   26.272055] Skipping EDID probe due to cached edid
[   26.340046] Skipping EDID probe due to cached edid
[   26.376033] Skipping EDID probe due to cached edid
[   26.412030] Skipping EDID probe due to cached edid
[   27.676058] Skipping EDID probe due to cached edid
[   31.556041] Skipping EDID probe due to cached edid

---

