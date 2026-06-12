---
title: "VMWARE and Ubuntu"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by sdmike on 2007-06-27
Can you run Ubuntu in Windows XP using VMWARE?

---

### Post by tgm4883 on 2007-06-27
Yes

---

### Post by mosaic2s on 2007-06-27
is it possible to install and run with 80% efficiency winxp within ubuntu? this will effectively take care of few specialised programs that do not run on ubuntu.

sandeep

---

### Post by tgm4883 on 2007-06-27
what do you mean by 80% efficiency?

---

### Post by luvr on 2007-06-27
I use VMware Workstation to run Windows XP under Ubuntu, and it works great. There's no noticeable performance penalty, and Windows XP runs much more stable within the virtual machine than it used to do on the *"bare metal."*

You *do* need **VMware _Workstation_** (which does not come for free) for best results, though.

---

### Post by dabl on 2007-06-27
VMWare Player 2.0, running a Win XP virtual session, works great under Kubuntu and Ubuntu Feisty, although setting up your virtual machine is not the world's most obvious process.

Couple of points:

- If Linux is doing something with your sound chip/card (like running Firefox with Flash), then Win XP in VM Player isn't going to have access to it

- Ditto for USB devices

- I benchmarked a rather ponderous MS Visual FoxPro database that I use, called "The Master Genealogist", in both native Win XP and virtual Win XP under VMWare Player, on the same hardware platform.  The performance hit in VMW Player was a shade under 5% for a CPU-intensive routine called "Verify File Integrity".  Under Win4Lin, the same benchmark showed a 15% performance hit, compared to the native Win XP system.  The database app would not ever run correctly under Wine.

- VMWare Player is free (as in beer), but you will need a Windows installation CD and key to install Windows.

Hope that's a little informative.  :)

---

### Post by zdude on 2007-06-27
I've been playing with VMware Player 2.0 for a few days now and although it does work for the most part and is faster than the last version, I found problems with the SMP (multiple cpus) not working correctly - it froze my computer completely, more than four different times. I believe it occurred when accessing the CD/DVD drive. Also, plugging in one of my flash drives into the USB port causes a BSOD, it was loading some kind of program (the USB flash drive was) when it BSOD- it works perfectly in Ubuntu or regular stand-alone windows. The serial ports work in the regular window apps (like terminal) but not in other apps (various modem/fax software) that I tested. 

I was hoping the the SMP and the serial ports would work due to some old software I had as well as some programs that are real number crunchers that are multi-threaded but it looks like those will still need to be booted into windows to run. I was hoping to finally dump my windows partition but looks like it will be a bit longer yet. :(

Edit: Also, I found the WinXP clock does not stay synced while running. It starts out correct but then speeds up dramatically and then sometimes, slos down somewhat. Weird.

---

### Post by elsaturnino on 2007-06-27
I've been running the XP on VMWare server for a couple months. It does a fine job doing the limited number of tasks it needs to perform (like running photoshop). My only gripe is that VMWare server doesn't have support for USB 2.0 so my usb hard drive is painfully slow.  The following links should prove useful if you decide to try VMware server.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
[http://www.go2linux.org/node/30](http://www.go2linux.org/node/30)

---

### Post by dabl on 2007-06-27
> **elsaturnino said:**
> I've been running the XP on VMWare server for a couple months. It does a fine job doing the limited number of tasks it needs to perform (like running photoshop). My only gripe is that VMWare server doesn't have support for USB 2.0 so my usb hard drive is painfully slow.  The following links should prove useful if you decide to try VMware server.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
[http://www.go2linux.org/node/30](http://www.go2linux.org/node/30)

Yep -- I found this one helpful too:

[http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model](http://www.penguin.ch/dokuwiki/doku.php/virtual:vmware:model)

---

