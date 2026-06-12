---
title: "What is the proper/correct/easiest way/commands to remove 15.04 and reintall 14.4?"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by chris15491 on 2015-05-05
i am very un tecky. please write the answer as if to a 5th grader.

thanks

---

### Post by Y^2om&amp;#7sgP on 2015-05-05
try this link

[http://ubuntuforums.org/showthread.php?t=2253340](http://ubuntuforums.org/showthread.php?t=2253340)

Seemms there's no easy way I'm afraid, backup and start again

---

### Post by dino99 on 2015-05-05
its like doing a fresh install, but that time you make it over the one you does not want to use: you use gparted to know which partitions are used (should be /, swap and /home on a standard installation).
when you start installing 14.4 (or else), choose 'something else' option when the installer ask you where you want to install the distro, and select the partitions previously shown by gparted: take care to only set 'format' setting for the / partition and add the 'boot' flag, the swap & /home are reused as is (without formatting /home indeed if you want your data not erased), and select ext4 as the type. Later you will be asked about grub, select /dev/sda

---

### Post by Mark Phelps on 2015-05-05
You can't "go back" to an earlier release -- if that is your question.  So, if Ubuntu is the only OS on the machine, the solution is to boot from the 14.04 installation media and select the option to use the entire drive.  That will reformat the drive and do a clean install of 14.04.

---

### Post by Vladlenin5000 on 2015-05-05
> **Mark Phelps said:**
> You can't "go back" to an earlier release -- if that is your question.  So, if Ubuntu is the only OS on the machine, the solution is to boot from the 14.04 installation media and select the option to use the entire drive.  That will reformat the drive and do a clean install of 14.04.
^^^^
This.
Needless to say, do your backup before attempting a new installation.

---

