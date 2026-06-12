---
title: "Dropped to busybox, trying live desktop on 64-core machine with 256GB"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by Jonathon_Doran on 2015-02-19
This is a new server, and I really want to boot a live Linux image to check a few things.  I think I hit a bug in the current Fedora release.

I downloaded the latest Ubuntu today and booted the image off DVD.  I am dropped into busybox.

* There are no hard disks on this machine
* There is a DVD drive I am booting from
* Supermicro 2042G-6RF server
* 4 * AMD 6376 processors (total of 64 cores)
* 256GB of memory installed
* Only USB device is a keyboard (I might add a mouse in a bit)

I have not completed memory testing (which takes a very long time), but the first overnight run went well.
I have not performed any CPU stability tests yet.

The end result:  I am at the Busybox v1.21.1 prompt.  I was hoping to be at the screen which allowed me to try Ubuntu out.

Does anyone have any advice on how to proceed?

Thanks,
Jonathon Doran

---

### Post by tgalati4 on 2015-02-19
Welcome to the forums.  Put your finger on the Scroll Lock key and push it just before being dumped to busybox.  Post your error messages.

I believe that current kernels have up to 64 CPU's configured (up from 16 years ago), so that should not be the problem.  Send an email to SuperMicro and ask them what versions of Linux are certified on your hardware.

---

### Post by Jonathon_Doran on 2015-02-19
Well, 64 is within the up-to-64 range.  The Supermicro tech mentioned Red Hat and CentOS.  Neither is doing much better.
But thanks, and I will try to clarify exact versions of those distributions with Supermicro.

---

### Post by QIII on 2015-02-19
The live media supports 64 cores by default, but installed it should support 256 cores.

What is your graphics adapter?

---

### Post by Jonathon_Doran on 2015-02-19
[COLOR=#000000][FONT=verdana]The board has an integrated Matrox G200eW with 16MB of RAM.[/FONT][/COLOR]

---

### Post by QIII on 2015-02-19
I see a lot of trouble with that adapter and recent releases of Ubuntu when Googling it..

I'm on my cell, or I'd point you to some with possible solutions.  One answer was to use 12.04 or 12.04.1.

---

### Post by Jonathon_Doran on 2015-02-19
Thanks, I'll give that a try.  I'm seeing odd behaviour for sure.

---

### Post by tgalati4 on 2015-02-20
Check the BIOS and try to increase the shared video RAM.  Or boot in compatibility, low resolution mode, or use the "alternate" text-only installer version.

---

