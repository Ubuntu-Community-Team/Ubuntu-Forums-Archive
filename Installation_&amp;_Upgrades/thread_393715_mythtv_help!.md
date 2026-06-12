---
title: "mythtv help!"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by linedpaper on 2007-03-26
I'm following the ubuntu mythtv wiki to get my mythtv going.  Sadly I have directv and can't seem to get the usb port working so I have an irblaster I'm going to use.  I'm following the lirc setup and compiled in the lirc_serial module, but I'm getting the following error when I try to start lirc.  Can anybody help me out?

```
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.

```

---

### Post by linedpaper on 2007-03-26
bump

---

### Post by fenian on 2007-03-26
What model/manufacturer cable box are you using?

---

### Post by hansoffate on 2007-03-26
What IR are you using?  The built in one from a PVR 150?

---

### Post by linedpaper on 2007-03-26
sorry, no i'm using the irblaster.info one.  It's the serial one that some guy makes himself.  It's supposed to work with mythtv/lirc, problem is I can't get lirc to start with the lirc_serial module in and load modules set to true.  Starts fine as soon as I change it to false.

---

### Post by superm1 on 2007-03-26
Hi,
The problem is most likely that you didn't disable kernel serial support.  see the serial section here: [https://help.ubuntu.com/community/Install_Lirc_Edgy#head-6ceb2a6bf65eddb537dd6038798144b163ab4a0a](https://help.ubuntu.com/community/Install_Lirc_Edgy#head-6ceb2a6bf65eddb537dd6038798144b163ab4a0a)

---

