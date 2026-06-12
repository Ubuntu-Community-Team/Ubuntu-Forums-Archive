---
title: "Unable to boot after 16.04, boot-repair made it worse"
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by Zeophlite on 2016-05-01
I recently upgraded from 14.04 to 16.04, and after doing so, I would reboot into GRUB, select Ubuntu, then get a fdisk error

Using a live USB for 16.04, I used boot-repair.  After running that, I now reboot into Ubuntu and get just a black screen, with no further information

boot-repair log: [http://paste2.org/WZVa9OO8](http://paste2.org/WZVa9OO8)

Machine has Windows 10 dual boot, which loads correctly.

Any commands I should run from the live USB to help debug this?

---

### Post by oldfred on 2016-05-01
Have you tried nomodeset?

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

Do not know about AMD.
      
 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu

---

