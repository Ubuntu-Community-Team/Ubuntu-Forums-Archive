---
title: "Ubuntu 14.10 Doesn't Boot After Installation"
date: 2014-11-19
forum: Installation &amp; Upgrades
---

### Post by okeydokey2011 on 2014-11-19
Hi all, I'm a new user of Ubuntu & I'm having problems getting it to boot after installation. Any help would be appreciated. I've already run the Boot Repair & have a link of the report which tells me "Boot Successfully Repaired" so I'm now confused :p [http://paste.ubuntu.com/9099464/](http://paste.ubuntu.com/9099464/)    


Thanks Nic.

---

### Post by oldfred on 2014-11-19
Your install looks normal.
But which flavor are you installing. Full Ubuntu is more for newer hardware and you may need Lubuntu or Xubuntu.

But with just Ubuntu installed it will not normally show grub menu, as you only have one standard option. You then need to hold shift key from BIOS until menu appears.

It looks like you have an old nVidia card. GeForce 6150SE

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You then will need to install a legacy nVidia driver and in System settings it should offer the correct one, but verify which is correct.

 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
        [http://www.geforce.com/drivers](http://www.geforce.com/drivers)
    
Also since old video, what are other specs of system?

---

