---
title: "Upgrade/install Hardy-&gt;Intrepid. OS and /home partition from livecd?"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2008-10-24
Here's the deal.
I have hardy installed, with a partition for the OS and a /home partition for data. I also have some windows partitions but I'm leaving them alone.

I downloaded the live cd.
Can I install fresh intrepid onto ubuntu partition (format/install) while keeping my /home directory intact and settings saved? Can this be done with live cd?

Do I need the alternate CD in order to upgrade hardy to intrepid while retaining my /home partition with settings and data? I don't plan on upgrading over the internet since it would be 500mb or so, and if upgrade doesn't work great then I'd have to download alternate/live cd anyways. (my internet is not stable, so upgrading would be a bad idea over the internet)

Is it possible to install fresh intrepid onto ubuntu OS partition while keeping /home partition the same and keep settings for installed programs? I presume I would still have to install programs again (VLC etc), will it overwrite settings on /home partition or will it screw stuff up?

Or should I backup /home partition data (almost all is just settings for ubuntu such as wallpapers and configuration files), move them onto windows partition, and format both OS and /home partition with a complete fresh install? Then migrate my config files back to /home and install all my apps again? I only have around 20mb of files that need to be saved on ubuntu OS. So not a problem backing them up.

---

### Post by FuturePilot on 2008-10-24
Yes. When it comes to the partitioning part select Manual or Custom (I can't remember what it's called) and just specify what partition your /home is and to mount it as /home. Just make sure **not** to check the Format box. Then specify your / and swap partitions accordingly. You do want to check the Format box for / if you're doing a fresh install though.

All your personal files and settings will still be there. You will have to reinstall your programs though.

---

### Post by logos34 on 2008-10-24
Here's the info from the official page to back up what FuturePilot is saying:

> [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)[B]

Clean Install Upgrade (not recommended)[/B]
 If your /home directory is contained on a separate hard-disk partition you should be able to upgrade by performing a clean install of the current release of Ubuntu and 'adopting' the old /home directory. 
**Back-up any important data before following this procedure as data loss is possible, and very well may be likely.** 

[LIST=1]
[*]Obtain an installation CD for the release of Ubuntu 7.04 you wish to install, and boot from it.
[*]Start the installation process. When you reach the *Prepare disk space* stage of installation, choose the *Manual* option and press **Forward**.
[*]Identify your current '/' (root) partition. Select '/' as the mount point and ensure that *Format* is ticked. **You will lose all data on this partition and the new version of Ubuntu will be installed there instead.**
[*]Identify your swap partition and set its mount point as 'swap'.
[*]Identify your /home partition. Set its mount point as '/home' and make sure that *Format* is **not** ticked.
[*]Continue installation as normal until you reach the *Who are you?* stage, enter a username and password which *exactly match* your current username and password.
[*]Complete the installation as normal.
[/LIST]
Once the installation has completed, you should be able to log in to Ubuntu and your /home partition with all of your documents and settings should be intact. 
 
[]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion")

---

### Post by andrewabc on 2008-10-24
Thanks for the info.

I think moving about 15 files to my windows partition, then wiping both OS and /home will leave me with less problems in the long run (conflicting settings from hardy->intrepid).

Most of my stuff is on windows partitions, I'm still trying to primarily switch to linux (it's been 2 years trying :P). Compiz working better in intrepid it should help me.

EDIT:
I backed up data/settings from /home and ubuntu OS.
I installed from the livecd and formated OS and /home.
Everything seems to be working good.

---

