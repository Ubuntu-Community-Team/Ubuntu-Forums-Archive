---
title: "Lucid freezing"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by sdbrogan on 2010-05-30
I'm having a problem with a new install of Lucid freezing a few seconds after booting up.  Completely frozen -  ctrl-alt-backspace or alt-SysReq-R-E-I-S-U-B have no effect.  The md5sum of the installation iso was all right, the disk check was all right, & the memory test was all right.  It's a GeForce 5500 graphics card, but I haven't installed any special drivers.  Booting up to the command line (netboot) helps a bit but it still crashes after from a few minutes to a couple of hours. From the command line I tried removing compiz & compiz-core but it makes no difference.  I also updated the installed packages, including to the 2.6.32-22 kernel, but no difference.  This has happened with Jaunty & Karmic, but Intreprid runs fine, as did Windows XP.  Anyone have any ideas what I could do to find out the cause ?

---

### Post by ronparent on 2010-05-30
Try editing the kernal boot linr to add **noapic** and/or **nolapic**. Of course if added boot parameters fix your problem you will have to make them permanent by adding them to the boot line with **sudo gedit /etc/default/grub** in a terminal.

---

### Post by sdbrogan on 2010-05-31
Thanks, but I forgot to mention I'd already tried changing the boot parameters :

irqpoll noapic nolapic acpi=off

---

### Post by sdbrogan on 2010-05-31
I've also tried installing the 173 nVidia grphics driver, but it doesn't help.

---

### Post by ronparent on 2010-05-31
If you were experiencing kernel panic, the things you've tried might have fixed it. A bad memory stick perhaps? If you have a pair try reversing them or using in different slots. Obviously some glitch has broken the chain in execution. The where will be elusive unless an error is writen to the logs.

---

### Post by davidmohammed on 2010-05-31
others have tried booting with nomodeset in their grub... might work for you.

When you reboot are there any obvious error messages in the system log at or just before the time of the hard-lock?

---

### Post by sdbrogan on 2010-05-31
'nomodeset' doesn't help, nor swapping the memory sticks.  No error messages on reboot, so I've copied the contents of \var\log over to a USB stick - but where should I be looking & what should I be looking for ?

---

### Post by ronparent on 2010-05-31
An errant mouse or keyboard should have showed up in intrepid or win xp? Have you unplugged all devices not essential to normal operation to possibly locate one that may be glitchy with the system? Is something different in your system since intrepid? Does intrepic still run.

You seem to be covering all the bases. I doubt the nvidia graphics are a proble, but, then again, who knows?

---

### Post by sdbrogan on 2010-05-31
Intrepid still runs fine  on the same system.  I'd like to try with a different graphics card, just to see, but I haven't another to try.  What would be the drawbacks, if any, of running Lucid with the Intrepid kernel ?

---

### Post by ronparent on 2010-05-31
I doubt you have much chance of running lucid with the intrepid kernel. There is more to it than the kernel itself. You could probably dress intrepid to look like lucid. 

What is the build of your box (mb, bios. memory, etc)?

---

### Post by sdbrogan on 2010-05-31
AMD Sempron 300+ CPU
512+512+256 RAM
nVidia Geforce FX 5500 graphics card
Western Digital 40GB ATA disk
Phoenix BIOS v 6.00PG

---

### Post by sdbrogan on 2010-05-31
The motherboard is a Foxconn Winfast
NF3250GK8AA-EKRS
or
NF3250K8AA-ERS
(I forget which)

---

### Post by sdbrogan on 2010-05-31
It's
NF3250GK8AA-EKRS
(with nForce3 250Gb)

---

### Post by sdbrogan on 2010-05-31
I was wondering if perhaps there are two different problems : one with the kernel, which occurs infrequently in netboot or low graphics mode; & one with Xorg, which occurs within seconds off a normal boot.  So I've also tried changing some settings in Xorg.conf :

Option "DRI" "Off"
Option "AIGLX" "Off"
Option "PM" "Off"
Option "NoMTRR"

These don't help, but does anyone know any more that might ?

---

### Post by sdbrogan on 2010-05-31
Here are some logs.

---

### Post by sdbrogan on 2010-05-31
The freezing seems to have stopped after installing the latest mainline kernel 2.6.34 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

---

### Post by ronparent on 2010-06-01
Glad to hear that and hope it holds. I do feel that some of the updates are catching up with some of the known bugs.

---

### Post by sdbrogan on 2010-06-01
I hope so - I plan to try some older versions of the mainline kernel to see whether or not the fault's with the ubuntu-specific modifications.  And thanks very much for your help.

---

