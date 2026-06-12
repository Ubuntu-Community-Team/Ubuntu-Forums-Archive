---
title: "Ubuntu Raring Update Accidental Shutdown"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by rex689 on 2013-04-26
Dunring the uprade to raring ubuntu, my computers cord got unplugged and the computer turned off. The computer has no battery. When I started it back up it goes to a black screen that
says: 

Stopping System V runlevel compatibility.
Starting
Starting
Stopping
Starting CUPS printing spooler/server

Asking for cache data failed
Assuming drive cache: write through
(and repeats those last two lines over and over)

It does not allow me to type anything either.

I am currently getting the .iso 13.04, raring ringtail, from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and going to boot through my USB using Unetbootin.

I am planning to install linux and partition the drive so I can keep my files.

Is there a better way to fix this problem, keep my files or fix the linux so I can keep my settings?

If it helps, I have puppy linux on my flash drive, perhaps I can do something with that.

Thanks for any help.

By the way, I am at the install Ubuntu screen and it gives an option to Install 13.04 alongside Ubuntu 13.04, will this keep my files considering what I had before was Ubuntu 12.10 or Quantal Quetzal. I don't think the old installs had this option.

---

### Post by oldfred on 2013-04-26
Along side will create a new partition and install to that, assuming you have room to shrink existing install. It just auto installs to new / (root) and maybe new swap. 

Best to backup all of /home including the hidden files if you have not already.

There is such a thing as an over install or dirty install. I do not really recommend it and you still need a good backup. But if install was half way thru it may be the easiest way to repair. The other option may be from a liveCD chroot into the install and repair and finish upgrade.

       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

Instead of just reinstalling grub, you really repair and finish upgrade.

 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Depending on whre upgrade was at, this may finish it or you may have to also restart it.

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
sudo apt-get -f install
dpkg --configure -a

---

### Post by Sanada1615 on 2013-04-28
I did the same thing just now. I didn't know what the Forward install window was, it's popping up just happened to coincide with a spam website popping up, so I shut it down thinking it was a spam site--big mistake, as a bunch of files failed to install correctly after that, leading me to the bigger mistake of stopping the installation halfway. After that, no programs would open, and I manually shut off my computer (I run 12.04 alongside Windows 7). What can I do? I can't boot directly into Ubuntu now, it just restarts every time I try, even in recovery mode. Is there a way to backup /home without booting into Ubuntu? What are my options? thanks for any help, and pardon my newbness.

---

### Post by oldfred on 2013-04-28
You should be able to backup /home from liveCD/DVD/Flash. Just be sure to include all the hidden files & folders.
You then should try to chroot into your install and continue update, or else a new install. See post #2 above.

---

