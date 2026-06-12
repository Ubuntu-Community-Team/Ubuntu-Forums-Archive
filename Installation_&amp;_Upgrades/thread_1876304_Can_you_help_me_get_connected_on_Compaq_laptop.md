---
title: "Can you help me get connected on Compaq laptop?"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2011-11-06
I installed 10.10 on a Compaq laptop. Laptops are completely alien to me. It has a built in network adapter. I do not know how to configure it. Can you help me?

---

### Post by lkraemer on 2011-11-06
First thing you need to consider is that 10.10 won't be supported for long term.  I'd suggest installing 10.04.3 LTS (Long Term Support), but it's your choice.  The end of life for Ubuntu 10.10 will be coming shortly as it's already late 2011.

Most Compaq Computer Laptops I own use the Broadcom Wifi Hardware, and I'd expect yours to have the same.

I created a HOWTO: and while it is probably out of date, it should give you an idea of what needs to be done.  If you follow my guide I'd suggest you use the Driver that is default with the Version of Ubuntu you install, versus trying to use ndiswrapper and some Windows Drivers.  But, once again it's your choice.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto+broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto+broadcom)

There are several other HOWTO:'s on the forum, and you might like one of the others better, so do a bit of searching before you dive into the process.

Whatever guide you use, Please post your results as you go, so we know what progress you are making, as we can't see your screen.  Also others will be viewing your postings and learning as you progress through your quest.

I'd expect that within 30 minutes you should be up and running, as most likely the firmware isn't installed.

If you have access to a LAN where you can plug in a Ethernet Cable and Update your system, then Check for New Hardware Drivers, most likely your update will load the firmware and get the Wifi working, but that isn't always the case.

Good Luck!

LK

---

### Post by fdrake on 2011-11-06
can you post the output of:
```
lshw
lsci
rfkill list all
iwconfig
ifconfig
```

---

