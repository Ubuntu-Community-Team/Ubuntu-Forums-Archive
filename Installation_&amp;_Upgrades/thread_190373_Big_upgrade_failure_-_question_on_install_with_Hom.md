---
title: "Big upgrade failure - question on install with Home backup"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by stig on 2006-06-06
I tried upgrading from Breezy 5.10 to Dapper 6.06 yesterday using the Update Manager and after reading and following all the warnings, advice etc on the Forum stickies. But after 5 hours I had an aborted install, no xserver, loads of broken packages and also a problem due to Nautilus-Share
(like the one here: [http://ubuntuforums.org/showthread.php?t=188559](http://ubuntuforums.org/showthread.php?t=188559))

I had a lot of problems when I upgraded from Hoary to Breezy too, so I think it would be better now to do a clean install of Dapper by downloading and burning a CD. I have already backed up my Home folder to two CDs - one with all the data files and the other with all the hidden files.

I know that the data files will be OK when used on the new Dapper install but what about using the hidden, config, files? Can I just copy everything from the CD of old Home files over the new Home folder? For instance, I have done a lot of customization of OpenOffice (mapping macros to keys etc). Will this be retained by copying in the old hidden files over the new?

Also, when I install Dapper from a CD I will need to install a number of applications which I had on Breezy, such as Scribus. Would it be better to install these before copying over the Home folder hidden files?

---

### Post by pellgarlic on 2006-06-06
i would guess that it would be better to install the programs first, then reinstate the hidden config files, as the progs will create these files during installation, thereby overwriting your backups (unless the install process is smart enough to check if they exist first, and not overwrite them if they do, but in the absence of that knowledge, it'd be better to avoid that potential problem).

i would also guess that the config files should work okay, if the newly installed version of the program remains the same as the previously installed version. if a newer version is installed, it would probably depend on the individual program, whether it uses the same files and syntax within the files, whether it would work with the backed-up config files or not. 

probably best to check on openoffice.org's site to see if it gives details of compatibility of config files between different versions (and also for any other program of similar position for you. maybe a quick email to them if you can't find the info on their site?). or, you could just try it and see, and keep your fingers crossed. 

(if doing it this way, it might be an idea to backup the config files that are created with the installation, so you can easily switch back, should the old config files prove to be incompatible. then maybe a quick peek into the files could reveal similarities/differences if they exist, and present a way to hand-edit the old config files to accord with the syntax expected by the new version of the program...)

so, if you're lucky, the config files will just work. if you're slightly less lucky, a little bit of hand-editing will make them suitable. if you're unlucky, you'll either have to revert to the older version of the program, abandon your config modifications and start again with the new version of the program, or spend a bit of time figuring out how to convert the files to be compatible with the new version.

---

### Post by rcarring on 2006-06-06
Breezy used OpenOffice 1.9 (the beta to OOo 2.00), I would expect config files would work with the newer version -- 2.02 -- since it is an upgrade.

I would do a default Dapper install, then migrate your Home files back again. Maybe you could create an extra user, in addition to yourself, and test out the config files there before copying them back to your own Home folder.

---

### Post by stig on 2006-06-06
Sorry for the slow response when your responses were fast - I've been away from the computer for a few hours.

Thanks pellgarlic for a detailed and very lucid reply, and rcarring for the idea of testing as an extra user.

While I was away the computer was downloading Dapper, so now I can try an install. Perhaps when I do the next upgrade it will be better - I suspect one of the problems might have been a hang over from the poor hoary to breezy upgrade. But there is definitely a problem with nautilus-share during Dapper upgrade - and that's a pity because I found nautilus-share to be an excellent easy way to network my ubuntu and windows PCs together.

---

### Post by loney on 2006-06-06
As a debian distribution, Ubuntu takes great care to preserve local configurations in an upgrade.  Debian policy dictates that packages do not modify /home or /usr/local. 
Therefore, you should be able to restore /home without a problem. You might also want to restore /var/mail.

/etc config files are a bit subtler; cf. Krafft's "Debian System" section entitled "The sacred configuration files". A good practice is to keep a backup of any /etc file modified. This can be done automatically by editors, e.g. the ~ suffix in emacs. Then run find on the backup /etc files and restore modified /etc files on a case-by-case basis.

When an individual application is opened, it might migrate an existing /home config to a new config. Restore /home before opening any desktop application.

---

### Post by stig on 2006-06-07
The Dapper install went very smoothly and very fast, unlike my attempt to upgrade.

To be on the safe side, I restored the Home files (both hidden and shown) first, then opened individual installations. Evolution showed all my mail and my folders and I only had to set my account details again.

When first opened, Firefox did not show bookmarks, extensions etc and OpenOffice did not have my customization. But after resoring the .mozilla and .openoffice folders again everything was back to normal.

I like some of the new style and icons etc but Add/Remove applications seems to have lost some of the useful applications from its lists - e.g. I seem to recall Bluefish was there. I guess they will be in Synaptic, but that means we have shifted them from the more easy to the less easy way of doing things. Odd!

The Applications, Places and System menus show some strange, inconsistent behaviour. Sometimes they open as expected, other times they are partly off-screen and have arrows (I have the bar at the bottom of the screen).

---

### Post by pellgarlic on 2006-06-09
[QUOTE=stig]The Applications, Places and System menus show some strange, inconsistent behaviour. Sometimes they open as expected, other times they are partly off-screen and have arrows (I have the bar at the bottom of the screen).[/QUOTE]

maybe you could post a screenshot to illustrate?

---

