---
title: "Cannot boot after botched upgrade, can I repair?"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by jtravisp on 2010-06-06
Last night, my left mouse button on my Acer laptop stopped working out of nowhere. While searching for a solution I started the upgrade process. Without thinking I restarted during the upgrade installation, which has apparently caused some big problems.

I cannot boot any longer. I get the Ubuntu splash, then a slowly flashing black screen.

I am able to boot to the Live Cd without any problems, but I'm not sure what to do from there. I'm been searching the forums, but can't find anything.

I've been running the 10.4 beta without a problem for a while.

Thanks for the help!!!

---

### Post by wilee-nilee on 2010-06-06
> **jtravisp said:**
> Last night, my left mouse button on my Acer laptop stopped working out of nowhere. While searching for a solution I started the upgrade process. Without thinking I restarted during the upgrade installation, which has apparently caused some big problems.

I cannot boot any longer. I get the Ubuntu splash, then a slowly flashing black screen.

I am able to boot to the Live Cd without any problems, but I'm not sure what to do from there. I'm been searching the forums, but can't find anything.

I've been running the 10.4 beta without a problem for a while.

Thanks for the help!!!

You have been running Lucid beta with no updates is this correct? 

Do you mean upgrade in that there were updates available if the 1st question is correct? 

You can't upgrade the distro without some special setups, the post is not real confusing but to get help a few things need to be confirmed.

Upgrade has two different meanings with Ubuntu, the second being distro-upgrade.

---

### Post by jtravisp on 2010-06-06
> **wilee-nilee said:**
> You have been running Lucid beta with no updates is this correct? 

Do you mean upgrade in that there were updates available if the 1st question is correct? 

You can't upgrade the distro without some special setups, the post is not real confusing but to get help a few things need to be confirmed.

Upgrade has two different meanings with Ubuntu, the second being distro-upgrade.

Right, sorry I was unclear. I was running Lucid beta. I don't think it was a distro upgrade (I guess you're saying this wouldn't be possible, anyway?), but I'm not positive.

---

### Post by wilee-nilee on 2010-06-06
If you can get to a command line run,
```
sudo dpkg --configure -a
``` 
Another command to use may be this
```
sudo apt-get install -f
```
To see if it gets the upgrade from the lucid updates back running.
You really want to be using the update and upgrade option in a distro, it will keep this sort of thing from happening.

Really you might want to also include whether this is a dual boot situation with MS or Apple and if the Lucid is a wubi install in a MS install. This sort of information can have things move quicker.

---

### Post by darkod on 2010-06-06
It might be a stupid question, but if you were running only the Beta, have you tried to boot in live mode, get out the data you want, and just do a clean install of the final release?

Can you even update the Beta to be like the final release?

---

### Post by oldfred on 2010-06-06
since it was in the middle of updating I think you will have to chroot into your system and run all the updates from that. kansasnoob has the best way to chroot as you can copy one line since he combined them all with &&.

kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Then you need to run all the updates.

Some commands, not sure which you may need, you should not need the uninstall grub & reinstall grub2, and you should not need to run the delete & reinstall of the desktop, but I include just in case Note all # are comments so do  not copy & paste those:

#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
Commands once in chroot:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

upgrade can only update existing packages and add new ones 
The command to upgrade to next release version is "sudo do-release-upgrade" (CLI) or "gksudo update-manager -d" (GUI).

---

### Post by wilee-nilee on 2010-06-06
I must say that the details in oldfred's and darkod's posts always separate the wheat from the chaff. ;)

---

### Post by jtravisp on 2010-06-06
> **oldfred said:**
> since it was in the middle of updating I think you will have to chroot into your system and run all the updates from that. kansasnoob has the best way to chroot as you can copy one line since he combined them all with &&.

kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Then you need to run all the updates.

Some commands, not sure which you may need, you should not need the uninstall grub & reinstall grub2, and you should not need to run the delete & reinstall of the desktop, but I include just in case Note all # are comments so do  not copy & paste those:

#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
Commands once in chroot:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

upgrade can only update existing packages and add new ones 
The command to upgrade to next release version is "sudo do-release-upgrade" (CLI) or "gksudo update-manager -d" (GUI).

This did it! I used the alternate install CD to get to the command line. I ran all of the commands listed above and I'm back in business. Now on to that pesky problem with the left mouse button not working all of the sudden...

Thanks!!!!

---

