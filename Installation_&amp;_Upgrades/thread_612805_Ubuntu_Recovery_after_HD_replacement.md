---
title: "Ubuntu Recovery after HD replacement"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by mvanner on 2007-11-14
I had system hard disk failure that would result in a the drive going dead after running for a while (and Ubuntu really doesn't like dead devices!). After a power off reset the drive would run long enough for me to do a full tar back-up of the drive and copy the resulting tar file to a network attached drive. I picked-up a 500gb replacement for the 160GB failing drive. Installed Ubuntu 7.10 and then copied the tar back from the network drive and restored. Now the new drive won't boot into Ubuntu. I updated the /etc/fstab with the new partition information.
When I run in recovery mode it appears Ubuntu is trying to access a drive that doesn't exist. Eventually I get into the initramfs [busy-box].
I haven't checked casper.log, but I suspect it will tell me about trying to install or mount a device that doesn't exist. Does anyone have any suggestions as to what config file(s) I need to change to get the boot to continue?
I could wait until the 160gb drive replacement arrives from Seagate and try again. But I'm the curious type would like to understand the start-up process better anyway.

---

### Post by Fire_Chief on 2007-11-14
You probably need to update your GRUB settings in /boot/grub/menu.lst
Boot from the LiveCD then check the entries to verify that it is pointing to the correct partitions and the correct kernel.

---

### Post by mvanner on 2007-11-15
Updated the grub settings and that didn't fix the problem.

Tried a reinstall which worked fine and then a recover from the tar not restoring /boot or /etc/fstab, but everything else and that had the same effect. Still won't boot. Is there another file I shouldn't have replaced, vmlinuz for example?

---

