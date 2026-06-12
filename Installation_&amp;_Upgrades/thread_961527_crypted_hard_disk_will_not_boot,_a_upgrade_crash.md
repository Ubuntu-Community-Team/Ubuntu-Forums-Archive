---
title: "crypted hard disk will not boot, a upgrade crash?"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Valir on 2008-10-28
--------------------------------------------------------------------------------

Hi, 

Urgent help needed! Please help

my hardy studio rt kernel will not boot. Can anyone help me fix the specific problem, or alternatively tell me how I can salvage my data from my home folder before doing a clean install?

I have a hardy installation with a crypted hard drive. Been working fine (with some hickups on shutdown, a problem related to networkmanager, but it was solved, and I am not sure if has anything to do with this)

Now, my computer stalled and after a forced restart the system will not boot. 

It might have happened after an upgrade, but I have restarted a few times since last.

_____This is what happens if I boot in recovery mode_____

Enter LUKS passphrase: (I enter password)

then later: [15.874579] padlock: VIA PadLock Hash Engine not detected.
modprobe: WARNING: Error inserting padlock_sha (/lib/modules/2.6.24-21-rt/kernel/drivers/crypto/padlock-sha.ko): No such device

key slot 0 unlocked
command successful.
cryptsetup: failed to setup lvm device.
Done.
Begin: waiting for root file system .... ...
Done.
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
Reading all physical volumes. This may take a while...
Found volume group "ubuntu" using metadata type lvm2
ALERT! /dev/mapper/ubuntu-root does not exist. Dropping to a shell!


..................................

Ok, here comes BusyBox
(initramfs)

But if I can´t cd to anything, and dir gives me /bin/sh and dir: not found.

.................

What is happening?


Help would be greatly appreciated.

p.s. My battery is not working, so the computer has sometimes been abruptly turned off, maybe this has done some damage to the filesystem?

---

