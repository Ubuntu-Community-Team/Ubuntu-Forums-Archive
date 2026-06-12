---
title: "How to resume the upgrade of ubuntu 11.10 to 12.04"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by Nalya on 2012-05-24
Hello, I tell them the problem I have. I started to upgrade my Ubuntu 11.10 to 12.04 with the update manager but in the middle of the installation I turned off the pc and now when I try to turn my machine lets me black screen with posters check all ok and not as summarizing the update of ubuntu. In the last thing left is

Chekking the battery [ok] and there it is. I'm honest I could not prove anything because this happened to me in the morning before coming to work. It already was doing the update and therefore so is the screen but if you can not summarize the update to finish installing it. The idea is not to lose the data (like a fool not record due to time) I want to exhaust all that can to avoid losing but in the case that no solution is lost. Hopefully they can give me some idea. Just recently I will be able to prove when I come home at night because now I'm at work.

Thank you!

---

### Post by oldfred on 2012-05-24
So do you get grub menu, or can you get grub menu with shift key held down from BIOS to menu appearing? Have you tried rescue mode?

Then it may be a video issue. 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you cannot even get to grub, you have to chroot into your install and update from there. But you need the current liveCD or USB to run the chroot.

these will get you to chroot:
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
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
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

