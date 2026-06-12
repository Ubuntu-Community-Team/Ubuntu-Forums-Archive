---
title: "problem with forcedeth NIC driver"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by patrickgamer on 2007-02-05
First time Ubuntu user. I just installed 6.10 on my AthalonXP 2800 running on an nForce2 mobo. 

The default driver for the NIC is forcedeth. Everything else seems to have installed OK, but I can't connect to anything, (can't even hit my local router).

Is there some kind of tweak/config I'm supposed to make to initialize (or reinitialize) the onboard network card?

Thanks,
patrickgamer

---

### Post by patrickgamer on 2007-02-07
I still can't get it to work. Here are some things I've tried since my last post:
- I used ifconfig to down and up the eth0 device (and rebooted between states)
- I've tried unpluging the machine to sap power in case any windows code was eprommed in the NIC
- there was something else, but i can't remember. doens't matter b/c it didn't work


Originally I considered that my copy of forcedeth was out of date, but the date of my Ubuntu image is October of 2006, and according to [http://www.hailfinger.org/carldani/linux/patches/forcedeth/](http://www.hailfinger.org/carldani/linux/patches/forcedeth/) the latest forcedeth was released in August of 2006, so my copy should already contain the most up-to-date drivers.

---

### Post by patrickgamer on 2007-02-07
never mind. I'm the world's biggest idiot.

It was always working. I just forgot that my router had mac address filtering enabled...
/cry

---

