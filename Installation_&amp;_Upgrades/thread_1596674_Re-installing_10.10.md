---
title: "Re-installing 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by shiman6 on 2010-10-14
So when I upgraded from 10.04 to 10.10, xorg didnt work anymore. It would freeze up the whole computer at boot, and all I am able to do is go into rescue mode. I tried booting from a previous kernel, and no luck there either. I tried re-installing X, but that didnt work either.

Is there a way to trick ubuntu into doing a re-install by using the dist-upgrade option of apt-get?

Dont know if this helps, its an HP Pavilion N5495, P3, 512mb ram. I dont know what kind of graphics processor it has.

---

### Post by shiman6 on 2010-10-15
Nobody has any ideas? I dont know that much about the updating system of Ubuntu, but im sure there is a way to change some things, then trick Ubuntu into re-installing 10.10 or 10.04 though "apt-get dist-upgrade" ?

---

### Post by garvinrick4 on 2010-10-15
[http://ubuntuforums.org/showthread.php?p=9975299#post9975299](http://ubuntuforums.org/showthread.php?p=9975299#post9975299)

---

### Post by oldfred on 2010-10-15
If you can get to a terminal by manually booting from the rescue mode then run these commands:

If not you can chroot into your system and run these commands.

If command line then use sudo -i to get into sudo mode
Commands once in chroot:
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#houseclean
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

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by shiman6 on 2010-10-16
The first fix, i will use it as a last resort. I tried the second one, i am trying to trick Ubuntu into re-installing 10.10 or re-installing 10.04. I am looking for non destructive methods of re-installing or downgrading.

---

