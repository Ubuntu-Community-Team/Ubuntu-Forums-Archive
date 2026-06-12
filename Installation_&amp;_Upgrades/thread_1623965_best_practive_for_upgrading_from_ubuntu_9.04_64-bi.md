---
title: "best practive for upgrading from ubuntu 9.04 64-bit to 10.10 64-bit"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by baserunner_ams on 2010-11-17
Hello community,

my current system runs 
- ubuntu 9.04 64-bit (jaunty)
- kernel linux 2.6.28-19-generic
- gnome 2.26.1
- /home in md raid5 (3 disks) (mdadm)
- /, /swap and /boot in fakeraid mirror (2 disk)
- 4 GB RAM, quadcore processor (Q6600)

as support and thus updates for 9.04 are discontinued i need to upgrade my system. 
Due to my configuration i had a couple issues when upgrading 8.04->8.10 and 8.10->9.04 which was the reason why i waited so long.

My gameplan for the upgrade is to loose the fakeraid if possible (eventually i keep the then spare disk for a windows xp installation later on)

1) Backup whole system to usb disk
2) download latest iso (64-bit alternate) -> burn CD
3) upgrade

any good advice hint is welcome to avoid trobles

thanks

---

### Post by mörgæs on 2010-11-17
Might be easier to begin with installing XP.

Try running 10.10 as a live boot first to verify that it works well on your hardware.

---

### Post by lobralleo on 2010-11-17
If you want to avoid upgrading often, you might want to stick to the LTS release and install 10.04 instead of 10.10. This way, you will be covered till early 2012.

---

### Post by mörgæs on 2010-11-17
Till early 2013, actually.

---

### Post by lobralleo on 2010-11-17
> **mörgæs said:**
> Till early 2013, actually.

Oh right, LTS are released every two years but supported for 3 full years... my bad :)

---

### Post by oldfred on 2010-11-17
If you are doing a new install rather than an upgrade, you can list all your install apps, to make it easier to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

 dpkg --get-selections | grep -v deinstall > ubuntu-files
or
 dpkg --get-selections > ubuntu-files

If your are breaking your RAID you also need to remove settings on the RAID drives that cause issues.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

I also save any system wide settings I customized in /etc,  but do not automatically reinstall as they may conflict with the new maintainers version which I always default to first. 
Of course you should have good backups. Is /home a separate partition or are you planning on restoring it?

---

