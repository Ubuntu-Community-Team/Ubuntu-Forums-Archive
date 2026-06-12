---
title: "Kubuntu Boot Issues, no gui"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by Stephan H on 2012-09-14
Ok also got some feedback:

Successfully defragmented and shrinked the initial partition (W7), installed (K)Ubuntu and apart from root (11GB), swap (5GB) and home (20GB), I formated 20GB of the remaining partition as ext4 and the rest in FAT32 for mutual access from both OS.

Kubuntu started fine after install. GRUB gives you a clear choice and both systems worked. I only couldn't install Firefox. The installer "pretends" to install packages but then there is still no FF. Never mind, saw it was reported as a known bug.

Today I started Kubuntu again but it wasn't starting up. Screen remained black.
Tried repair, tried file check etc. and now one can get to a terminal screen and login as root, see files etc. But it doesn't have a graphical desktop anymore.

What's wrong? Thinking of a re-install. 
But I got to try Kubuntu after my Mandriva (2010.2) lost its graphical desktop first, then died completely and it wouldn't let me install it again.
It led me to think it was a HDD failure, so replaced the HDD, tried Mandriva again with no success. Took the machine to a repair shop, they installed W7 to show the HDD actually works. Then tried (K- and)Ubuntu which worked fine. Kubuntu offers more options to customise your workplace. So decided on Kubuntu.

Now it looks the same initial problem comes up again. has anyone got any ideas??

Stephan

---

### Post by YannBuntu on 2012-09-14
**@Stephan:** please open a new thread.

---

### Post by oldfred on 2012-09-14
Moved to a new thread.

From terminal have you tried updating again?

apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

can you run ? 
startx

---

### Post by Stephan H on 2012-09-17
Hello,

No, couldn't run any of these. Hence it took a while now as I re-installed the system. Went well this time, even Firefox goers beyond the installer.
I got one step further now and there's a new question. Looks like this would also be a separate topic. 
So this time I opened a new thread: [http://ubuntuforums.org/showthread.php?p=12244838#post12244838](http://ubuntuforums.org/showthread.php?p=12244838#post12244838)

Thanks for all help and ideas so far!

Stephan

---

