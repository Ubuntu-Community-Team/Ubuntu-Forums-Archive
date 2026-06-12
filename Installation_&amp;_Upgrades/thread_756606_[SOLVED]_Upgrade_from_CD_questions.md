---
title: "[SOLVED] Upgrade from CD questions"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by Umang on 2008-04-16
I'm preparing for the April 24th upgrade to 8.04. Downloading over 200 to 300MB is too expensive for me, so I though I'd buy a CD from a distributor (official) and update with the CD. I have a few questions: (I've already read [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades))
[LIST=1]
[*]Do I have to get an Alternate CD, will the normal LiveCD do? (Looking at [community wiki page on Updating to Hardy]("https://help.ubuntu.com/community/HardyUpgrades") )
[*]Do I have to update all the packages also? (I have 240MB waiting to be updated, I would like to avoid doing it from the net). Can't I update from the CD? If I did install 8.04 directly, I wouldn't need to update all the packages, so can't I do it from the CD? ([Community wiki page on Updating to Hardy]("https://help.ubuntu.com/community/HardyUpgrades") says I need to update everything before I try to upgrade to 8.04)
[*]If I cannot. And I have to do it from the net, can I save my application data, or mount /home on a separate partition and reinstall Ubuntu on the root partition? (if yes, please tell me if I'll need to format the root partition before doing anything).
[*]Or, can I comment out all the repositories apart from the CD, and then upgrade, that way it won't have any problems with updating to 8.04?[/LIST]

Thanks in advance!

Umang

---

### Post by Partyboi2 on 2008-04-16
You can use the alternate cd to upgrade your system from gusty to hardy, the packages will get updated to what is shipped on the hardy alternate cd. If you did decide to upgrade from the net then you will not have to move your /home folder as this will still be intact after the upgrade.

---

### Post by Umang on 2008-04-16
But if I decide to update from alternate CD will I need to mount /home somewhere else?

Also, can I do it with a LiveCD, or does it have to be an alternate CD?

Thanks a lot!

Umang

---

### Post by Partyboi2 on 2008-04-16
This is all you will need to do, in your case you can skip step 1
> **Upgrading using the alternate CD/DVD**

 Use this method if the system being upgraded is not connected to the Internet.[LIST=1]
[*]Download and burn the alternate installation CD.
[*]Insert it into your CD-ROM drive.
[*]A dialog will be displayed offering you the opportunity to upgrade using that CD.
[*]Follow the on-screen instructions.[/LIST]If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 
 gksu "sh /cdrom/cdromupgrade"
 > Also, can I do it with a LiveCD, or does it have to be an alternate CD?You can only upgrade with the alternate cd.
> But if I decide to update from alternate CD will I need to mount /home somewhere else?
no

---

### Post by Umang on 2008-04-16
Thanks a lot, you've answered all my questions! :)

---

