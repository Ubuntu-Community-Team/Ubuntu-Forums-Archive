---
title: "Two big issues..oh please help"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by GmAz on 2006-06-16
Ok...I have two issues that are out of my league.  First one is the major one.

I have three hard drives.  I have Ubuntu on its own hard drive and all was well.  Then I got the Vista beta 2 and decided to see what it looks like and how my system stacked up.  I installed it on another hard drive but apparently Microsoft likes to overwrite all boot sectors so now I can't boot to Ubuntu anymore.  I realize a re-install of ubuntu would take care of that, but I don't want to do that.  I have done a lot to get it working the way I want it.  Is there a way to re-install grub running off the Live CD?  If so, I would like it to pick up both Ubuntu and Vista.  

Second issue is that right before I installed Vista, Ubuntu told me that it had an update for several 'glib' files.  I installed the updates and it said a reboot was required.  Upon reboot I get the command prompt telling me that XServer cannot load.  I type in GDM in the command prompt to load Gnome and nothing.  Just the command prompt.  How can I get Gnome back?  I did install the newest NVidia drivers if that helps.

The main thing I need is getting Ubuntu bootable again.  Right now, Vista sucks, doesn't recognize my Wifi adapter and is slow as hell.  And no, I don't have a slow system.  It crashes and takes like 5 mins to fix itself.  I guess I can't expect much form a beta.

---

### Post by jchau on 2006-06-16
For the GRUB issue, [this]("http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation") should help.  I never had to try it, but it seems to be the solution.  I'm not sure if the Desktop install CD has a rescue mode.  If it doesn't, try the alternate CD.  Hope this works.

As for the X issue, there seems to be an [entire thread]("http://ubuntuforums.org/showthread.php?t=187177") devoted to it.  If that doesn't work, try posting the exact errors you get, or a log file with those errors.  (eg. try to elaborate "and nothing" is it an error, or does nothing really happen).  If your X works properly, you should be able to "get Gnome back" by entering the command "startx".

---

