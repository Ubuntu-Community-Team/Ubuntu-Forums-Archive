---
title: "Update 14.04 LTS -&gt; 16.04 LTS fails, &quot;too many errors&quot;"
date: 2016-05-25
forum: Installation &amp; Upgrades
---

### Post by Malibyte on 2016-05-25
Hi all -

I have several machines running Ubuntu, and, having a few days off work this week, decided to upgrade all of them from Trusty to Xenial.  Five of them (three servers, one laptop and one desktop) upgraded fairly easily, with some minor snags (mainly due to the switch to systemd) which I was able to fix without too much trouble.  My big media server, running MythTV, Plex server and a bunch of other big apps, would not upgrade - I noticed a lot of error messages during the procedure, which finally crapped out before completion, giving me the cryptic message "there were too many errors".  It appears due to classic dependency hell, as many wouldn't install because their dependencies weren't set up yet.  Multiple attempts to clean this up with "dpkg --configure -a" and "apt-get install -f" and apt-get dist-upgrade -f" were only partly successful, leaving me with a list of 50 or so apps which were listed as not installed (including the X server and the initrd for the new kernel) and 600+ which apt said were not installed. 

I finally gave up and reverted to 14.04 using my image backup and tried it again.  Same result.  Restored from backup, now back on 14.04 and running as usual.
One small laptop, running the 32-bit version, had the same problem.  I will probably do a clean install on that one, since I don't use it much.  However, doing a fresh install and re-installing all the apps on my media server would be a day-killer.  Any other magic methods of getting this upgrade to finish up cleanly?

Thanks in advance!

---

### Post by oldfred on 2016-05-25
Is system fully up to date?
Do you have any ppas, or proprietary drivers like nVidia installed? They must be removed first, as they often hang up and prevent all the updates.

I have always preferred clean installs to a new 25GB / (root) partition. All my data is in a separate /mnt/data which I relink and I export all installed apps with every backup, so I can easily reinstall them. All settings are in /home so rsync or restoring from backup brings all those back in. Some configuration settings I use a script for.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below) I now have added ESP - efi system partition to backup:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by Malibyte on 2016-05-26
Yes, several ppas and the nvidia driver installed via Ubuntu itself, rather than downloaded from Nvidia.  Will try removing it and disabling the ppas when I try the update again in a week or so (going away on a business trip).  I have them on a couple of the other systems which did cleanly upgrade as well, but the media server has a LOT of ppas.   It is fully updated, with the exception of the kernel and headers, which I have not had any need to update since I've had no issues with them, and it's behind a solid firewall.

Thanks very much for the suggestion, will post up when I have results.

---

### Post by howefield on 2016-05-26
PPAs "should" be disabled automatically by the upgrade and left for the user to sort out after the upgrade as I understand it, might be worth checking that required ppas are still functional and reflect xenial repositories on the machines that have successfully upgraded.

Also, on such a "complicated" upgrade as your media server, it might be worth waiting for the official upgrade at the .1 release, it is only a matter of some weeks away.

---

