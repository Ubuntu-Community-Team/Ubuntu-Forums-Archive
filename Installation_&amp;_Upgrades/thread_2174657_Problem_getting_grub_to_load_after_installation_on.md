---
title: "Problem getting grub to load after installation on UEFI system"
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by stephen16 on 2013-09-15
Hello,

I followed the instructions found here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), but when I start up the computer, it goes directly to Windows, without the Grub ever showing. Here is the link given to me by the boot repair process: [http://paste.ubuntu.com/6111772/](http://paste.ubuntu.com/6111772/)

I appreciate any help.

---

### Post by ajgreeny on 2013-09-15
Try setting your second hard drive as the priority boot device.  Grub is installed to sdb not sda, so that is the first thing to do.  Come back again if that is not the answer.

---

### Post by oldfred on 2013-09-16
You are showing grub legacy on sdb. That must be an old drive. Also XP does not read gpt partitioned drives.

You show grub in the efi partition. It usually does not auto boot ubuntu after install, you have to go into UEFI menu and choose the ubuntu entry or try the one time boot key to test booting of ubuntu entry.

Boot-Repair has added correct entries for Windows UEFI boot. But os-prober creates BIOS boot entries that will not work.

It also looks like os-prober found all your old installs on sdb. But if booted in UEFI mode, you probably cannot use any of those entries as they need BIOS/CSM mode. If you have a working BIOS boot in sdb, then from UEFI/BIOS using CSM mode should be able to boot sdb installs, but then will not be able to boot any installs in sda.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry from os-porber that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

