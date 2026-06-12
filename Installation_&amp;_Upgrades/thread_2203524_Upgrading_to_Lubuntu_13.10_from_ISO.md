---
title: "Upgrading to Lubuntu 13.10 from ISO"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by BigBadWoofer on 2014-02-03
My system is currently running Lubuntu 12.04 that I have installed from a Live CD. Seems to be working fine. Since it is an older system the BIOS do not include a boot from a USB memory stick. I have found the other treads about using GRUB2 to boot from an ISO file. I have downloaded the ISO for Lubuntu 13.10 and placed it on my hard disk and create the GRUB menu entry.

I can boot in the ISO and it starts to run. The log of activity comes out in text mode. It scrolls by pretty ast but I don't notice any obvious error messages. I think it reaches the point when it wants to switch to graphics mode. My monitor goes blank and I hear several clicks coming from the monitor as it resets. However, the monitor shows a large number of vertical green bars covering the top third of the screen. And that's it :(. I have to reset the system to continue.

Do I have to tweak the monitor settings in the ISO before booting it? If so where would I find there to do that? Or what else do you suggest?

lspci shows "VGA compatible controller: S3 Graphics Ltd. VT8375 [ProSavage8 KM266/KL266]"
What other info would be helpful?

---

### Post by mörgæs on 2014-02-05
Upgrading from 12.04 to 13.10 is a long step and likely to fail. 
I suggest a fresh install using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO").

---

