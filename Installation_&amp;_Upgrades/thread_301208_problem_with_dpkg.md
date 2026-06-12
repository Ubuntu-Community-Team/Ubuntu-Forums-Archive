---
title: "problem with dpkg"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by karnakdk on 2006-11-16
I installed gnuplot, and one of the suggested packages were gnuplot-doc. Then I "sudo apt-get install gnuplot-doc", but my computer froze when configuring the package.

"dpkg --audit" returns the following:

$ sudo dpkg --audit
Password:
The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 gnuplot-doc          Documentation for gnuplot

I ran "dpkg --configure gnuplot-doc", but, again, the computer froze while configuring the package. I also tried "sudo dpkg --purge gnuplot-doc", but the computer freezes too.

Now, I can't update any package! When I click on the update-notifier icon, I get this: "Only one software management tool is allowed to run at the same time. Please close the other application e.g. 'aptitude' or 'Synaptic' first." These are NOT running.

With "sudo apt-get update" I get the following:

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
       [ etc... ]
Fetched 6B in 19s (0B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

The suggested command also freezes the system. What can I do?

---

### Post by bapoumba on 2006-11-16
Hi,
have you tried **sudo dpkg --configure -a** ?

---

### Post by karnakdk on 2006-11-17
Yes, and it didn't work.

---

### Post by bapoumba on 2006-11-19
Just a wild guess, do you have enough room on your partitions ? **df -h** will let you know.

---

### Post by karnakdk on 2006-11-20
Yes, I do.

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              21G   17G  4.3G  80% /

---

### Post by bapoumba on 2006-11-24
Are you still stuck ?

---

### Post by johnraff on 2008-05-13
It would be really helpful if people posted back when they got their problem fixed.

I've got a very similar problem now.
[http://ubuntuforums.org/showthread.php?t=788820](http://ubuntuforums.org/showthread.php?t=788820)

---

