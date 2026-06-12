---
title: "Hardy alt-installer won't boot on Thinkpads?"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by SixedUp on 2008-08-03
I've been using Ubuntu for well over a year now, and have 4 Thinkpads and a home-brew server running on Gutsy. I recently dist-upgraded the server from Gutsy Server to Hardy Server over the network, and that went flawlessly.

However, when I tried the same with my daughters ancient Thinkpad 600, running Xubuntu (which is really only for her to write essays and browse the web on), we lost the networking. Rather than trying to piece it all back together I decided to do a fresh install of Ubuntu Hardy from a new CD.

I downloaded the ISO, verified the md5sum, and burned the disk at 4x.  The Thinkpad couldn't boot it, and I got the error "Cannot boot from this CD. Please try a BIOS upgrade" from ISOLINUX. I've rechecked the ISO (md5sum is still fine!), and burned another CD from it. This fails in exactly the same way. 

I've now tried these CD's in 4 different Thinkpads (2 x 600's, a T23 and a T60) ... they fail to boot in any of them, always suggesting that I need a new BIOS. HOWEVER, All those machines can boot just fine from older Gutsy Alt Installer CD's, and are at the most recent BIOS levels available to them.

The obvious conclusion is that ISOLINUX, or something it depends on, is seriously broken in the Hardy release (Gutsy used ISOLINUX 3.36, Hardy uses 3.53, current is 3.71 - 8 releases on). But I see very little reporting of problems with this in the forums, which suggests it's not the case. In addition, I *CAN* boot from my original 8.04 server disk (note, this is before the 8.04.1 point release, when there was only an 8.04 disk), which also suggests it may be more subtle than just a flaw with ISOLINUX.

Does anyone have any suggestions what else I can check / do?

---

### Post by SixedUp on 2008-08-05
Bump ...

---

