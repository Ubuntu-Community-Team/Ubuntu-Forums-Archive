---
title: "Doe's any user know the command given in terminal when GUI used to dist-upgrade"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by garvinrick4 on 2011-05-04
For my own curiosity what are the commands given to a terminal when user dist-upgrades with update manager. There are so many ways it seems to dist-upgrade I just wonder what
Ubuntu has decided on using for it's GUI procedure? Maybe using sudo do-release-upgrade -d will give me a terminal description or throw in a -v but have no install left I want to dist-upgrade. Just curious is all and feels like a legit question.

---

### Post by kansasnoob on 2011-05-04
[http://www.ubuntu.com/download/ubuntu/upgrade](http://www.ubuntu.com/download/ubuntu/upgrade)

The command you're suggesting is somewhat more applicable to a server upgrade :)

---

### Post by garvinrick4 on 2011-05-04
When a user sees that there is an dist-upgrade available in the update-manager and simply clicks on that button to dist-upgrade will it first change the sources.list
to next version and do an update and then dist-upgrade to finish the upgrade of version.
Basically like the Debian way but just accomplishing task by hitting button in GUI application. Or is the Debian way now a thing of the past and new commands are given by
the update-manager in GUI?
#I am wondering why the Debian way although valid not Supported by the Ubuntu community? What are the commands the GUI sets off if not Debian way?
# If the update-manager does not change the sources.list first and then update and dist-upgrade. How does it accomplish it's task? 
# This is not an important topic but one that I am curious about because this week I have
been studying the different methods of dist-upgradeing over time and all seem to change sources.list first including perl way. (Which worked well in VMware from maverick to natty.)

---

### Post by kansasnoob on 2011-05-05
This is a bit outdated but quite similar to present:

[http://static.howtoforge.com/images/upgrade_ubuntu_9.10_to_10.04/5.jpg](http://static.howtoforge.com/images/upgrade_ubuntu_9.10_to_10.04/5.jpg)

I do upgrade testing and always add at least two extra PPA's and when it's "setting new software channels" it always tells me that it's disabling those repos.

Generally the rest is really straight forward. Downloading packages is sloooow, like 1 1/2 hours even though I can usually DL a 700MB iso in under 20 minutes.

OT but you might find the new upgrade via live-installer interesting (even though it sort of vomited on me the last time I tried it):

[http://ubuntuforums.org/showthread.php?t=1744742](http://ubuntuforums.org/showthread.php?t=1744742)

---

### Post by Sef on 2011-05-05
Dist-upgrade is no longer supported. Do not upgrade that way. See kansasnoob's post 2 for how to properly upgrade.

---

