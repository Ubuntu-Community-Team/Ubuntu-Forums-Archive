---
title: "G5 Power Mac Rejects Linux Discs"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by Chucklz15 on 2013-01-25
Hello all,

I'm trying to slap a nice version of ubuntu onto this G5 Power Mac I have (PowerPC G5 3.0, 1.8GHz, 2GB RAM, 200GB HDD, GeForce FX 5200) but I'm having a problem booting from the disc.

I was given a copy of MAC OS X (10.3.5) when I bought it (second hand from my school) and I managed to install MAC perfectly fine. The problem occurs when I try to boot from a linux-type disc, or even MAC OS X 10.6 (leopard...not that I want MAC OS anyway hehe).

When I insert the disc and reboot the computer, I hold down 'c' but no dice. The screen sits grey for a sec while the CD spins but it will just eject the disc and carry on into MAC OS.

I was able to install Linux on one of these G5's before, but now it's not working. Am I forgetting a step? :confused:

---

### Post by Easy Limits on 2013-01-25
Are you sure you have the PPC version of Ubuntu?  CD/DVD drive could be failing?

---

### Post by gifford on 2013-01-25
There is an Apple forum here that may offer better help for PPC. I would agree with the checking of version of the disk to make sure it is PPC version.
I believe that Leopard will not install nor work on a PPC chip, only Intel.

---

### Post by Chucklz15 on 2013-01-25
Got ubuntu 12.04 installed. Problem is, I get that questionmark/dirty-apple-grin folder icon A.K.A yaboot has a problem, or the device isn't correctly configured. Working on the currently...

---

### Post by Chucklz15 on 2013-01-26
UPDATE:

Got the yboot configured correctly...well sorta.

I actually had to create my own yaboot.conf because for some reason the installer didn't make one.

I finished setting it up, and for my image location I used:

```

image=/vmlinux
	label=Linux
	initrd=/initrd.img
	append="quiet splash"
	read-only

```

Now when I boot, I enter "Linux" into the prompt then it tells me this:

```

boot: Linux
Please wait, loading kernel...
   Elf kernel loaded...
Loading ramdisk
/ht/pci@3/k2-sata-root/k2-sata@0/disk@0:3,\initrd.img: No such file or directory
ramdisk load failed !

```

Then drops me in the OF prompt. I checked my files when I go into the live-cd and vmlinux and initrd.img are both on root. Maybe I'm using a wrong vmlinux?

---

### Post by Chucklz15 on 2013-01-27
I gave up and installed 12.10 via the alternate install (also solved the reject disc problems, apparently my drive only likes to boot dvds...)

The yaboot was configured correctly and the boot worked, the problem now is that it hangs right after

```

*Starting crash report submission deamon [ OK ]

```

Quite ironic I thought...

---

