---
title: "Lost power during 10.10 upgrade"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by Mustang33 on 2010-10-26
Was upgrading from 10.4 to 10.10 using the Update Manager.  All files downloaded and I think it was about 1/3 of the way through the Installation when I lost power.  Now when it boots I have a purple screen with no login box.

Is there a way to restart the upgrade?

---

### Post by lukeiamyourfather on 2010-10-26
Push Ctrl + Alt + F2. This should bring up a terminal which you can use to continue the upgrade.

```
sudo apt-get dist-upgrade
```

Double check that the correct repositories are still there (for Ubuntu 10.10). If it doesn't work then it might be more trouble to resolve than starting over with a fresh install.

---

### Post by Mustang33 on 2010-10-26
Ctrl + Alt + F2 did nothing.

Just for kicks tried Ctrl + Alt + F1-12 and none of them did anything either.

Guess I gotta download the ISO...

---

### Post by lukeiamyourfather on 2010-10-26
> **Mustang33 said:**
> Ctrl + Alt + F2 did nothing.

Just for kicks tried Ctrl + Alt + F1-12 and none of them did anything either.

Guess I gotta download the ISO...

Yeah, that sucks. I was thinking it might have just broken the graphics drivers or GNOME. Since Ctrl + Alt + F# doesn't do anything the problems sounds more severe. Troubleshooting it with enough time could probably resolve the issue, but if it was me I'd just start over (but backup data first if it isn't already). Good luck with it.

---

### Post by Mustang33 on 2010-10-26
Luke,

Thanks for your quick reply.

Thankfully I have everything I *needed *stored in Ubuntu One.  Just hate to have to go through and get everything setup like I wanted again.  Install GIMP, MS Fonts, BOINC, etc, etc, ect...

---

### Post by justborn on 2010-10-26
hey i have the same exact problem...can nyone help?

i've currently logged in using a live-cd.

---

### Post by oldfred on 2010-10-26
One thing you can try, but it may depend on how far the upgrade has gone.

You can chroot into your system and run all the updates from that.

kansasnoob oneline chroot ------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh? Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition (needs change if separate /boot)
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Once chrooted into your system run all commands to update:

Commands once in chroot:
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories & 
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

You may have to check sources to see if it is still the old version or updated to the new version.
/etc/apt/sources.list

---

### Post by ubian on 2011-09-26
Ok, I found partial solution.
Had the same problem, pulled out the cable by mistake when upgrading :/
My upgrade failed while packages were installing.

It's a good solution for people who don't have a backup of their /home folders.
If you have a backup, you will probably be better with the clean install.

Download Ubuntu iso and get it on disk or memory stick.
Run the disk/media and choose upgrade.

It will give you a error before finishing saying that upgrade can not install all applications. You will have to install them manually.

Click ok, computer will restart.

To find out what's missing open your home folder and press [ctrl+H] this will show you hidden files and folders.

Many of them are folders with settings, etc for the software that was installed in the past.

Simply check if you can see any names here that are missing from your Applications menu and install them again.

For example I can see .gimp-2.6 folder in my /home but when I go to Application/Graphics menu I can see that gimp is not installed.
I install gimp and it's back with all your settings, brushes etc.

NOTE: I've noticed some weird problems with this setup later on so made clean install anyway. But it may work for you.

---

### Post by nothingspecial on 2011-09-26
Thanks for the information. :D

Back to sleep thread.

---

