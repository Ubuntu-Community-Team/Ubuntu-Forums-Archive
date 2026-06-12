---
title: "help upgrade from 17.10 to 18.04"
date: 2019-08-12
forum: Installation &amp; Upgrades
---

### Post by doggydaddy206 on 2019-08-12
i am struggling, i cannot get my desktop to upgrade from 17.10 to 18.04

no matter how i approach it, I keep getting errors basically saying "Failed to Download repository information"
E:The repository 'http://archive.ubuntu.com/ubuntu artful Release' does not have a Release file.

i see (now) that 17.10 quit support like a year ago, and well, i don't know what the heck ive been doing for the past year, but clearly not paying attention.

What should i do?

thanks

---

### Post by guiverc on 2019-08-12
Ubuntu 17.10 (2017-October) is well past EOL (18.10 from a year later is now EOL too), and after a release goes to EOL it's software repositories get moved from the location they were (in your error message) to old-releases.ubuntu.com.  There is no set date on when this move occurs except it's after EOL (17.04 moved very quickly; 17.10 was slow).

If you don't like release-upgrading every 6-9 months please use a LTS or long-term-support release that is supported for 5 years (or 3 years if a flavor). 

Refer [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) for help on your EOL release.  You are in luck in that your next release-upgrade was to a LTS that is still supported  (it gives you more choices & makes for an easier upgrade)

---

### Post by doggydaddy206 on 2019-08-12
thanks!

---

### Post by doggydaddy206 on 2019-08-12
lemme ask this:  is an EOL upgrade generally pretty stable?  or would i be better off doing a full new install?  i dont really want to do a new install (and all the backup efforts), but i will if needed.

---

### Post by QIII on 2019-08-12
If you do any upgrade, you should back up anyway.  That is particularly true with an EOL.  If you are going to back up anyway, a fresh install will be cleaner.

---

### Post by guiverc on 2019-08-12
If I was in your place, I would change your sources to point to old-releases, `sudo apt update`***, `sudo apt dist-upgrade` (get yourself fully-up-to-date), reboot if kernel or certain changes were installed, then `do-release-upgrade`to cause yourself to bump to 18.04.

*** note I'd take note of what additions you made to your sources, and consider any PPAs or 3rd party stuff you've added and how it'll impact 17.10->18.04 upgrade.  I may disable/remove/purge them depending on what I saw whilst still on 17.10.  The 3rd party stuff is the major problem with release-upgrades.

After you're on 18.04, reboot & test it out.  If necessary add-back some 3rd party otherwise leave them off.

If you have troubles with release-upgrade to 18.04, and get stuck - you can re-install (using an 18.04 ISO on thumb-drive) using "something-else" and selecting your partitions, ensuring you have "format" unticked!!!!!! This option causes your added software to be noted, system directories are wiped, install is done, then software you added to your system is added back (providing it's available in sources; mainly an issue for 3rd party) then user is asked to reboot.  No user files are touched (unless format was ticked) and most/all your additional software is added back (unless you selected format). Gloabal changes (made in system directories) will likely be lost, but user changes (mods made in $HOME) won't be touched unless you formatted...    

If you want to use the HWE kernel; use the 18.04.3 ISO that only recently came out (you'll have fewer updates).  If you don't want to use the HWE kernel, use the 18.04.1 ISO if you need to use ISO..

As @QIII has already stated - good backups are always a MUST.

---

