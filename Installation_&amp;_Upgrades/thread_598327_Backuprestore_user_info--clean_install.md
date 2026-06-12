---
title: "Backup/restore user info--clean install"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by revlarry on 2007-10-31
Good morning!

I am a fairly new user of Ubuntu, and am still learning how to do things. 

I would like to deploy 7.10 on a couple of computers, and do a clean install on each. Both have 7.04 on, and are running well. I prefer the clean install route, since it can be done with the LiveCD, and I can use that CD for multiple installs. The upgrade path using the alternative install has some issues (according to these forums), and would require a two long downloads (LiveCD and then UpgradeCD) Given a slower internet connection, this does not seem as practical.

Is there an easy way to back-up and restore my user settings to make the change-over even easier? Such a process would also make future upgrades simple. I have network options, external storage options, USB thumb drives, etc., so storing and retrieving my user setting wouldn't be a problem ... just need a quick "how-to" if it is possible.

Thanks for any help, even if it is a "No, you can't do that."

---

### Post by taurus on 2007-10-31
Back up the /home directory because that is where your personally settings are.  Otherwise, create a separate /home partition and you can mount that partition to /home when you reinstall but do not format it.  Then, everything is there when you first log in on your new system.

---

### Post by revlarry on 2007-10-31
Thanks for the help ... I thought it might be that simple. This will save me a lot of time on downloads, and a bit on each installation. Once I get the new installs running, I have people who want to come and see what Ubuntu is really like (I've already given them LiveCDs of 7.04) ... but I think the installed package is a much better "selling point".
Thanks again!

--Larry

---

