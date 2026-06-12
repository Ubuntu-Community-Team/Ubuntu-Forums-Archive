---
title: "Updating Persistent USB Flash Drive"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by WilhelmGGW on 2012-06-11
I used the Pendrive USB Installer to create a persistent USB flash drive, so I could run Ubu12.04LTS on a Dell Mini-9 with a broken SSD. Everything works fine *except* doing a system update (250 files!) and new program installations. It's like they *almost* complete well, but they hang up and don't fully install.  It *seems* like the issue has something to do with installing the new kernel and other packages not being able to hang their hats on it.

Observation: When I couldn't get things to work right with my first Pendrive installation to the USB, I tried it again. For this go around, I decided to NOT install any new programs nor start the Update Manager myself.  Now several hours in, the Update Manager has still not started by itself, quite differently than what happens (I think) when one installs Ubuntu directly on a PC (with hard drive). That makes me wonder whether it's to be used at all when I run the OS from the flash drive.

Is there a way to fix this -- so I can install new software and keep everything entirely up to date? Or are changes to the initially installed OS disallowed somehow, or crippled -- as I just explained?  Is there anything I can do about this?  A big Thank You to anyone who can help.

---

### Post by efflandt on 2012-06-11
Bootable iso on USB is intended for testing Ubuntu on systems, installing it, or using it for rescue/repairs.  Things that happen during boot are on a fixed squashfs file system that boots before persistent data is mounted.

While you can install programs that you launch after booting, and store certain system settings (timezone, wireless security, additional users) in persistent data, you cannot install or update things like kernel, video drivers, etc. that initially happen during boot.  It is also totally insecure in that it boots without a password to a user (ubuntu) who is effectively admin.

So if you want to use it securely regularly and want to be able to update it, you should really do a regular install (8 GB minimum recommended).  However, for the partitioning portion of install, make sure that you select "Other" to do the partitioning yourself, and select from the drop down list there to **put grub on the mbr of your USB flash drive** (not worded that way, but select the proper drive).

---

### Post by WilhelmGGW on 2012-06-11
Thanks so much. Timely and thorough response.

---

