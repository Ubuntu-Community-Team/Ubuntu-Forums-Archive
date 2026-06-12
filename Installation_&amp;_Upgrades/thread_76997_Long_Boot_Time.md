---
title: "Long Boot Time"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by Tralobyte on 2005-10-16
When Breezy starts up, it first says it's uncompressing and booting the kernel. Then it says "Loading, please wait..." and stays there for around 50 seconds. The whole boot time to the login screen takes a little over 2 minutes. It's not much of a problem except for the initial hang right after booting the kernel. Anyone else having the same problem?

---

### Post by pardasaniman on 2005-10-16
Yes.... Try disabling "queit" and "splash" on your boot settings...

From the top of my head:  <--I may be very wrong.
When you are presented with the grub boot menu to select your OS, hit e on the kernel you want to boot, and then hit e on the kernel boot parameters, remove splash and quiet, and then hit enter, then hit b to boot the kernel.  

Now when the kernel boots, you should be able to visibly see where it hangs, tell us here, and submit a bug report of necessary.

--Good Luck!!

---

### Post by Tralobyte on 2005-10-16
Thanks for the bug finding technique. The relevant part is below. Note that I editted it to say where it hangs.
```

 Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
 ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
 ACPI: bus type ide registered
 ide0: I/O resource 0x1F0-0x1F7 not free.
 ide0: ports already in use, skipping probe
 ide1: I/O resource 0x170-0x177 not free.
 ide1: ports already in use, skipping probe
#####THIS IS WHERE IT HANGS#####
 Probing IDE interface ide2...
 Probing IDE interface ide3...
 Probing IDE interface ide4...
 ide4: Wait for ready failed before probe !
 Probing IDE interface ide5...
 SCSI device sda: 195173685 512-byte hdwr sectors (99929 MB)
 SCSI device sda: drive cache: write back
 SCSI device sda: 195173685 512-byte hdwr sectors (99929 MB)
 SCSI device sda: drive cache: write back
  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3
 Attached scsi disk sda at scsi0, channel 0, id 0, lun 0

```

---

### Post by pardasaniman on 2005-10-16
Something similar happened to me in Kernel 2.6.10 , it was fixed with booting with ide2=noprobe ide3=noprobe ide4=noprobe ide5=noprobe.

Also, do you have a scsi disk?  if not, do you have a USB key in there?  Try removing it and rebooting.

It may be worth submitting a bug on bugzilla.

Good Luck!

---

### Post by Tralobyte on 2005-10-16
Sorry, but adding that line didn't work. And I'm pretty sure it is a SCSI drive.
Here's what my grub looks like:
```

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro ide2=noprobe ide3=noprobe ide4=noprobe ide5=noprobe #quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot
```

---

### Post by pardasaniman on 2005-10-17
Hmm... I'm stumped.  It's must be a damn annoying problem though.

Is it still probing for ide2,ide3,ide4, and ide5 like before?  I don't think that should be happening.

I think it may be worth submitting a bug report.

---

