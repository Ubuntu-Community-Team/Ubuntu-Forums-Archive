---
title: "Jaunty upgrade hassles"
date: 2009-02-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by praxis22 on 2009-02-11
upgrading from intrepid, all went well, untill it came time to reboot, at which time I had to go find a keyboard monitor and mouse, (I use it as standalone system at work, login via telnet.)

It took me while to work out why dhcp was autoconfiguring the network. stupidly I checked hosts and not interfaces saw it's static address was unchanged and couldn't work out what was wrong. Long story short, the install had changed the network adpater from eth0 to eth1, so interfaces which was configured for eth0 wasn't working. 

Took me a while to work that out, you don't expect the install to do such things to your hardware. 

Then I had all manner of issues with gdm, just didn't like it's old config, screwed up, locked up, wasn't at all happy. (I should point out it was using the same keyboard and screen, etc.) So I booted single user and did dpkg-reconfigure. Only now gdm will not come up at all, or more to the point will not drive the screen. though reflections works OK but the screen resolution in gnome is horrible, 800x600 or so across 2x 20" monitors. I restarted dbus, hald, etc. multiple reboots, mutliple xorg.conf's, same results.

When I opened a terminal, it took up most of the screen, and I discovered the keyboard had been remapped, none of the keys worked, the return gave me = etc. A complete dogs breakfast. So I did most of my configuration via telnet. 

Eventually I fell back to the failsafe and booted from scratch, this gave me a screen on the real gfx card, but the reflections session was still horrible to the point of being useless. Though the scroll keys did work so I could go up and down through old commands. Anyway...

In the end I decided to ditch the POS gnome and go with xfce as a default session. This flies. Not only does it boot up with two screens at 1600x1200 with proper sized terminals, the keyboard  works too. Bonus!

This isn't on anything exotic it's an old IBM thinkcenter:


```
lshw -businfo
Bus info          Device      Class       Description
=====================================================
                              system      83052CG
                              bus         IBM
                              memory      111KiB BIOS
cpu@0                         processor   Intel(R) Pentium(R) 4 CPU 2.00GHz
                              memory      8KiB L1 cache
                              memory      512KiB L2 cache
                              memory      512MiB System Memory
                              memory      256MiB DIMM DDR Synchronous
                              memory      256MiB DIMM DDR Synchronous
pci@0000:00:00.0              bridge      82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Inte
pci@0000:00:02.0              display     82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Devi
pci@0000:00:1d.0              bus         82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #
pci@0000:00:1d.1              bus         82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #
pci@0000:00:1d.2              bus         82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #
pci@0000:00:1d.7              bus         82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
pci@0000:00:1e.0              bridge      82801 PCI Bridge
pci@0000:02:08.0  eth1        network     82801DB PRO/100 VE (LOM) Ethernet Controller
pci@0000:00:1f.0              bridge      82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
pci@0000:00:1f.1  scsi0       storage     82801DB (ICH4) IDE Controller
scsi@0:0.0.0      /dev/sda    disk        40GB IC35L060AVV207-0
scsi@0:0.0.0,1    /dev/sda1   volume      35GiB EXT3 volume
scsi@0:0.0.0,2    /dev/sda2   volume      1466MiB Extended partition
                  /dev/sda5   volume      1466MiB Linux swap / Solaris partition
scsi@1:0.0.0      /dev/sdb    disk        40GB IC35L040AVVN07-0
scsi@1:0.1.0      /dev/cdrom  disk        CD-ROM F522E
pci@0000:00:1f.3              bus         82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
pci@0000:00:1f.5              multimedia  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
```

It's about as vanilla as they come.

I'm a UNIX sysadmin, you wouldn't want to try this as a n00b.

---

### Post by eyelessfade on 2009-02-11
Just one question, Telnet!? Why? I truly hope you never connect to this box from outside your private network

---

### Post by nyarnon on 2009-02-11
> **praxis22 said:**
> 

I'm a UNIX sysadmin, you wouldn't want to try this as a n00b.

A n00b alfa testing? :lolflag:

---

### Post by praxis22 on 2009-02-12
Why telnet? Because it's old, trusted and reliable, it "just works" besides which none of our UNIX boxes have internet access. I had to cobble together a perl script to manufacture access though a MS gateway just to get out.

We have a RHEL server that's as naked as the day it was installed because we can't get out to patch it :)

As for n00bs alpha testing, I've seen it done. When they hear about all the "cool stuff" they figure they have to try it. Then the bleating starts. :P

---

### Post by Nixie Pixel on 2009-02-12
> **nyarnon said:**
> A n00b alfa testing? :lolflag:

Hey, we n00bs want to try cool stuff too!

(Or in my case, avoid a bug that causes kernel panics every day in Intrepid)

---

### Post by praxis22 on 2009-02-12
> **Nixie Pixel said:**
> 
(Or in my case, avoid a bug that causes kernel panics every day in Intrepid)

Really? That's odd what was the cause?

---

### Post by Nixie Pixel on 2009-02-12
> **praxis22 said:**
> Really? That's odd what was the cause?

Your guess is as good as mine.

(So as not to derail this thread any further, check out [this thread]("http://ubuntuforums.org/showthread.php?t=976287") for details)

---

### Post by praxis22 on 2009-02-12
Ah wireless demons...

I have no truck with wireless on security and speed grounds. Cabled is always so much faster. 

Have you tried NDIS wrapper:

[http://en.wikipedia.org/wiki/NdisWrapper](http://en.wikipedia.org/wiki/NdisWrapper)

It allows you to run windows wireless drivers in Linux, which has the advantage of not killing your kernel if they don't work :)

---

### Post by Nixie Pixel on 2009-02-12
It wasn't a wireless problem for me.  It may have been for other people, but not for me...

Anyway, I won't hijack your thread any more :)

---

### Post by praxis22 on 2009-02-12
No worries it was more just a warning for others. Got it working now. Caveat emptor and all that. :)

---

