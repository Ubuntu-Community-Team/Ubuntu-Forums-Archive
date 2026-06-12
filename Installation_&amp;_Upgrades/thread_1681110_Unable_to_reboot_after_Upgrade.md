---
title: "Unable to reboot after Upgrade"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by DaveH77 on 2011-02-03
This has happened twice now and I can't find this problem described anywhere.
 
Tuesday:
I have a brand new disk installed from an Ubuntu 10.04 LTS Live CD.
Everything worked just fine. 
 
Rebooted.
Everything worked just fine.
 
Thursday
This morning it did a system update.
Everything worked just fine
Moved files across from an old drive - into the home directory - no system stuff
Did some compiles, etc 
 
Rebooted the computer
Not so fine.
 
On reboot I get the BIOS screens and then I get a blinking underscore cursor in the upper left. It then changes resolutions and I still have the blinking underscore. Nothing else. Hitting ESC at any time doesn't get me a grub menu or an alternate boot sequence.
 
If I boot from the Live CD I can mount the disk and everything is there - just no sign of booting at all.
 
Any ideas?
 
OK - i found the Grub2 instructions to use Shift instead of ESC.  Now it changes resolutions and comes up with 
 
mountall:Disconnected from Plymouth
 
Which led me to try this
 
sudo mount /dev/sda1 /mntchroot /mntThen I

Code:
sudo mount /dev/sda1 /mntchroot /mntThen I
Code:
sudo apt-get install updatesudo apt-get install -fsudo dpkg-reconfigure plymouthsudo dpkg-reconfigure gdm

 
with still no luck booting from either the kernel or the recovery kernel.

---

