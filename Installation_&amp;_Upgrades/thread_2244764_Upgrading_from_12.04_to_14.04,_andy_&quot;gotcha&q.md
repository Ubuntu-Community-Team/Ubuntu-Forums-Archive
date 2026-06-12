---
title: "Upgrading from 12.04 to 14.04, andy &quot;gotcha&quot;'s?"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2014-09-18
I'm looking at upgrading from 12.04 to 14.04 and now that 14.04 has been out almost 6 months most of the common issues should be known and how to fix it figured out.

So, are there any "gotacha"s I need to be mindful of when updating from 12.04 to 14.04? If so, what are the work-arounds?

I have heard, nad plan on doing so, I should remove or disable any PPA repositories before running the update.

Anything else?

---

### Post by oldfred on 2014-09-18
The usual issues and why I now always install to a new 20 or 25GB / (root) partition.

If you have any proprietary drivers for Video or Internet you must uninstall them and then reinstall after update.
And since some ppa may not have new versions they often cause the major issue. When that ppa does not work entire upgrade crashes midway and creates major issues.

Always have good backups as if you were doing a new install, or backup all data, /home, /etc and export list of installed applications.

And have a full live installer of the new version, in case you have to make repairs and to have another way to boot. Run live installer in live mode to make sure you do not have any new issues.

Some find an upgrade takes longer than a new clean install. And before you upgrade be sure to houseclean old kernels and applications and make sure you have space for download of new data in addition to current data.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

        Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

If dual booting with Windows be sure to have a full backup of it also.


 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

       
 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by Dragonbite on 2014-09-18
Great information!

Thankfully it is a single-OS system and I have tried 14.04 on it via Live USB to see if there were any issues showing up.  It seemed to work just as well as it does with 12.04 and the Radeon video card is one that I think support was dropped to the legacy driver or something like that.  So I have been getting by with whatever Ubuntu includes by default.

I'm going to go through all of those links soon, just to make sure.  A good backup is something I may, or may not have (always second guessing myself) so I'll probably do a massive copy before I actually run the update.

I get tempted, too, to run a clean install and then only install the applications one-at-a-time (and skip any I don't really use anymore).

---

### Post by ubfan1 on 2014-09-18
I like the clean install route myself, just to get rid of all the cruft that tends to build up over time.  That said, the 12.04 to 14.04 upgrade was pretty easy -- Needed to get the very latest vmplayer, and maybe had a Postgresql DB glitch (maybe that was on a regular update, but going from 9.1 to 9.3 left the old 9.1 running on the default port (5432), and the new 9.3 on 5433, but the sources were not changed, so things depending upon them like ecpg, would fail.  I can see that as a testing phase for the new stuff, but hadn't bumped into it before.
  A straight install, with separate app installs has a gotcha if you have any 32 bit programs.  The old ia32 libs are no longer present, so you need to figure out what 32 bit packages are needed and install them.  Easy, but now ldd instead of listing the necessary libraries, wrongly claims that your 32 bit executable is "not an executable".  So starting with the 32 bit ld, start trying to get ldd to work (it's just a script), then determining necessary packages is easy.

---

