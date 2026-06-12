---
title: "Radeon KMS in karmic ?"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Seren on 2009-09-09
I am not quite sure if radeon KMS will be enabled by default under Karmic.

Early discussions seemed to be positive about it, but we are relatively close to release now and as far as I know it hasn't been enabled by default yet. IIRC, it is already available from a PPA.

Is this planned for next alphas and betas ? or has it been postponed to Karmic+1 ?

---

### Post by inportb on 2009-09-09
As far as I recall... you gotta have some packages from the Xorg edgers repository for this to work properly. I haven't really pursued this as KMS is not one of my priorities... but it would be nice to have it.

---

### Post by Seren on 2009-09-10
To answer my own question I have found in wiki/kernel team status, the following information

> 
Good Progress KMS for Intel i915 enabled by default userspace drivers are KMS enabled, testing so far is good generally. KMS for ATI Radeon is now in the kernel with 2.6.31-rc based kernels, userspace support is now available in a PPA and expected to transition shortly, still disabled by default. KMS for Nouveau is not likely to make the Karmic kernel. Pushed test kernels with ATI Radeon and Nouveau -next updates, for xorg-edgers testing.


[https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Karmic#Milestoned%20features](https://wiki.ubuntu.com/KernelTeam/ReleaseStatus/Karmic#Milestoned%20features)

---

### Post by taavikko on 2009-09-10
The final release of 2.6.31 kernel will bring KMS for r1** - r5** chipsets.
r6** and up are expected in 2.6.32 (which will not be in 9.10)

Wheter KMS is enabled by default in final release of 9.10 is up to devs to figure out.

---

### Post by Slug71 on 2009-09-14
Any news about whether or not Radeon KMS will be enabled by default in Karmic?

---

### Post by Seren on 2009-09-15
Since kms is working for radeon R300-R500 based chipset but not yet for R600-R700 (it will be added in 2.6.32 kernel), I am not sure it will be enabled by defaut in Karmic in the end.

The information I have gathered from the kernel team meeting minutes are rather cryptic...

---

### Post by Jingo on 2009-09-15
If not enabled by default, what are the easy steps to enable it?

---

### Post by antiram on 2009-09-15
in a new /etc/modprobe.d/radeon-kms.conf
write
```
##enable KMS Radeon
options radeon modeset=1
```
sometimes needed:
```

sudo update-initramfs -k `uname -r` -u
```

or boot with kernelparameter
radeon.modeset=1

---

### Post by jerrylamos on 2009-09-15
radeon.modeset=1 works on my ati radeon mobility 7500.  

It does not in my ati radeon Xpress 200.

So far any time I've been able to get KMS to run on ATI or intel it's been a lot slower.  But the developers aren't done yet.

Jerry

---

### Post by Eestlane on 2009-09-16
I'm just warning that it didn't work with my 9800 PRO. Be sure to just test it with the radeon.modeset=1 in GRUB first.

---

### Post by inportb on 2009-09-16
lol... it made my LCD black and the backlight blink on and off :P
(that's with a x1250m)

---

### Post by omega_drh on 2009-09-17
FYI, I just tried this with the latest everything in Karmic today, and got the screen flashing off and on repeatedly on my Mobility Radeon 7500 (r100).
```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
	Subsystem: IBM Device [1014:0530]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR+ FastB2B+ DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 66 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 3000 [size=256]
	Region 2: Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon, radeonfb
```

---

### Post by angryfirelord on 2009-09-20
Hmm, this sounds interesting. Hopefully it'll work out of the box because I'd really like to play something like nexuiz on the open-source radeon driver. Phronix did some benchmarks back last year and nexuiz on mesa didn't score too well.

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_mesa_catalyst&num=2]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_mesa_catalyst&num=2")

Although 2.6.31 included some kernel level support already (if I'm not mistaken), so I'll try some testing myself. Right now, all I tested was Bzflag in 1680x1050 mode at high quality. In Ubuntu, I get around 10-25 fps, depending on the detail of the maps. In Vista, I get 20-45 fps. So it's really moving along quite well and in another year, we may be back to fglrx levels of performance.

---

