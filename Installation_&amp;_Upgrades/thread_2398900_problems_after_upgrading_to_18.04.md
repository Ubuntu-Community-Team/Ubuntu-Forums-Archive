---
title: "problems after upgrading to 18.04"
date: 2018-08-19
forum: Installation &amp; Upgrades
---

### Post by ubontik2 on 2018-08-19
Before upgrading to Ubuntu 18.04.1 LTS everything was just fine.During upgrading online something went wrong, and the system crashed.I was not able to fix it, and installed from a flush drive. 
I see my external hard drive but when I try to save a file I get a message: "Could not read the contents of media. Error opening directory '/media': Permission denied" This happened with inkscape. It does not see a USB drive.
Please help me. I am a newbie.
Would it be OK to save on a hard drive and then move to a USB drive or there is fix for this.

Thank you

---

### Post by TheFu on 2018-08-19
I wouldn't trust an OS that had issues during the upgrade. There are likely to be issues related to the failures.  Could be minor or it could be a total dead end. Can't tell at this point.

If something failed in the upgrade to 18.04, I'd restore from the backup made just before the upgrade attempt, then try again.  If there are any failures, take careful notes so you can post the EXACT error message along with the EXACT stage of the process when it happened.

As for the external disk, try power cycling it and reseat the connectors. Give it 5 seconds between any actions.  If there are issues, check the **dmesg** output. Problems should be at the bottom. Checking other logs wouldn't hurt either, but for USB storage connections, I normally see issue in the dmesg output.

---

### Post by ubontik2 on 2018-08-19
Thanks [**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685"),

As I said I have clean install from a USB drive. Now I have some minor problems (home directory is lost, Thunderbird filters, etc.). I never had this before. Now I'm going to do back before upgrades.:(

---

### Post by oldfred on 2018-08-19
If you did a new clean install, did you use Something Else and select your old /home partition as new /home partition. It does not automatically find an old /home partition.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

