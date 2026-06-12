---
title: "Install from USB drive, can't boot"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by [h2o] on 2007-06-18
I have followed the guide in the wiki ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)) but I have some troubles.

First, the drive did not automatically mount, and I was unable to mount it. So, I formatted it by running mkfs -t vfat /dev/sdb1 and after that it showed up as usual.

Then I installed syslinux and tried to reboot. In my BIOS the drive showed up as a harddrive and not "removable drive", but choosing to boot from it resulted in a black screen with some text flickering in the bottom right corner (looked like "______" most of the time, but flickering).

The "boot:" prompt that the wiki said should show up did not...

I thougt that it might have to do with having nothing to boot, so I copied the contents of the alternative disk to the memory stick and trioed to boot. Now, in BIOS it did suddenly show up as removable drive and not harddrive like before, but it did not boot from it (removable drive was first boot option).

Any ideas what might be wrong? Since I'll be installing Ubuntu on a computer without CD- or floppydrive I really need to be able to somehow install from a USB stick.

---

### Post by Ahab the Eskimo on 2007-07-07
I too am frusterated and I wish someone would post the code for a Ubuntu/Kubuntu Alternate install syslinux.cfg so that I can copy and paste it. 

That or Prescott motherboards are too old (I doubt it)...

(I have spent a week trying 8-10 *different* tutorial with no success)

---

