---
title: "Freezing during install at 88%"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by CUrza on 2008-02-19
Hey everyone,
I'm dual-booting XP and Ubunty 7.10. I reformatted my whole drive, and made two 30GB partitions. First, I installed Windows on the first partition, no problems. Now I am trying to put Ubuntu on the second partition, but it is freezing at 88%. It says "importing documents and settings" and it's been here for about 15 minutes. Any ideas?

Also, it says I am installing the boot directory at hd0. Is that correct, or would hd0 be where my Windows install is? The two partitions are C and D, and Windows is already on C and functioning fine. Would I need to specify the boot program to install at hd1 for it to go onto D?

EDIT: Also, the install is ext3 at mount point "/". My Windows install is NFTS. Did I do this correctly, or should Ubuntu be something other than ext3?

---

### Post by mxg01 on 2008-02-21
Firstly, do you have lots of stuff in you 'My Documents' folder on XP? If so then it could be taking a while to copy over. Does the disk light flash during this time?

Otherwise you could run the install without selecting 'import settings'. If it completes then it's something dodgy in your 'My Docs' folder. You can manually move stuff over later. If it still hangs then it might be worth trying the alternate install CD.

Ubuntu uses file system EXT3 so that's fine. That partition won't be referred to D in Ubuntu though. As for booting, the install process will install GRUB which is a boot loader. This will (should) recognise your XP system and add that as an option on boot. When you boot you'll see a screen with the options on it. XP will be at the bottom and the default Ubuntu boot will be at the top. You'll have 10 seconds to change your mind otherwise it will boot into Ubuntu.

---

