---
title: "Running persistent Ubuntu from USB"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by rknetsch on 2010-01-05
I am currently running Windows 7 and would like to "play around" with Linux and learn how to use it, but am not willing to entirely "jump ship: as of yet.  Thus, I would like to be able to use my USB key (32 gig) that is persistent.  I have had no success in being able to get this to work; I went to [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) and attempted several different times and the only one I could get to work was not persistent.  Any suggestions?

---

### Post by lmarmisa on 2010-01-05
The Ubuntu 9.10 Live CD includes a tool for installing a persistent version of this operating system in a USB key.

Download Ubuntu

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and burn a CD. Then start the Live CD and select System -> Administration -> USB StartupDisk Creator


My personal recommendation for learning Ubuntu or many other GNU/Linux distros is to use a virtualization solution like [http://www.virtualbox.org](http://www.virtualbox.org) running in your Windows 7 host system.

Best regards,

Luis

---

### Post by adam814 on 2010-01-05
Maybe this will help:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by rknetsch on 2010-01-06
Okay, I downloaded the ISO and put it on CD.  When I boot off the CD, it gives me a menu, so I ran the "run ubuntu without changes" and then made a USB boot disk.  When I boot off the USB I get the same menu as I do with the CD.  Do I then run the install to run Linux with persistence?

---

### Post by 00ber n00b on 2010-01-06
persistence..................

---

### Post by lmarmisa on 2010-01-06
You don't need to install anything more. Select your language and Try Ubuntu without any change to your computer or wait until the system starts automatically.

You will have an Ubuntu with persistence in your USB key if you defined in the **Make Start Up** menu some storage space for documents and setings when starting up.

---

### Post by rknetsch on 2010-01-06
So I select from the USB boot menu to run Ubuntu without changes, but it will still allow changes.  Is that what you mean?

---

### Post by lmarmisa on 2010-01-06
Yes, this menu needs an improvement :)

---

### Post by rknetsch on 2010-01-06
Okay, I'll try again and let you know.  I tried the install option and everything went blank.  I am going to remake a bootable USB again and then see what happens.  If it works, I'll catch you on the Ubuntu side of things.

---

### Post by rknetsch on 2010-01-06
Okay, I now have it working.  The only problem is that my Broadcomm wireless device was shown as "active, but not in use".  I had inactivate and then reactivate the driver to get it to work.  Any ideas?

---

### Post by efflandt on 2010-01-06
Yes that is one problem with booting persistant iso from USB is that when you activate Broadcom STA and reboot, the modules are there, but do not load automatically like they do in a regular installation.  Simply do **sudo modprobe -v wl** from a terminal after booting, or edit /home/ubuntu/.profile and insert the following:

```
# load Broadcom wireless module if necessary and not already loaded
# (change BCM4311 to your device, like BCM4312)
if lspci | grep -q BCM4311; then
    lsmod | grep -qw wl || sudo modprobe wl
fi

```Explaination: The default user that logs in automatically is "ubuntu", so ubuntu's .profile runs at that time. If it finds your wireless device in lspci, then if it does not already find "wl" module in lsmod, it does modprobe wl.  This is all ignored if booted on a PC that does not have that device.

---

### Post by rknetsch on 2010-01-07
Well, I decided to go with Wubi, but thanks for your help.  I am using it now and although I am not yet convinced of its stability, it is working much better than the other option.

---

