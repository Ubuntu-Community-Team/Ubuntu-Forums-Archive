---
title: "Installation of Lubuntu without disc"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by Chuckymong on 2012-10-05
Hello, my PC currently has no OS installed therefore I could not download a copy of lubuntu. I asked a friend to download me a copy and burn it to CD and post it to me. When i received the copy I try to install it which failed. Then i booted the "Try Lubuntu" which worked where I noticed I could install it from there. I tried this but again it failed.

Then I used the check disc for defects option upon boot and found that there is an error.

My query is - Can i download the lubuntu ISO using the "Try Lubuntu" feature, and then install it without having to burn it to disc due to the fact I do not have a CD-RW drive?

Thanks in advance Marcus.

---

### Post by The Cog on 2012-10-05
I can't think of any way to download and then install directly. The nearest I can think of is to download your own copy of the ISO (to memory) and then use the startup disk creator to create a bootable memory stick.

---

### Post by oldfred on 2012-10-05
It is a bit advanced.

You could create a 1 or 2GB partition with gparted from liveCD, install grub2 to the drive and then use this procedure:

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Change to make grub in MBR boot from a dedicated grub only partition on drive., but then add ISO file(s) as above. You also have to manually create the grub.cfg file:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

