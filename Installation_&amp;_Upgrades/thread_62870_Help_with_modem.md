---
title: "Help with modem"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by abominable on 2005-09-06
Hello,

I'm trying to set my modem, but I'm facing some problems.. It is an external modem connected to my pc through USB.

[Here are the Instructions..](http://www.intracom.gr/helpdesks/netmod/installation/engl_install-guides.htm) about netMod USB Installation LINUX 2.2x..

I manage to mount my usb device (or at list I think so) but when I'm booting to Linux there appears a line: mount point /proc/bus/usb doesn't exist... The strange is that I can see that location in my pc.. Any Ideas??

---

### Post by xy77 on 2005-09-06
Could you post the output of
```
$ lsusb 
```
please?

It should list the modem. Another helpful thing may be to check
```
$ dmesg | grep -i usb 
```
which tells you of any usb activity your system notices.

If the modem appears somewhere in the list, you should be able to continue with its configuration. If you have wvdial installed ```
$ sudo apt-get install wvdial
``` you can run ```
wvdialconf wvdial.conf_test
``` to find out if the modem is being recognized by wvdial.

And it might be of interest, whether you use any other USB devices successfully.

That's all I came to think of. Perhaps anyone else knows a bit more about /proc/bus/usb

- David (xy77)

---

### Post by abominable on 2005-09-07
Thanks a lot.. I manage to get it work..

---

