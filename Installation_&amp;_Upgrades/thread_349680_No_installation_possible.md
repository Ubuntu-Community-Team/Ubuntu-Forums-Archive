---
title: "No installation possible?"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2007-01-30
I just tried to install Ubuntu 6.10 on my new PC using the desktop install CD.

I first tried to check the CD and after a while of the Ubuntu logo I got a text page with the following error message:

```

BusyBox v.1.1.3 (...)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)

```I then tried to install Ubuntu with the standard options (just changing to my keyboard layout) and got exactly the same error message.

Not very encouraging ... :(

Hardware: Intel 965-ICH8 board with two SATA disks (running in IDE mode) and a DVD drive attached to an IDE controller.

---

### Post by johann_p on 2007-01-30
Ok -- I first switched off the splash/quiet options and got this output:

```

... 
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory 
Done. 
mount: Mounting /sys/ on /root/sys failed: No such file or directory 
mount: Mounting /proc on /root/proc filed: No such file or directory 
Target filesystem doesn't have /sbin/init 

```
followed by the stuff mentioned in my previous post.

I then downloaded the "alternate" CD and tried that one -- this fails in the step that tries to mount the CDROM, complaining about a missing driver/module and telling me to either provde a driver disk or to pick a module manually.

My DVD writer is recognized under Windows as a Optiarc DVD RW AD-7173A and is attached with PATA to the Intel DG965WH  mainboard.

I tried OpenSuse 10.2 and the installer worked just fine.

I'd rather install Ubuntu but it seems Ubuntu doesn't let me :(

---

### Post by majestros on 2007-01-31
I had the exact problem.  I also had issues when trying to install debian a few years ago.  a year or so prior to that, I had a redhat installion work fine though . . .

Please let me know if you solve this problem, I'll try the alternate CD next.

ASUS A7V8X
AMD Athlon XP 1600+
Nvidia GeForce 6600GT
Trendnet USB KVM to logitech mouse and microsoft keyboard
I have a number of internal HD and a previously partitioned system and boot loader (though the debian can't launch X Windows)

---

### Post by RAMpire on 2007-03-07
I've had the exact same problem, johann, in every detail you listed.  I recieved the same errors with the alternate CD, the Live CD, and even when I tried to use the P.H.L.A.K. Live CD.  OpenSuse works fine for me as well.

Processor: Intel Core 2 Duo E6300
Motherboard: Intel DP965LV
DVD: Lite-ON DVDRW SHW-160P6S

---

### Post by johann_p on 2007-03-07
I think it is a fact that Ubuntu Edgy and earlier just does not support that hardware. 

I have installed OpenSuse 10.2 without problems on that computer.

The current Festy Fawn also works, but of course it is still under development.

---

### Post by zvacet on 2007-03-08
Did you try this
[http://www.ubuntuforums.org/showthread.php?t=28948]("http://www.ubuntuforums.org/showthread.php?t=28948")

---

### Post by glotz on 2007-03-08
One thing you could try is installing Dapper and upgrading to Edgy.

---

### Post by juice99 on 2007-03-08
i have the exact same thing and nobody cares, trying to solve it for 30 hours, sent bug report

debian works fine, windows works fine, open suse works fine. only ubuntu doesnt work.

i asked like 100 times on irc channel, nobody knows anything. i made some threads - nobody knows anything.

Feisty got the exact same problem + doesnt support ati 1950 pro, and nobody cares. why is that?

---

### Post by glotz on 2007-03-08
You're entitled to a full refund if you still have the receipt.

---

