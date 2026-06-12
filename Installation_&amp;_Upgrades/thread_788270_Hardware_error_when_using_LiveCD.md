---
title: "Hardware error when using LiveCD"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by sackbj on 2008-05-09
I was trying to boot a machine that has never used Linux before with an Ubuntu 8.04 amd64 LiveCD.  After the initial animated graph, my screen begins outputting this over and over again:

```

[194.740360] ata1: (irq_stat 0x00000040, connection status changed)
[more numbers] ata1: exception Emask 0x10 SAct 0x0 SError 0x4000000 action 0x2 frozen

```

I don't know what to make of this error, can anyone help?

My computer is:
E6850 3.0GHz
Abit IP35 Pro Mobo
8GB (4x2GB) G.Skill Ram
WD Raptor for OS, WD 640GB storage
ATI HD 3870 X2

If the LiveCD session goes well, I'll put another hard drive in there and make Ubunbu the main OS.

Thanks in advance!

---

### Post by Pumalite on 2008-05-09
Have you tried the Alternate CD?

---

### Post by sackbj on 2008-05-09
No, I will download the alternate CD and try that.

---

### Post by sackbj on 2008-05-09
Ok, now that I look at the alternate CD I see that it is for a text-based installer without a LiveCD environment.  One of the things I was hoping to acomplish with the install CD was the run the live enbironment and check to make sure my hardware was compatible.  I would prefer to find a way to do that before actually installing the OS.  However, if this error is the result of X trying to load I may be sunk.  Could this be an ATI issue?

---

### Post by Pumalite on 2008-05-09
If you want to try; knock yourself out with these:
Boot parameters
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791

---

### Post by sackbj on 2008-05-11
Pumalite:

I downloaded the alternate install CD.  It went to the first menu, I selected English, and the first thing I did was test the CD for defects.  It loaded the Linux kernel, printed out a copule of lines and hung.  I hit ctrl-c, and my machine began printing out this over and over agian:

```

/build/buildd/cdebconf-0.125/src/debconf.c:135 (main): Cannot initialize debconf template database

```

Every once in a while it would throw in something like:
```

[numbers] ata5.01: Exception Emask 0x0 SAct 0x0 Serr 0x0 action 0x2 frozen

```

I don't know what to make of this.

Edit: 
For a little clarification I let it run a little longer this time.  This is what I see when I use the alternate CD with the Install Ubuntu option:

```

[numbers] usb 2-2: can't set config #1, error -71
[numbers] irq 19: nobody cared (try booting with the "irqposs" option)
[numbers] handlers:
[numbers] [<fffffffff88-19300>] (usb_hcd_irq+0x0/0x60 [usbcore])
[numbers] [<fffffffff88-19300>] (usb_hcd_irq+0x0/0x60 [usbcore])
[numbers] Disabiling IRQ #19
[numbers] ata1.00: revalidation failed (errno=-5)
[numbers] ata1.00: revalidation failed (errno=-5)
[numbers] ata1.01: failed to set xfermode (err_mask=0x40)
[numbers] ata2.00 revalidation failed (errno=-5)
Starting system log daemon: syslogd, klogd.

```

Then it seems to hang.

The [numbers] looks like [33.036089], and they go up every time a new line is spit out.

---

### Post by Pumalite on 2008-05-11
The boot parameters are to be used one by one and in different combinations until you hit the right one.

---

### Post by sackbj on 2008-05-12
Unfortunately, I am not comfortable messing with boot parameters.  I will keep reading about them with the links you provided, but I would like to approach from a hardware standpoint first if possible.

Is it possible that this is a hardware error that could be solved by removing a piece of incompatible hardware?  I'm asking this because of the "ata1" error I keep seeing.  Right now all of my ata devices are SATA drives.  I have a Pioneer Blu-Ray drive, ASUS DVD-ROM drive, a WD Raptor, and a WD 640GB drive.  I will double-check the compatibility lists for these devices; I would be ok removing one of them if it is indeed behind this error.

---

### Post by Killa Frog on 2008-05-12
If you can't start into the livecd properly, try when booting from disc: live video=ofonly and see if that gets you  in the live environment. If it does, the rest should move along swimmingly for you.

---

