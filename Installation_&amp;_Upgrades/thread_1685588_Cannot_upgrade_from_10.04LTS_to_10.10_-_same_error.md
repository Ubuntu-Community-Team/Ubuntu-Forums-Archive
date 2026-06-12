---
title: "Cannot upgrade from 10.04LTS to 10.10 - same error each time"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by jack_123 on 2011-02-10
Hi I tried to upgrade to 10.10 using update manager but it gave the error below each time i tried. Please help!
Thanks much in advance!
''''
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

---

### Post by sikander3786 on 2011-02-11
Welcome to the forums :-)

Go to System > Administration > Software Sources > Other Software Tab and disable all the testing PPAs.

Then from Applications > Accessories > Terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

Then either run this command or run update-manager.

```
sudo do-release-upgrade
```

Let us know how that goes.

---

### Post by jack_123 on 2011-02-11
> **sikander3786 said:**
> Welcome to the forums :-)

Go to System > Administration > Software Sources > Other Software Tab and disable all the testing PPAs.

Then from Applications > Accessories > Terminal:

```
sudo apt-get update && sudo apt-get upgrade
```Then either run this command or run update-manager.

```
sudo do-release-upgrade
```Let us know how that goes.

Thanks sikander3786 -- None of those commands worked. Even running those commands from terminal give out the same error. After trying multiple times, now the issue is that the moment i open the update-manager gui, it checks for updates, and then throws me the error I pasted above. (Previously it used to show up only when I clicked on the actual 10.10 upgrade button on the update-manager).

None of the commands would work...I tried the apt-get dist-upgrade as well.

Any way to fix this problem so that I can upgrade fine?

---

### Post by jack_123 on 2011-02-11
ANyone around who knows how to fix this problem? I wwould want to avoid reinstall here.

---

### Post by Patthebrat on 2011-02-11
Having the same problem.

---

### Post by cosaki on 2011-03-03
I am having the same problem too.

I've also tried installing with a 10.10 live USB, but I can't get the partitioning to work.  I currently have a 80 gb partition for windows 7, and a 60 gb partition for Ubuntu 10.04.  I could only get it to add a second Ubuntu partition for the new release, or write over the entire drive.  Even when I click to use the entire partition, it shows that the size will be 250 gb (when it should be closer to 60).  Never had any problems with it before.

---

### Post by sikander3786 on 2011-03-03
Just found the solution and posted here. I hope it will work for you.

[http://ubuntu4beginners.blogspot.com/2011/03/unresolvable-problem-occurred-while.html](http://ubuntu4beginners.blogspot.com/2011/03/unresolvable-problem-occurred-while.html)

---

### Post by cosaki on 2011-03-03
Thanks! I'll give this a shot when I get home.

---

