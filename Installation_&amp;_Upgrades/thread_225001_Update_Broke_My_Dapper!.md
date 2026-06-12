---
title: "Update Broke My Dapper!"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by gandalf2041 on 2006-07-28
I'm new to Ubuntu but, not to Linux. I've been running FC5 and decided to give Ubuntu a try.  I installed it on a Dell Dimension 8100 with a 3ware IDE Raid.  The installation went fine.  I spent some time customizing and then used the user's guide to get my codecs updated.  I followed the directions in the "How to Make Things Work in a Hurry" on the Restricted Formats Wiki. BOOM! When I reboot, I get to a point just before the GUI loads, and the computer hangs.  The light on the floppy is on constantly like it's being accessed but nothing is in the drive and the light never goes out.  It shouldn't be problem with the drive because I had rebooted several times before this update and I had done two prior without incident. I did add the Universe and Multiverse repos to get the gstreamer bad and ugly repos (per the Wiki instructions). Any help would be greatly appreciated.

---

### Post by Ziox on 2006-07-28
if you don't use you floppy that often, then i guess you can disable it in your bios. Also, if you can log in via the other consoles, the perhaps you can check the Xorg log /var/log/Xorg.0.log, and it should tell you what's wrong (though it's a mighty long file) (i'm guessing it's Xorg's fault...)

---

### Post by gandalf2041 on 2006-07-29
Thanks Ziox. It does indeed seem to be the floppy.  I disabled it in the BIOS and booted in just fine.  Guess I'll need to do some investigation.

---

