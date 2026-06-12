---
title: "Updating Ubuntu 14.04 problems"
date: 2015-01-23
forum: Installation &amp; Upgrades
---

### Post by mbkwp on 2015-01-23
The updater wants to install new updated, good I like that. 
It is saying /boot is full and to clean that out, then use sudo apt-get clean to finish any temp files of. I can't empty /boot and the command does not exist per the computer.
What to do?

On aside, my keyboard is slow and will not allow normal typing when repeating letters, such as oo or ll. It has to be done very slowly. Any suggestions?

---

### Post by Penguin360 on 2015-01-23
Do you mean you cannot run this command?
```
sudo apt-get autoclean
```

Or this command?
```
sudo apt-get autoremove
```

---

### Post by fantab on 2015-01-23
If /boot is full then there could be old and unused kernels.
The following command will remove all the old kernels except the one in use:
```
sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

Then you can check with
```
df -h
```
for /boot space.

---

### Post by ajgreeny on 2015-01-23
Just out of interest, why are you using a separate /boot partition?

You need one, and it's made automatically, if you choose to use either LVM partitioning or encryption, but if you have neither of those, it causes more problems than it solves, in my opinion.

It is probably too late to change now, but bear this in mind next time you install any Linux distro, and for now simply remove all the old kernels you have on your system.  You can see what kernels you have from the command ```
ls -l /boot | grep vmlinuz
```and you can remove old ones with the command shown above from fantab, or do it manually by removing linux-image versions except for the two latest ones, which I do with synaptic; I have never used the software-center, much preferring the greater flexibility of synaptic

---

### Post by mbkwp on 2015-01-23
Now the machine is telling me to run this.  apt-get iinstall -f

Then ti tells me this.
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Any ideas?

---

### Post by fantab on 2015-01-23
The 'lock' happens if you use more than one package manager... or if package manager is already busy. Restarting Ubuntu should take care of it.
Also 'apt-get -f install' should be run with 'sudo':
```
sudo apt-get -f install
```.
Before you run version upgrade make sure you have your present ubuntu up-to-date.

If there are errors the please post the 'error' output here, so we know what is going on.
Post the output of:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by mbkwp on 2015-01-23
Finally. Updates seemed to be locked up for what ever reason. As to the partition question, it is how the program was installed and  I never knew it would be a problem or was even set up that way.
Thank you very much.

---

