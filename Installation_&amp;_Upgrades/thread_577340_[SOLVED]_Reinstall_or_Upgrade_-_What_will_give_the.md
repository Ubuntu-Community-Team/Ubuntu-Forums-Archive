---
title: "[SOLVED] Reinstall or Upgrade - What will give the expected result?"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by Zugzwang on 2007-10-16
Hi experts,

Since in 2 days the latest version is coming out, I'd like to give it a try. My last Ubuntu didn't fully work, mainly because Wireless LAN configuration did only work using some tweaked shell script I copied from some forum (It was supposed to automatically book into a couple of different nets just like Win XP does) and the X-Server configuration was somewhat flawed (Laptop, internal screen was 16:10 but I frequently use external 4:3 screens).

So I've got two possibilities:
- upgrading
- reinstalling

In the first case, I'm afraid that the new stuff (improved network manager including WPA support) and multi-screen-manager doesn't work as it would in a new installation. Anyway, I forget where I made changes in the configuration files and where I put the shell script.

In the second case, I'd like to avoid burning a CD (and if possible, also using a USB flash drive, I'm not even sure if that works with my Laptop). Since the last Ubuntu version was hardly usable for me, there is no data to keep (however, the Windows installation should remain intact). The installer shouldn't touch the Windows partition since no re-partitioning is neccesary, right?

Which method would you prefer and how do I circumvent the given problems for the two methods?

Cheers and Thanks! :wink:

---

### Post by PmDematagoda on 2007-10-16
I think you would have better luck with installing a fresh Gutsy Gibbon:) since an upgrade may, in your case, cause more problems than solve them. About the partitions, yes, you should be able to install Ubuntu on your existing Ubuntu partitions without touching your Windows XP installation.

---

### Post by r!ots on 2007-10-16
if i do a reinstall and i want to keep all my preferences and especially my thunderbird profile can i just copy my /home directory before reinstalling and then move it back after the reinstall?

---

### Post by Zugzwang on 2007-10-17
r!ots, yes, you can as far as your settings are user-dependent (which applies to the Thunderbird profile). So any setting which is not set for a new user account if you create one remains.

However, if you upgrade your distribution and the new version of program XY uses a different configuration file format, you may lose some of it (depends on the programs). One example is a saved GNOME session which wasn't readable after the upgrade anymore. But Thunderbird & Firefox  should be fine.

System-wide settings like which packages you installed, which mount points you have and driver configuration will be erased.

---

### Post by cuby on 2007-10-17
Update from CD.... 
Download the alternate CD installation.
If the upgrade fails the cd for a reinstall is already with you.

---

