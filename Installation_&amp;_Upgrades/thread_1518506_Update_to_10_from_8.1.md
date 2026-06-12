---
title: "Update to 10 from 8.1?"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by Snowman53 on 2010-06-26
I have a Dell Laptop that has 8.1 installed. When 9 became available, I tried to upgrade, but there was a ATI video driver issue that I could never solve.

I have tried the 10 live CD and it seems to work. 

The update dialog offers the upgrade to 9, but not 10. 

How can I upgrade from 8.1 directly to 10? 

Or capture the personal files and setups before a clean install?

Thanks!

---

### Post by oldfred on 2010-06-26
Because 8.04 was LTS long term support, you can upgrade from that to the next LTS or 10.04. All others can only upgrade to the next version, so you would have to do many upgrades.

You should back up /home which has all your data and hidden users settings, any custom system configurations you have in /etc (but they may not be valid for the new version, more for reference just in case), and a list of all your installed programs. If you have  a separate /home it is a little easier as you can just reuse it and not reformat. If you have room and separate /home you can just install a new / (root) since it only needs 10-20GB, so you still have your old root for reference. 

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

 dpkg --get-selections > ubuntu-files

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources (medibutu, etc), the tip will only reinstall Ubuntu files. But any that refer by version of Ubuntu will have to be updated first.

---

