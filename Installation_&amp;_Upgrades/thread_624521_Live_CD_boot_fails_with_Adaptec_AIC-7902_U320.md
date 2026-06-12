---
title: "Live CD boot fails with Adaptec AIC-7902 U320"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by khosra on 2007-11-27
Hello.

I have a Sun w2100z with:

- Adaptec AIC-7902 Integrated Ultra320 SCSI Host Bus Adapter
- Ultra320 SCSI

The livecd doesn't complete boot. It pops me into the busybox initramfs prompt after scanning my one disk, a u320 SCSI (/dev/sda). No errors are displayed. The machine boots fine with the livecd with just pci=noacpi if I disable SCSI in BIOS.

I've tried unsystematically every boot option I can think of. It doesn't seem to be possible to disable scsi during the boot process (noscsi doesn't do anything) so I can at least fully boot the livecd and then load the scsi modules. If there is, please let me know.

Does anyone have suggestions? I have tried what was suggested here:

[http://ubuntuforums.org/showthread.php?t=280566]("http://ubuntuforums.org/showthread.php?t=280566")

Thanks!

---

