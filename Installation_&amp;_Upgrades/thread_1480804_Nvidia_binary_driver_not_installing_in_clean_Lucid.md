---
title: "Nvidia binary driver not installing in clean Lucid install"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Envy Life on 2010-05-11
I have a Geforce 6200, trying to use nvidia-current.  However I'm getting the following:

(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Hardware Drivers says the nvidia-current driver is "Active but not in use" and my only option there is to remove.  I've removed, re-activated, and rebooted at least 10 times... even re-installed from command prompt.  

$ modprobe nvidia
FATAL: Module nvidia not found.

Package manager shows installed nvidia-current, nvidia-current-modaliases, nvidia-settings all installed. 

No driver is located in /usr/lib/xorg/extra-modules

$ lspci -vnvn

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV44 [GeForce 6200 A-LE] [10de:0222] (rev a1)
        Subsystem: XFX Pine Group Inc. Device [1682:226a]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Region 2: Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at f7ce0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nouveau
        Kernel modules: nvidia-current, nvidiafb, nouveau


Looks like a general issue with the installer.  I don't know how to work around it.

---

### Post by G-mL on 2010-05-12
yeah! same exact problem with me. I have an NVS 160 card and have been having the same exact issues from the past few days. Currently, I am running on "low graphics" mode. Every time I try to activate the nvidia drivers, it gives the same error while starting X. Anyone have any suggestions?

---

### Post by Envy Life on 2010-05-12
If I run nvidia-xconfig which creates an xorg.conf, it'll specify the nvidia driver, which it cannot find and ask me whether I want to fix it or go into low resolution mode.  

If I purge the xorg.conf file, it'll auto-load the nouveau driver and allow high res.

---

### Post by dino99 on 2010-05-12
have you compiz, java or flash installed ? try without the other video drivers installed too ( you only need nvidia*)

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by frantid on 2010-05-12
Envy Life,  this guy had the same problem and fixed it.  See first post.

[http://art.ubuntuforums.org/showthread.php?t=1473121](http://art.ubuntuforums.org/showthread.php?t=1473121)

---

### Post by Envy Life on 2010-05-13
No, that guy had a different set of issues with network and vesa driver.  I tried his instructions, which is pretty much what I've done 5 times now, and got the same results.  I even manually copied /usr/lib/xorg/extra-modules/nvidia_drv.so from another box and it won't use it, so it's a deeper problem than a simple missing driver file.

---

### Post by frantid on 2010-05-13
>  			 			 			 		   		 		 		...snip.... the Hardware Drivers said I had the nVidia driver  installed, but running nvidia-settings said that I did not. I tried  reinstalling the nVidia drivers a few times, with no luck.


I know he had other problems as well, the part above is what I thought was similar to yours, too bad it didn't work for you.

---

### Post by Envy Life on 2010-05-13
Thanks I did try all that was in that thread.  

I've read about an issue where the Hardware Drivers said the nvidia driver was not in use, when in fact it was, which is why I cross-checked with lscpi, which in my case is accurate.  

nvidia-settings also confirms that I'm not using the nvidia driver, but tells me to run nvidia-xconfig rather than to install it.  Doing that just leads to the "low resolution" X server prompt on a reboot because it can't locate the nvidia driver.

---

### Post by G-mL on 2010-05-15
I ended up finally getting my nvidia drivers to work. What happened was that I upgraded to Lucid from Jaunty and during the process, I chose to keep my modified menu.lst. Thus, the kernel that Lucid was booting into was not changed during the installation process. When I launched into Lucid, I was still on the only kernel (2.6.31-14). In a recent update, the kernel was upgraded (2.6.32-21 -> 2.6.32-22) and so the nvidia drivers got all screwed up. I manually changed which kernel I was loading into in my menu.lst file and updated grub and everything worked! The only thing I had to do was "remove" and "activate" the drivers after loading the new kernel.

---

### Post by bluesscream on 2010-05-16
I downloaded actual driver for my card from Nvidia's site. Removed all Nvidia related stuff in synaptic except nv or simply ```
sudo apt-get purge nvidia*
``` and installed the driver manually. There are countless howtos around. For me this did the job in my lucid amd64 environment for all kernels <2.3.33, even preempt and realtime. With jockey respectively hardware manager I rarely was lucky on up to date kernels.

---

### Post by Envy Life on 2010-05-27
To finalize this thread, I was able to isolate the issue to bad RAM.  This is after I ran memtest on two different occasions, once for over 12 hours, both error free.  BIOS didn't catch it either, but after pulling one bank of chips it appears the system has stabilized. Interesting, yet very frustrating exercise when almost all the symptoms appeared to be video/video driver related.

---

