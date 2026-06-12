---
title: "Delay and black screen on ASRock G41M-LE"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by sreym on 2009-12-30
I have been installing 9.10 on motherboard ASRock G41M-LE. First, i got a 3 min delay while loading from LiveCD, then it shows glowing Ubuntu symbol and after a while - black screen. Nothing else happens after it and nothing works.
 
Same problem happens after installing alternate version.
 
Delay is after this message:
 
```
 
[    0.992981] [drm] Initialized drm 1.1.0 20060810
[    0.999846] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.999896] i915 0000:00:02.0: setting latency timer to 64
[    1.004803] [drm:i915_driver_load] *ERROR* Detected broken video BIOS with 262140/262144kB of video memory stolen.
[    1.004874] [drm:i915_driver_load] *ERROR* Disabling GEM. (try reducing stolen memory or updating the BIOS to fix).
[    1.004953]   alloc irq_desc for 27 on node 0
[    1.004955]   alloc kstat_irqs on node 0
[    1.004962] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[    1.004979] BUG: unable to handle kernel NULL pointer dereference at (null)
...
[    1.008928] ---[ end trace 10d579ba18744bf5 ]---

```

I tried to blacklist video, i915 - nothing worked.
 
Attached file contains logs.
 
Thank you in advance.

---

### Post by kras1001 on 2010-01-05
I have the same Motherboard ASRock G41M-LE and the same problem. Video is Intel GMA X4500.
Updated BIOS to ver. 1.90 (last version): from here [http://www.asrock.com/mb/download.asp?Model=G41M-LE&o=All](http://www.asrock.com/mb/download.asp?Model=G41M-LE&o=All)
Here is output from dmesg command:
> kras@kras-desktop:~$ dmesg | grep drm
[    1.138666] [drm] Initialized drm 1.1.0 20060810
[    1.146944] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    1.156980] [drm:i915_driver_load] *ERROR* Detected broken video BIOS with 262140/262144kB of video memory stolen.
[    1.156982] [drm:i915_driver_load] *ERROR* Disabling GEM. (try reducing stolen memory or updating the BIOS to fix).
[    1.157062] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
and
> kras@kras-desktop:~$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "i810" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
(EE) intel(0): [drm] Failed to detect GEM.  Kernel 2.6.28 required.
(EE) intel(0): Failed to become DRM master.
(EE) intel(0): Failed to initialize kernel memory manager

and
> kras@kras-desktop:~$ cat /var/log/Xorg.0.log | grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Warning, couldn't open module i810
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x61110 (PORT_HOTPLUG_EN) changed from 0x10000120 to 0x30000120
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x10000b00 to 0x30000b00
(WW) intel(0): DRI2: failed to open drm device
(WW) intel(0): drmSetMaster failed: Bad file descriptor


The only way to boot in X is whit this option in second row in GRUB - **i915.modeset=0** 

HELP PLEASE

---

### Post by sreym on 2010-01-05
Ooops, I forgot that I'd upgrade BIOS too.

---

### Post by sreym on 2010-01-05
> The only way to boot in X is whit this option in second row in GRUB - i915.modeset=0 
And why it isn't suitable for you?

---

### Post by kras1001 on 2010-01-05
> **sreym said:**
> And why it isn't suitable for you?

Because Video is very slow!
Everything refresh slowly, when minimize and maximize windows, and there is no 3D acceleration even i thing no anything graphical acceleration  ... Sorry bad English... You know I mean!
In my language(Bulgarian) this call - shibana rabota!

---

### Post by sreym on 2010-01-05
Hmmm... May be problem could be solved by last driver for Intel cards (beta, alpha, even pre alpha). I will try it if find proper driver.

---

### Post by kras1001 on 2010-01-05
> **sreym said:**
> Hmmm... May be problem could be solved by last driver for Intel cards (beta, alpha, even pre alpha). I will try it if find proper driver.

I think maybe in kernel 2.6.33 and intel video driver ver.2.10 this problem will be solve.
I use Archlinux with kernel 2.6.32 and xf86-video-intel 2.9.1-1 and have same problem. Maybe Ubuntu 9.10 solve this problem in next driver or Xorg update(I use Ubuntu 9.10 and ArchLinux - who will fix bug first:)?).
Please if you find decision of problem write me in e-mail: kras1001 __at__ mail.bg ( __at__ =@).

---

### Post by kras1001 on 2010-01-18
I found a partial solution for problem.
In BIOS --> Advanced Screen --> PAVP Mode(Disabled) and Primary Graphics Adapter = Onboard and Share Memory = 128MB. Remove i915.modeset=0 from GRUB.
Try it and say is that work for you.
Sorry for my bad English!

---

### Post by stitch on 2010-02-01
Hi Kras1001, thanks it worked great for me :)

Ciao/Stitch

---

### Post by drondron on 2010-04-19
> **kras1001 said:**
> I found a partial solution for problem.
In BIOS --> Advanced Screen --> PAVP Mode(Disabled) and Primary Graphics Adapter = Onboard and Share Memory = 128MB. Remove i915.modeset=0 from GRUB.
Try it and say is that work for you.
Sorry for my bad English!


Thx, works fine on Asrock G41M-S. Can begin installation :)

---

### Post by ILMV on 2010-05-20
Just surfed in from Google after hours of research, and glad to say that kras1001 has provided the answer for my problem too!

I'm building two servers based on the ASROCK H55M motherboard and been having the same problems and using the i915.modeset=0 in the grub config to get a screen to display.

After changing the BIOS settings as suggested we are now able to boot to a desktop.

So once again, cheers kras1001!

---

### Post by drinden on 2010-08-04
Thank you [kras1001]("http://ubuntuforums.org/member.php?u=360629"). You are the best. I searched and tried different solutions for hours. Could not get it do work until I saw your answer on this thread. 

It took a long time before I thought of searching for ASRock G41M-LE.

---

### Post by evg219 on 2010-11-09
> **kras1001 said:**
> I found a partial solution for problem.
In BIOS --> Advanced Screen --> PAVP Mode(Disabled) and Primary Graphics Adapter = Onboard and Share Memory = 128MB. Remove i915.modeset=0 from GRUB.
Try it and say is that work for you.
Sorry for my bad English!

A lot of thanks to **kras1001**!
ASRock G41M-LE, video onboard, Ubuntu 10.04 LTS. I had 1 memory module installed and everything worked fine without customizing BIOS. But after installing 2x1GB dual channel system failed. Only above settings make system load normally.
P.S. Who knows, pls tell me name of the file, where should be string with "i915.modeset=0". In grub.cnf (10.04) there is no such string. Anyway, system loads :) .

---

