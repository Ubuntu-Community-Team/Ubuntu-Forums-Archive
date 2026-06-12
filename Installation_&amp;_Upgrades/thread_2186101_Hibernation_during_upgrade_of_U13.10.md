---
title: "Hibernation during upgrade of U13.10"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by lelionrougeca on 2013-11-05
Hi everyone, 

I accidentally put my computer into hibernation mode while it was conducting the update to 13.10. 

Now my system boots, and just crashes. The command center won't show and it's not connecting to my internet/network. It was working perfectly before. 

Anyone here have any ideas? I ran the recovery mode in advanced boot up and it seems to just stall. Should I leave it overnight? 

Some help would be appreciated. I have been trying to resolve this for a few days now. 

Thanks.
K

---

### Post by oldfred on 2013-11-06
Was this just a daily update of some software or a upgrade from 13.04?

If you cannot get into recovery mode you need to use live installer and chroot into your install to fix it. Or just totally reinstall.

       kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

OR:

 Of course you must first know what partition you want to mount, in this example I'm using sda1:

   sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).

Once chrooted.

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
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

