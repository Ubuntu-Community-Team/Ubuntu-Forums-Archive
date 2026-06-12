---
title: "Fresh install  upgrade method: Alternate ways?"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by sancho panza on 2007-07-16
[_This_]("https://help.ubuntu.com/community/FeistyUpgradesFreshInstall?highlight=%28upgrade%29") is the 'official' method to do a clean-install-upgrade without losing personal settings/data/programs.
[LIST]
[*]Is this the only way? Can I do it without creating a seperate /home partition?
[*]If its the only way, how do I decide how much space to allot to that partition? I'm not sure of what are the kinds of file that might get stored by the OS there, or which files there might expand over time. 
[*]Why can I not just copy the /home folder to an external media before the upgrade and then copy it back after the upgrade? My guess is that its because the /home folder has data written into it *during* the upgrade/install. Am I right?
[/LIST]

---

### Post by aysiu on 2007-07-16
I would recommend a /home partition--it's essentially the same as copying /home to an external media and copying it back... except that you don't have to copy it back.

What gets stored in the /home partition? All the user data. User settings (Firefox bookmarks, toolbar modifications, etc.). User personal files (music, pictures, etc.).

The OS (Ubuntu) will probably never be more than 10 GB. The user data can be a lot more than that (my music collection alone, for example, is over 50 GB), so the /home partition should be pretty huge.

It may be theoretically possible to copy the /home folder back (using a live CD) after the installation, but it may not be successful, and if you're going to go through that much trouble, you might as well make a separate /home partition.

---

