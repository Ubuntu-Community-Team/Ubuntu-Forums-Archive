---
title: "Creating an Installation SD Card"
date: 2015-08-23
forum: Installation &amp; Upgrades
---

### Post by james139 on 2015-08-23
I've got my Ubuntu system set up and running pretty much how I want it. Can I create an installation disk of my current setup, preferably on SD? Or does it have to be a fresh install then a back up from file if everything goes wrong?!

I don't know how to do either of these things so a nudge in the right direction would be good. I googled it but got quite a few conflicting options, some of which appeared not to work.

---

### Post by yancek on 2015-08-23
> Can I create an installation disk of my current setup,

The best software I am aware of to do this is remastersys which had versions specifically for Ubuntu and some derivatives as well as for Debian.  Unfortunately, for Ubuntu users, the person who wrote and maintained the software gave it up as it was just too much work, too many demands and too little reward.  I used it last on Ubuntu 12.04 and it worked fine.  Might work on later versions, not sure.  You should do regular backups to a different drive than the one on which you have your system installed.  Another option is to have either a separate /home or /data partition where you have personal data such as pictures, movies, music, documents.  Then when you do a new install, make sure you do not select to format that partition (home or data).

---

