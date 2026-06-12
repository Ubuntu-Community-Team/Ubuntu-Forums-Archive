---
title: "Advice re partition size for dual boot"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by echo59 on 2010-10-09
Hi,

I've been playing around with Ubuntu for the past 9 months or so and have decided to take the plunge....  I've Vista installed already and would like a dual boot set-up.  I've 2 HDs currently, 220GB for OS(s), and 230GB for data/documents so I plan to share my documents HD between OSs.

I've 142/222GB free on my OS drive and my plan was to partition this drive for my Ubuntu installation.  What size partition should I create?  I have nearly everything (plus more) installed on Vista already.  I was thinking 80GB for Ubuntu would be enough.  Do I need more???

Also, I've been using a Live distro of Karmic on my USB key.  If I install from the USB key will the install copy my modifications automatically (Chrome, Compiz, VLC, etc) or will it do a clean install?

I tried to install Lucid on my USB (both as update and fresh install) but to no avail.  Should I go for a fresh install of Lucid onto my new partition????


I'd love to hear any opinions out there.....


J

---

### Post by clrg on 2010-10-09
80GB should be more than enough. My installation currently uses 7GB, including additional software I installed.

I'm glad you decided to install Ubuntu :)

---

### Post by oldfred on 2010-10-09
If you plan on having data elsewhere I recommend 20GB for a system partition and 2GB for swap. If you want to hibernate then swap should be the same size (slightly larger) that your RAM memory. If you want you can have a separate /home that has your user settings, but if data is elsewhere /home inside the / (root) is ok. Either way just be sure to back it up regularly.

I have several system partitions and after manually mounting my data & shared partitions copied history to a bash file to let me semi-automatically remount on every install. That way I can upgrade or test the beta and easily have all my data in the system partition.

It will not copy data over. All of your user settings are in /home, so all you have to do is copy your current /home into your new /home. 

If you have done any system settings they will be in /etc. You can also export a list of all installed applications and reinstall the most current versions.

 dpkg --get-selections > ubuntu-files

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

