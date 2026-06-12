---
title: "Wireless network not working"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by dinmc on 2009-12-25
Just installed the latest Ubuntu 9.10 software on my laptop. Newer used Linux before!!!
The installation made no problems, and everything looks fine - only one thing is not working!! Wireless networking. The wired networks works perfact, but not the wireless network.
What can I do??

Regards
Lars

---

### Post by Ginsu543 on 2009-12-25
Does your laptop have a Broadcom wireless adapter? If so, this is a known issue with an easy fix. You need to connect your laptop directly to your router using an Ethernet cable (to access the internet). Open System --> Administration --> Synaptic Package Manager. Type "broadcom" under Quick search and hit Enter. You should see a file called "bcmwl-kernel-source." Mark it for installation and click "Apply" to install. Once you reboot, your wireless should work.

If your laptop has a different wireless adapter, you will need to find the right Linux driver for it.

---

### Post by dinmc on 2009-12-26
> **Ginsu543 said:**
> Does your laptop have a Broadcom wireless adapter?

YES!! It does, so I followed your instruction. When typing "broadcom" in the quickseach field, it finds "bcmwl-kernel-source" and I installed this package and restarted, but still no wireless network. Actually when typing "broadcom" in the quickseach field it finds this "bcmwl-modaliases" as well. This was already installed. Should this be removed to make it work?

Regards
Lars

---

### Post by mprice on 2009-12-26
Which Broadcom wireless card are you using the exact model to be specific, if you are not sure of the exact model you can find out by putting this command in the terminal.

```
lspci
```

---

### Post by shredder12 on 2009-12-26
go to System->administration->hardware drivers..
nd chk if the wireless driver is enabled..

---

### Post by dinmc on 2009-12-27
> **mprice said:**
> Which Broadcom wireless card are you using the exact model to be specific, if you are not sure of the exact model you can find out by putting this command in the terminal.

```
lspci
```

Its a Broadcom 4318

Regards
Lars

---

### Post by dinmc on 2009-12-27
> **shredder12 said:**
> go to System->administration->hardware drivers..
nd chk if the wireless driver is enabled..

I got no drivers here!

Regards
Lars

---

### Post by Geezer60 on 2009-12-27
I just went through the same thing a few hours ago.  I went to hardware drivers in Admin (make sure you're connected via wired at the time) and when it came up, I clicked on the center item (Broadcom drivers), it downloaded and installed.  I then clicked "Activate" and when I pulled the cable, it connected right up with wireless.

---

### Post by dinmc on 2009-12-27
> **Geezer60 said:**
> I just went through the same thing a few hours ago.  I went to hardware drivers in Admin (make sure you're connected via wired at the time) and when it came up, I clicked on the center item (Broadcom drivers), it downloaded and installed.  I then clicked "Activate" and when I pulled the cable, it connected right up with wireless.

When I go into hardware drivers under Admin, it's empty. No drivers here.

Regards
Lars

---

### Post by Ginsu543 on 2009-12-27
I just checked my System --> Administration --> Hardware Drivers, and the bcmwl-kernel-source file installs Broadcom drivers for BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware. Since yours is 4318, that may be why the drivers are not working. According to the official Broadcom download site [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), it appears those are the only models they support (at least for linux).

---

### Post by shredder12 on 2009-12-28
you might want to give this a try..
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) 
or 
[http://linuxers.org/howto/how-install-drivers-bcm43xx-chipset-based-wireless-cards-ubuntu](http://linuxers.org/howto/how-install-drivers-bcm43xx-chipset-based-wireless-cards-ubuntu)

there has been a mention of success with bcm4309 card.. so it could work for you too..

---

### Post by KyleG545 on 2009-12-28
This might help

[http://forums.linuxmint.com/viewtopic.php?f=53&t=14349&start=0](http://forums.linuxmint.com/viewtopic.php?f=53&t=14349&start=0)

---

