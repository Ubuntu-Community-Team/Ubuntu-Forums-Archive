---
title: "Upgrade to 6.06 from 5.10"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by watto_one on 2006-06-17
When I upgrade will I lose what is in my HOME folder.  I.E music,  private files etc.

---

### Post by johnc4510 on 2006-06-17
If your /home folder is on the same partition as your root / folders, then yes. If it is on a separate partition the answer is no, not as long as you don't format that partition during install. 
You can backup your /home file and that is the best thing to do in either case.

---

### Post by watto_one on 2006-06-17
Thanks I will Backup my files before upgrade

---

### Post by FredB on 2006-06-19
Upgrading without backuping up your home is like driving while being completely drunk : very dangerous #-o

---

### Post by rcarring on 2006-06-19
An alternative might be to add the alternate cdrom to repo, remove all the repos from the list and then do mark all upgrade and apply. In theory this should upgrade all the Breezy packages to Dapper ones. However, in practice I havent tried this yet, and I know that so many things change on upgrade that backing up and doing a clean install is a better solution IMO.

---

### Post by Najand on 2006-06-19
[QUOTE=watto_one]When I upgrade will I lose what is in my HOME folder.  I.E music,  private files etc.[/QUOTE]

In my case nothing happened to my homefolder during upgrading, although it is on the same partition as root folder is. Still very dangerous without making backups as you  don't know if something might go wrong during upgrade process.

---

### Post by FredB on 2006-06-19
[QUOTE=Najand]In my case nothing happened to my homefolder during upgrading, although it is on the same partition as root folder is. Still very dangerous without making backups as you  don't know if something might go wrong during upgrade process.[/QUOTE]

You were very lucky... Too maybe ? ;)

Looks like Murphy was away from your computer when you did your upgrade !

---

### Post by Gustav on 2006-06-19
The main reason for having a separate /home when upgrading is not that the upgrade destroys your data, it's that the upgrade may fail and you'll might have to do a complete reinstall. 

Then you will curse the day you didn't made a separate /home partition (if you didn't).

---

### Post by az on 2006-06-19
[QUOTE=watto_one]When I upgrade will I lose what is in my HOME folder.  I.E music,  private files etc.[/QUOTE]
NO!  Dist-upgrading will not touch your home drive.  It will not touch your partition table or anything.

If you are unhappy with the result, you will not be able to downgrade back, and maybe that is why some advocate the use of a seperate home partition.

Personaly, I think it's a lot more simple to just back up your important data in other ways than making a seperate partition.

Just be sure that you are dist-upgrading from the archive and not booting from the installer and reinstalling - *that* will wipe out your data.

To dist-upgrade from a cd, just boot into ubuntu and insert the cd into your drive.  Follow instructions on screen.

---

### Post by Mike Wilson on 2006-06-19
The post from Azz makes the 5.10 -> 6.06 upgrade sound simple. Well, for me IT WASN'T. By all means search the wiki for "dapper upgrade" and take to heart what it says there about the "Desktop" ISO/CD's problems. Your best bet is the "Alternate Install" ISO/CD. It worked for me, anyway, and left all home directory content and s/w settings intact.

---

### Post by az on 2006-06-19
[QUOTE=Mike Wilson]The post from Azz makes the 5.10 -> 6.06 upgrade sound simple. Well, for me IT WASN'T. By all means search the wiki for "dapper upgrade" and take to heart what it says there about the "Desktop" ISO/CD's problems. Your best bet is the "Alternate Install" ISO/CD. It worked for me, anyway, and left all home directory content and s/w settings intact.[/QUOTE]
Actually, the easiest way is to click on the update-notifier and select upgrade to new release....

---

### Post by mcwtlg on 2006-06-20
My upgrade from 5.10 to 6.06 on my dual boot (Ubuntu / WinXP) was far from easy.  While I have it all working, I do not see a lot of the things (XGL, etc) that  people are gushing about.  I did not lose any data, but the "upgrade" broke links as well as many other things.

* I backed up my home directory
* Edited my sources.list and changed all the instances of breezy to dapper
* Rem'ed out the repos I was sure would fail
* Saved the file
* Did an apt-get update
* Did an apt-get dist-upgrade

The I watched as apt removed a ton of packages and downloaded / installed very little.  When I rebooted, X was broken.  I was not worried, since can do the command line stuff.  I grabbed my laptop to start web surfing for what I needed to repair the issue and got X back.  However, most of my launchers failed and command line launches required full paths to run programs.  Ick. Well, I had to reconfigure a lot of packages and finally got the basics (T-bird, F-Fox, Samba, FTP, Bluefish GAIM, printing, etc) running.  I thought that now that I had an upgraded system, I would try XGL/Compwiz but that was a horrible failure so I had to remove it.

One thing that puzzles me.  My current drive usage, after the upgrade is 4 gigs.  Before, with the same programs, it was 3.1 gigs.  I have checked Synaptic for old and new versions of the same file, but no luck.  Any ideas on what I can look for that may be eating my space up?

btW, I did the apt-get dist-upgrade on 2 other boxes without any problems.  The only difference was the other boxes used XFCE as a WM.

---

### Post by az on 2006-06-20
[QUOTE=mcwtlg]My upgrade from 5.10 to 6.06 on my dual boot (Ubuntu / WinXP) was far from easy.  While I have it all working, I do not see a lot of the things (XGL, etc) that  people are gushing about.  I did not lose any data, but the "upgrade" broke links as well as many other things.

* I backed up my home directory
* Edited my sources.list and changed all the instances of breezy to dapper
* Rem'ed out the repos I was sure would fail
* Saved the file
* Did an apt-get update
* Did an apt-get dist-upgrade

The I watched as apt removed a ton of packages and downloaded / installed very little.  When I rebooted, X was broken.  I was not worried, since can do the command line stuff.  I grabbed my laptop to start web surfing for what I needed to repair the issue and got X back.  However, most of my launchers failed and command line launches required full paths to run programs.  Ick. Well, I had to reconfigure a lot of packages and finally got the basics (T-bird, F-Fox, Samba, FTP, Bluefish GAIM, printing, etc) running.  I thought that now that I had an upgraded system, I would try XGL/Compwiz but that was a horrible failure so I had to remove it.

One thing that puzzles me.  My current drive usage, after the upgrade is 4 gigs.  Before, with the same programs, it was 3.1 gigs.  I have checked Synaptic for old and new versions of the same file, but no luck.  Any ideas on what I can look for that may be eating my space up?

btW, I did the apt-get dist-upgrade on 2 other boxes without any problems.  The only difference was the other boxes used XFCE as a WM.[/QUOTE]
If you use the update-notifier upgrade-top-new-relase thinggie, it avoids a lot of hassle.  If for some reason the ubuntu-desktop package gets removed from your system, it makes sure that it is put back.  It is very reliable.

---

### Post by Daniel Ibrahim on 2006-06-21
[QUOTE=mcwtlg]
* Did an apt-get update
* Did an apt-get dist-upgrade

Then I watched as apt removed a ton of packages and downloaded / installed very little.  
[/QUOTE]
maybe you should have done
apt-get update && apt-get dist-upgrade

wouldn't this avoid the upgrade just in case the update didn't work?
That was what I found in the documentation on the upgrade...

---

### Post by mcwtlg on 2006-07-04
I found where all my space was going to...

I did an apt-get clean
apt-get autoclean and gained a gig of space back.
Wow.

---

