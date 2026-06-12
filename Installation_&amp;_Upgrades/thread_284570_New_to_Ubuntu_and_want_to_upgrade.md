---
title: "New to Ubuntu and want to upgrade"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by rey1321 on 2006-10-25
Hi guys! I just installed ubuntu 5.4 and then I found out that there is a new version, 6.06, my question is how can I upgrade my system with the new version(6.06) can I upgrade it from the internet or I have to install another cd with the new version. Also when I log on into the internet do I need a antivirus protection from a third party or I'm protected with the system itself.

---

### Post by studentism on 2006-10-25
I've never upgraded from one revision of Ubuntu to another, so don't blame me if things go horribly wrong (ie wait for another response or Google based on the lead here), but I believe the procedure is to change all instances of "breezy" to "dapper" in your /etc/apt/sources.list and then run "sudo apt-get update" then upgrade either through commandline ("sudo apt-get upgrade"), Synaptec, or the upgrade notification that appears in the upper right-hand corner.

On the other hand, this is a new install, so it probably doesn't matter if you wind up hosing it.

---

### Post by Redache on 2006-10-25
Open up a Terminal and type "sudo apt-get dist-upgrade" (Without quotation marks) and it should upgrade for you.

It will take a while as it'll be a few hundred meg in size but it's pretty automated for the most part. 

Hope it works!

---

