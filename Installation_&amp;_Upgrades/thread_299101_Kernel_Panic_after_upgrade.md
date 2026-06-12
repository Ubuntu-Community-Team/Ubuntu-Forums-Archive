---
title: "Kernel Panic after upgrade"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by 123dfdfg43 on 2006-11-13
Hi guys,

yesterday I upgraded to **Ubuntu6.10** and I encountered a big problem.
Linux doesn't boot any more with any kernel and I can read this error message before **kernel panic**:

[INDENT]
[   60.172608] parport: PnPBIOS parport detected.
[   60.172681] PNPBIOS fault.. attempting recovery.
[   60.172686] PnPBIOS: Warning! **Your PnP BIOS caused a fatal error.** Attempting to continue
[   60.172689] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[   60.172691] PnPBIOS: Check with your vendor for an updated BIOS
[   60.172695] PnPBIOS: set_dev_node: unexpected status 0x3a
[   60.172697] pnp: Failed to disable device 00:00.
[   60.172948] lp: driver loaded but no devices found
[   60.189746] mice: PS/2 mouse device common for all mice
[   60.228641] ieee1394: Initialized config rom entry `ip1394'
[   60.242402] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   60.307304] Linux agpgart interface v0.101 (c) Dave Jones
[   60.505209] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[   61.250989] EXT3 FS on dm-3, internal journal
[   61.354018] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   62.245684] cdrom: open failed.
[   70.177211] NTFS driver 2.1.22 [Flags: R/O MODULE].
[   71.828190] b44: eth0: Link is down.
[   73.824905] b44: eth0: Link is up at 100 Mbps, full duplex.
[   73.824909] b44: eth0: Flow control is off for TX and off for RX.
[  101.156643] NET: Registered protocol family 10
[  101.156809] Disabled Privacy Extensions on device c0321b80(lo)
[  101.158418] IPv6 over IPv4 tunneling driver
[  101.658566] Linux Kernel Card Services
[  101.658572]   options:  [pci] [cardbus] [pm]
[  101.662046] Intel ISA PCIC probe: not found.
[  101.662125] Unable to handle** kernel NULL pointer** dereference at virtual address 00000000[/INDENT]

I tried "pnpbios=off" with no result. My old Ubuntus worked very fine (only with "acpi=off" option).
I already tried to reinstall ubuntu6.10 from official CD and apparently new kernels can't boot on my pc.

Here's my hardware:
[INDENT]
* CPU:                  Athlon XP+ 2400
* MOTHERBOARD:          motherboard ASUS A7V8X
* SCHEDA AUDIO:         Creative SoundBlaster Live! 1024
* SCHEDA VIDEO:         nVidia GForce4 Ti 4200 128MB
* HARD DISK:            Fujitsu MPF3204AT [20GB]
* MONITOR:              philips brilliance 109P 19'' (H 30-111, V 50-160)[/INDENT]

Thank you in advance,
Andrea

---

### Post by AgenT on 2006-11-15
Assuming that the kernel giving you problems is 2.6.17-10-generic (x86). Assuming your root partition / is on /dev/hda1.

NOTICE: Instructions below say to use su, if this fails, use sudo with the next line below the su command instead like so: sudo mkdir....

Boot your favorite Debian (based) LiveCD and start a terminal (Knoppix is always reliable):
```
su -
mkdir -p /media/ubuntu
mount /dev/hda1 /media/ubuntu
chroot /media/ubuntu
```Now do a test:
```
echo "bbb" < /dev/null
```If you do not receive an error, continue. If you do receive an error, something is wrong with your permissions. Make sure you were root before you executed chroot!
```
apt-get update
apt-get install --reinstall linux-image-2.6.17-10-generic
exit
cd /
umount /media/ubuntu
shutdown -r now
```Reinstalling the linux-image package not only reinstalls all the files, but also updates a lot of programs that may be causing the kernel panic.

---

