---
title: "kernel 2.6.22-14.46 in alternate/live oopses"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Francesc Oller on 2007-10-29
I've a kernel oops when trying to install with gutsy/alternate. Problem is the same as Plamen Atanassov: [http://https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/152820]("http://https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/152820") which I'm including:

cut here -----------------------------------------------------------------------------------------------
2.6.22-14 has rendered my PC unbootable too. This is true for both i386, and AMD64 flavors of the kernel.

The problem appears when it tries to load the ide drivers for the disks I have. Modprobe exists abnormally,
and there's no ide support, so can't be booted. The kernel dumps to busybox.

There are a bunch of messages. The first, which seems a bit unrelated as it is a bit further up the log is:

[xxxx] BUG Unable to handle kernel NULL pointer dereference at virtual address 000000000

A bit further down we have modprobe trying to insmod ide_disk but fails, and exists anormally.

Stacktrace given:

[xxx] ide_in_drive_list 0x45/0x80 [ide_core]
[xxx] idedisk_check_hpa [ide_disk]

The stacktrace continues and I can add more if its needed (gotta do it by hand)

Some info on my hardware

00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

This problem did not exist on 2.6.22-12-i386
cut here -----------------------------------------------------------------------------------------------

Also true for -generic, which is mine.

I've same south/north bridge: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C

Some questions:

  1.- Is there an easy way to build 2.6.22-12-generic, which is no more in repositories?
  2.- Does anybody know a workaround?

Regards

Francesc Oller

---

### Post by Francesc Oller on 2007-10-29
I know more things now :)

The problem has to do with the 40GB ST340823A hard drive, if I substitute a 40GB ST340014A for it all goes well.

Looking at linux-image changelog.Debian.gz I find:

--------------------------------------------------------------------------------------------------------------
linux-source-2.6.22 (2.6.22-13.40) gutsy; urgency=low
...
  [Bartlomiej Zolnierkiewicz]

  * ide-disk: workaround for buggy HPA support on ST340823A (take 3)
    - LP: #26119
---------------------------------------------------------------------------------------------------------------

and some similar changes.

So, it seems to be a bug which appears when trying to fix another.

What to do in this case?

Regards

Francesc Oller

---

### Post by Francesc Oller on 2007-11-01
The issue is solved. Bug and workaround at:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156428]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/156428")

Cheers

Francesc Oller

---

