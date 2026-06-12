---
title: "Stuck boot after 14.04.1 installation/upgrade"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by graham18 on 2015-01-04
Been running 13.10 for a long time .. ran the upgrade and on first boot got the attached screen. Downloaded the ISO and did a clean instalation and got the same. If I run 14.04 from DVD it runs.

a bit perplexed to say the least as 14.04 upgrated on my other machine without problem.

---

### Post by oldfred on 2015-01-04
Can you right click? And then in changing screen, get to system settings?

I had that once, and related to video driver. What video card/chip do you have. 

Once I installed the proprietary drivers from nVidia for my card it worked.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

