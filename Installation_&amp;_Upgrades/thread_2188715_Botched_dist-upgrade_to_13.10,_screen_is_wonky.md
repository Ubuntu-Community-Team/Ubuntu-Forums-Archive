---
title: "Botched dist-upgrade to 13.10, screen is wonky"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2013-11-18
Hi,

I have Xubuntu 13.04 and just did a dist-upgrade.  Now my login screen is normal but my desktop is all messed up.

Any idea what happened?

[ATTACH=CONFIG]247923[/ATTACH]

Thanks.

---

### Post by Bashing-om on 2013-11-18
1clue; Hi !

Proprietary drivers installed ???
Try booting in recovery mode ( with networking)-> Additional Drivers and install the recommended driver ( preferably open source (??)  ).

[INDENT][INDENT]hey it's a thought
[/INDENT][/INDENT]

---

### Post by 1clue on 2013-11-18
On a lark I uninstalled all the proprietary drivers, reinstalled xubuntu-desktop and all the packages it installs, and at this point I get that instane zebra desktop with nothing on it.

No cursor either.  Just the desktop.

---

### Post by oldos2er on 2013-11-18
> **1clue said:**
> Hi,

I have Xubuntu 13.04 and just did a dist-upgrade.  Now my login screen is normal but my desktop is all messed up.

Any idea what happened?

[ATTACH=CONFIG]247923[/ATTACH]

Thanks.

If the dist-upgrade included a kernel upgrade, try booting to an older previously working kernel. It would also help to mention details of your video hardware.

---

### Post by 1clue on 2013-11-18
Booted back to the older kernel (again) and get the same zebra screen.

07:00.0 VGA compatible controller: NVIDIA Corporation GT200 [GeForce GTX 260] (rev a1)

I've been using the nvidia driver.

---

### Post by Bashing-om on 2013-11-18
1clue; Well ...

Let's look and see if we can get an idea of what is not going on.
Boot to the GUI -> ctl+alt+f1 to get a console.
What graphics card and driver are recognized ?
Terminal codes:
```

lspci | grep VGA
sudo lshw -C display
lspci -nnk | grep -iA3 vga ##better info/confirmation

```
My output, ATI card and open source (radeon) driver:
> 
sysop@1304mini:~$ lspci | grep VGA
06:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550]
//
 capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
//
sysop@1304mini:~$ lspci -nnk | grep -iA3 vga
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:2342]
        Kernel driver in use: radeon
06:00.1 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]
sysop@1304mini:~$ 


Depending on the outputs, might try booting with added boot parameters (say, nomodeset) and see what can be done to load a different grphics driver.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by 1clue on 2013-11-18
07:00.0 VGA compatible controller: NVIDIA Corporation GT200 [GeForce GTX 260] (rev a1)

sudo lshw -C display
[sudo] password for ken: 
  *-display               
       description: VGA compatible controller
       product: GT200 [GeForce GTX 260]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:24 memory:f2000000-f2ffffff memory:c0000000-cfffffff memory:f0000000-f1ffffff ioport:ac00(size=128) memory:f3c80000-f3cfffff



07:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT200 [GeForce GTX 260] [10de:05e2] (rev a1)
	Subsystem: Device [196e:064b]
	Kernel driver in use: nouveau

---

### Post by Bashing-om on 2013-11-18
1clue; OK,
Nvidia card and nouveau (open source) driver loaded ...

Let's see what results with the boot option "nomodeset" see if the default FB driver gets us a graphics display.

grub boot menu "e" key for edit mode -> arrow down and across to "quiet splash" insert the term "nomodeset";
ctl+x to continue the boot process.

[INDENT][INDENT]we be try'n
[/INDENT][/INDENT]

---

### Post by 1clue on 2013-11-18
Nomodeset got me a low resolution screen.

I just tried adding the nvidia-driver again

---

### Post by 1clue on 2013-11-18
So does nomodeset have to stay in there, or what?  I got the driver loaded and it's working full resolution.

Thanks.

---

### Post by Bashing-om on 2013-11-18
1clue; Nope !

That "nomodeset" disables kernel mode setting, not an action we want on a permanent basis.

At this point, activate "Additional Drivers" - 3rd party sources enabled in Software Sources - and install the "recommended" driver.

[INDENT][INDENT]finer than a frog's hair ?
[/INDENT][/INDENT]

---

### Post by 1clue on 2013-11-18
Cool.  Removed the nomodeset and rebooted, I've still got everything.  Thanks, thread solved.

---

### Post by Bashing-om on 2013-11-18
1clue; Great !

Glad things are "looking" up !

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by 1clue on 2013-11-18
Reading it again, I'm not sure if I got my appreciation through clear enough.  Thanks everyone.

---

