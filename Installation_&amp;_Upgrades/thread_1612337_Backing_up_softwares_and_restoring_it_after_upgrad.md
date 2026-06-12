---
title: "Backing up softwares and restoring it after upgrading ubuntu"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by nikhil.parmar on 2010-11-03
hello i m new to Ubuntu.........i want to know that can we do partition in ubuntu 10.10 just like windows????
The problem is, if we want to upgrade Ubuntu 10.10 to new version and we have installed lots of useful software than how can bring back the same softwares???? Is there any kind of BACKUP AND RESTORE technique so that we can restore it once we have upgraded our Ubuntu.....
Please help.......
Thank you

---

### Post by nikhil.parmar on 2010-11-03
please help...........

---

### Post by P4man on 2010-11-03
If you do an upgrade, all the applications that are still supported under the new version, will remain installed (and upgraded). the upgrade procedure will inform you which apps or packages can not be upgraded and will be removed.

If you want to install from scratch rather than upgrade, you can export a list of installed applications  and after the OS install, reinstall those applications again by doing this:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

To backup/restore application settings, just backup the homefolder and copy it back (or leave it if you have a /home partition).

Again though, that only works for applications in the repository that are still supported.



BTW, bumping once per day is considered ok. Once per hour is a bit impolite.

---

### Post by nikhil.parmar on 2010-11-03
thankzz
you mean that if i upgrade my ubuntu from a disk after formating the previous one, then to bring back my all softwares back i just need to backup my home folder and the paste it in the upgraded one, isnt it??

---

### Post by P4man on 2010-11-03
> **nikhil.parmar said:**
> thankzz
you mean that if i upgrade my ubuntu from a disk after formating the previous one, then to bring back my all softwares back i just need to backup my home folder and the paste it in the upgraded one, isnt it??

Nope. What you are describing is not an upgrade, its a reinstall from scratch. Are you sure you want to reinstall when you can do an upgrade?

If you must do a reinstall, see the link I provided on how to reinstall your applications in that case. The home folder only contains user data and settings, not installed applications. YOu probably want to do both (use the above commands to install the apps, and backup and restore the home folder to restore application settings and user files). The caveats still apply (only for apps still supported in the repositories, so this doesnt work for anything you installed manually through .debs or other ways).

---

### Post by nikhil.parmar on 2010-11-03
so this means that if i want all my softwares back, reinstalling them is the only option..!!!!!!

---

### Post by P4man on 2010-11-03
Please (re)read carefully...

---

### Post by irv on 2010-11-03
Check out this thread on [10.10. Upgrade vs. reinstall]("http://ubuntuforums.org/showpost.php?p=9933073&postcount=11"). I believe you will find it very helpful.
[http://ubuntuforums.org/showpost.php?p=9933073&postcount=11]("http://ubuntuforums.org/showpost.php?p=9933073&postcount=11")

---

