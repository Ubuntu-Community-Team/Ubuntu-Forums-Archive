---
title: "cannot locate library libraspberrypi-bin"
date: 2022-07-20
forum: Installation &amp; Upgrades
---

### Post by eelie on 2022-07-20
Hi,,

Trying to install libraspberrypi-bin, and get this:


```
$ sudo apt-get install libraspberrypi-bin



Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package libraspberrypi-bin



```
More information about my system:

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04 LTS
Release:        22.04
Codename:       jammy

```

any help? thanks

---

### Post by Holger_Gehrke on 2022-07-20
That package contains several small programs (dtmerge, dtoverlay, dtoverlay-post, dtoverlay-pre, dtparam, tvservice, vcgencmd, vcmailbox, vchiq_test) that interact directly with the hardware or the boot software of a raspberry pi. Since they are useless on non-raspberry-pi systems they are only available as packages for armhf or arm64 processors. So if you're trying to install them on a x86 based system, you'll get told there's no such package because there isn't - for that architecture.

Perhaps telling us what you're trying to achieve by installing that package will give someone an idea of how we can help you ...

Holger

---

### Post by eelie on 2022-07-20
for sure, thanks for explaining that.  

As for why I need to install it, I'm running a script listed below in the link that reports all the vitals for my Ubuntu machine to via MQTT. Unfortunatly, the temperature is nor reporting corrrectly, however, there was a note about that here in the instructions to install this package in Ubuntu only systems:

[https://github.com/ironsheep/RPi-Reporter-MQTT2HA-Daemon](https://github.com/ironsheep/RPi-Reporter-MQTT2HA-Daemon)

---

### Post by Holger_Gehrke on 2022-07-20
That script, too, is meant to run on a raspberry pi. It uses some of the commands from libraspberrypi-bin to get information that you'd get differently on a x86 PC. For example it uses vcgencmd to get the various temperature readings, which you'd get from 'sensors' from the package 'lm-sensors' on x86. Unless the machine you want to monitor is a raspberry pi, that script needs  a major rewrite to work.

Holger

---

### Post by eelie on 2022-07-20
thats is a good point.

I mean, it is working, its just the temperature value is not correct. Supposedly, that library would solve the issue....but if its going to cause issues, I can let the temperature go.

---

