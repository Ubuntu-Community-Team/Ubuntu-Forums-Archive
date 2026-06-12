---
title: "[SOLVED] Login loops when I try to use latest kernel (4.2.0-30-generic)"
date: 2016-03-13
forum: Installation &amp; Upgrades
---

### Post by SpoZen on 2016-03-13
I suspect it might be my graphic card drivers that are causing the X login to loop.
I type in my username and password and it tries to login and show me the desktop.
But after a few seconds the screen goes black and it takes me back to the login window.


I have the Nvidia proprietary drivers installed. 
Any ideas?

---

### Post by Bashing-om on 2016-03-13
SpoZen; Yeah ...

> 
I suspect it might be my graphic card drivers that are causing the X login to loop.

Possible and likely if this happened after a kernel upgrade .

We can look at what the X layer is reporting.
```

cat /var/log/Xorg.0.log

```
and as well IF a driver is loaded:
```

sudo lshw -C display

```
Please use code tags to enclose these outputs:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

As a likely place to start the troubleshooting.

[INDENT][INDENT]the kernel and the driver must agree
[INDENT][INDENT][INDENT]to talk to the hardware
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by SpoZen on 2016-03-14
> **Bashing-om said:**
> 
[INDENT][INDENT]the kernel and the driver must agree
[INDENT][INDENT][INDENT]to talk to the hardware
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Yes, I think the Nvidia driver must be updated to match the latest kernel. 


```

cat /var/log/Xorg.0.log

```

[http://paste.ubuntu.com/15385106/](http://paste.ubuntu.com/15385106/)

```

sudo lshw -C display

```

```
  *-display UNCLAIMED
       description: VGA compatible controller
       product: GM206 [GeForce GTX 960]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
```


FYI This is data gathered from tty2 since I was unable to login when using the -30 kernel.

---

### Post by Bashing-om on 2016-03-14
SpoZen; Hey hey.

We can do this . Get a driver loaded ... BUT 
What is up that you have added the boot parameter " rootflags=subvol=@ " ??

And what we know presently:
1) the display is "unclaimed" as no driver is loaded .. Does the boot parameter prevent building a driver?
2) Nvidia recommends the 361 version driver for that card .. kinda bleeding edge 
[http://www.nvidia.com/download/driverResults.aspx/98373/en-us](http://www.nvidia.com/download/driverResults.aspx/98373/en-us)
and only the latest releases have access to that driver . OR we obtain the driver from our trusted PPA.

3) So, what release is this ( does HardWare Enablement Stack play here ??) .
show us:
```

lsb_release -a
uname -a

```
so we know what platform we are dealing with.

Then we look at what it is going to take to clean up the system and (RE-)install the Nvidia proprietary driver .

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by SpoZen on 2016-03-15
> **Bashing-om said:**
> SpoZen; Hey hey.

We can do this . Get a driver loaded ... BUT 
What is up that you have added the boot parameter " rootflags=subvol=@ " ??

[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

Well I ain't your average Ubuntu user I run btrfs. I suspect that's why I have  " rootflags=subvol=@ "...
And these problems probably occur because I run the 352.79 Nvidia driver. (need it for CUDA support)

Now to the good news!!

I rebooted my PC to test the -30 kernel and give you some more data... To my suprise the login actually worked so I checked "uname -a"...

```
Linux Jan 4.2.0-34-generic #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

The computer must have updated to a newer kernel without me even noticing it and it works perfectly!!

I appreciate you trying to help me though! Would have been really hard to try to fix this without upgrading the driver...

---

### Post by Bashing-om on 2016-03-15
SpoZen; Uh Huh ..

Great you are up and running,

Yeah, bunch of fixes and security updates in the latest kernel releases . We chalk this up to both the driver and fixes in the new kernel.

[INDENT][INDENT]ain't 'buntu wonderful
[/INDENT][/INDENT]

---

