---
title: "Details of upgrade packages and install one at a time"
date: 2020-06-19
forum: Installation &amp; Upgrades
---

### Post by anthonyl2019 on 2020-06-19
Caution: Inexperienced user, Kubuntu 18.04 LTS

I'm trying to track down a problem and have restored my system to a non-problematic backup on 18 March.  This gives me a list of 219 updates available in Discover.

What I want to do is install each update as they were released.  I can get:

```
udo apt-get update >updatelist19Jun20.txt

```

Hit:1 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) bionic InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease

I don't know how to check details and install each one, and in any event I suspect they are not in date order.

My plan is to install one batch at a time and check if my problem occurs.  That at least will help me narrow it down to what might be causing the problem.

If I find a set up updates that do cause a problem, then how do I backtrack?

---

### Post by VMC on 2020-06-19
I'm guessing here, but have you tried:
```
sudo apt-get update <a file from updatelist19Jun20.txt>
```

---

### Post by ajgreeny on 2020-06-19
Depending on how many upgrades there have been you can see probably a large majority of them, if not all by running ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will list all upgraded packages by date and time.  This should allow you to figure out which day each of the upgraded packages arrived with you.

---

