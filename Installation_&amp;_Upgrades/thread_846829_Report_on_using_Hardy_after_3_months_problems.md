---
title: "Report on using Hardy after 3 months: problems"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by quixote on 2008-07-01
I've used Ubuntu or Kubuntu since Dapper.  I love the OS, the community, the forums, and the whole experience of using Ubuntu.  The difference to my Windows experience was so big that I've only accessed that half of my dual boot system three times in two years to do my taxes.

Just recently, I got yet another person to make the switch, and they've run into the same Hardy issues I've had, which means it's not just my old slow laptop (Sharp MP30).  That made me think it might be good to list all the problems in one place.  They've all been reported as bugs or are considered features (. . . !). There's no visible movement on any of them, although as an ordinary user, I wouldn't usually know until an update fixed them.  I did a clean install of Hardy once it came out in beta, and have been updating whenever the updater says there are new files.

So let me get to it.  The List (in no particular order).

> 1) gvfs KO'ed my root partition.   
I'd used Simple Backup before.  Under Hardy, something about it caused [gvfs to decide my root partition was 2x as big as it was]("http://ubuntuforums.org/showthread.php?p=4902571#post4902571").  That filled the partition.  That meant even simple operations that required writing to /tmp couldn't be done.  I had /home on a separate partition, otherwise everything would have ground to a halt.  Fixing the problem required commands as root to delete hidden gvfs files, and changing permissions on backups and deleting.  A user unfamiliar with CLI would have been faced with a bricked computer.

2) another gvfs annoyance, minor, yet huge.
it insists on naming all partitions by their sizes and will not let me give them meaningful names!  In searching for info on this, I found out that some devs somewhere think this is a Good Thing.  Um, **NO**.  The OS can do whatever it needs to.  But the user must be able to customize look and feel to suit their own needs.

3) network-manager applet has broken.
Not having a nice little GUI frontend for dealing with wireless is a dealbreaker for some of us.  I find kde better than gnome, but I've been using gnome ever since Feisty because nm-applet started working.  Without the [workaround by wieman01]("http://ubuntuforums.org/showthread.php?t=202834"), I wouldn't have wireless.  As it is, I have to run "sudo dhclient" whenever suspend lasts longer than the current lease from the router.  Again, users who don't like CLI would be living without wireless.  Or, more likely, without Ubuntu....

4) There is some kind of problem seeing usb.
I have a usb printer.  Suddenly, one day, (about a month ago? six weeks?) my system couldn't see the printer.  After some forum work, it turned out that the command "[lsusb]("https://bugs.launchpad.net/ubuntu/hardy/+source/cupsys/+bug/35638")" would jog the system into realizing / remembering that there was something attached to a usb port.  On another machine, there was the same issue with the usb connection to an mp3 player, and the same solution.

5) gksudo not working.
 [Update-manager doesn't work]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/187982"), and also other GUI-accessible commands that require gksudo to authenticate.  (It works on some machines, but older slower machines don't do so well.)  Hitting the "update" button starts an infinite loop that can only be stopped by using "sudo kill -9 <pid>".  Many users would have to reboot to deal with that issue.  "sudo <command>" works, but there again, requires the user to be comfortable with CLI.  I don't understand why this bug hasn't been dealt with.  Seems rather critical.

6)In my case, (I'm not sure how widespread this is) [CDs can only be burned as root]("http://ubuntuforums.org/showthread.php?p=5270130#post5270130").  Actually, Brasero just wouldn't burn disks.  K3b gave me the error message about not having permission, so I tried "sudo k3b" from a terminal.  That workaround wouldn't necessarily be obvious.  This wasn't a problem in any previous version, and I haven't tweaked the CD drive. 

If this was my first experience coming from Windows -- a suddenly not-working wireless, inexplicably full hard disk, strange messages about not being allowed to burn CDs, and an update-manager that went nowhere -- I wouldn't have been *able* to continue using Ubuntu, no matter whether I loved the concept or not.  Ubuntu's strength has always been that it works much -- much! -- more easily than other Linux distros.  Let's keep it that way!  And if something breaks in a good cause, at least let us know what the chances are of fixing it and how far away we are!

---

