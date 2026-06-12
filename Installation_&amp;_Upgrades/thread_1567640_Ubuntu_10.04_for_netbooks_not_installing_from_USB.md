---
title: "Ubuntu 10.04 for netbooks not installing from USB"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by mario.r on 2010-09-04
I have a netbook with 8.1 on it.  I downloaded 10.04 for netbooks and created a bootable USB drive as per the instruction on the sowload site, with my new iso image for 10.04.  Set the boot sequence to look at the USB flash drive first.

When booting the netbook, first line says: ***Pen Drive without operating system. Remove pen drive and reboot. GRUB loading stage 1.5.***

It then boots from the hdd.

On my desktop I then get a message saying installation failed and that I should look at the USB log file.  The file's contents look like this:
[I][B]
-- Starting up at 23:15:17 --
[23:15:17] new device:
{'capacity': dbus.UInt64(4082102272L), 'uuid': 'A890-BB5E', 'label': '', 'free': 3165224960L, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_A890_BB5E'}
[23:15:17] adding: /dev/sdb1
[23:15:37] mounting /home/user/Desktop/ubuntu-10.04-netbook-i386.iso
[23:15:37] updating dest_status as part of update_row_state
[23:15:47] Installing...
[23:15:47] Source CD: /home/user/Desktop/ubuntu-10.04-netbook-i386.iso
[23:15:47] Destination disk: /dev/sdb1
[23:15:47] Persistence size: 318 MB
[23:15:47] Marking partition 1 as active.
[23:15:47] installing the bootloader to /dev/sdb1.
[23:15:49] ['/usr/share/usb-creator/install.py', '-s', '/tmp/tmpM6fYjA/.', '-t', '/media/disk', '-p', '318']
[23:17:27] Unmounting source volume.
[23:17:27] Install command exited with code: 256
[23:17:27] Forcing shutdown of the install process.
[23:17:27] Unmounting source volume.
[23:17:27] Install failed.[/B][/I]

Any ideas please?

---

### Post by mario.r on 2010-09-04
Does anybody have any advice please???

Frustrated beyond belief!!

---

### Post by C.S.Cameron on 2010-09-04
Have you checked the MD5SUM of the downloaded iso?
Bad downloads are often a problem.

---

### Post by mario.r on 2010-09-04
What is the MD5SUM and how do I check it?

---

### Post by robert leleu on 2010-09-27
My laptop is presently 10.04, and I never created boot-USB sticks.
However it delivers the same message at start-up.
Ther is an USB stick permanently attached (I use it for backups)

---

