---
title: "is it possible to run programs from a drive other than home drive?"
date: 2022-07-04
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-07-04
This is probably a strange question.  I had a system that ran well and then it couldn't find the boot partition.  Then I decided to put an 1tb ssd for the main drive because it really increases the speed of the machine.  So, now, I have a drive with all my programs, etc. on it and I wonder if its possible for it to run any of those programs.  When I first set this up with eh ssd it was actually running everything and then it got an update and suddenly it couldn't anymore.   I suspect I can't but I thought I would ask.

Thank you..............

---

### Post by ubfan1 on 2022-07-05
You can mount your old drive, say /mnt/xxx, then run what you like with a full path, /mnt/xxx/home/user/bin/program   etc.  or just add those paths to your programs to your PATH variable in .profile.  Unless you explicitly mount your old drive with the "noexe" attribute, you should be able to run programs.  If your user UUIDs are different, (old vs. new) you may have a permission problem accessing the program.

---

### Post by SeijiSensei on 2022-07-05
You can run any program for which you have the execute permission by using its full path as ubfan1 suggests.

However, I wouldn't do this for ordinary applications. I'd just reinstall them from the repositories. For scripts you write or software you compile from source you can mount the old drive and use the entire path. However I wouldn't keep this arrangement very long either. Just copy everything over to the SSD drive and move along.

You can refresh your memory on what was installed on the old drive by looking in its /var/cache/apt/archive directory. You can ignore lots of things in that list, especially packages that begin with "lib." These are all likely "dependencies" that were installed alongside the applications you requested. But a few items should catch your eye.

---

