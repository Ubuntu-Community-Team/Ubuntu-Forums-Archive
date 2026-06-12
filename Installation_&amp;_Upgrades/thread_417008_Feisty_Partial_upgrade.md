---
title: "Feisty Partial upgrade??????"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by pketch on 2007-04-21
Hi everyone,

Hope you're all doing well. 
Instead of doing a fresh install of Feisty, I decided to try upgrading my existing Edgy installation.  Well, it appears to have gone really well.  I downloaded the Alternate Install CD and did a sudo sh /media/cdrom0/cdrominstall to start the upgrade.  Everything upgraded properly in about 40 minutes.

When I rebooted my computer, X worked fine as did my proprietary NVIDIA Driver.  I was most impressed.  The only thing negative was that it uninstalled beryl for some reason, but I easily reloaded that.  I see all of the new Feisty options like Desktop Effects and Restricted Driver manager so I assume the upgrade finished properly.  The best part is, I noticed that Realplayer doesn't stutter and I don't have to turn off Beryl anymore to play a video file or a 3d application.  Even cooler, suspend and hibernate (Which NEVER worked) are working.  Unfortunately, the resume function doesn't work at all, but at least I've got some hope of fixing that now because it will actually shut down.

So, all in all I'm extremely pleased with the upgrade and happy with Feisty.  Here's the problem:

This morning, I noticed an automatic update, and I clicked on it to see what it was.  This is the message I received:

Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
A previous upgrade which didn't complete
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-release version of Ubuntu

It listed 538MB of updates!!!  How can that be?  This scares me a little because my Feisty install is working far better than Edgy did and I *really* don't want to break it.  But if I'm only partially upgraded to Feisty, then should probably fix this.  538MB of updates sounds alot like a dist-upgrade over the net, and the whole reason I went with the Alternate Install CD upgrade method was to avoid any trouble with overloaded servers and massive numbers of people trying to upgrade all over at once.

Anybody have any ideas on what might be wrong or suggestion as to whether you think it's safe or not to go ahead and let that massive update go through?  Keep in mind Feisty is ROCKING for me right now.

Thanks for any input!

---

### Post by nevin on 2007-04-21
i got the same thing; it requires me to do a partial upgrade.  but i used the regular ubuntu cd...

but when i say go ahead with the partial upgrade, it says it can't authenticate the packages...
so i don't know about the partial upgrade....  maybe it's just me.

nevin

---

### Post by pketch on 2007-04-21
I wasn't aware that you could use the desktop live CD to do a CD upgrade.  I specifically downloaded the Alternate CD because I had read that it was the only way to do an "offline" dist upgrade.  Are you sure you are running Feisty or didn't actually do a fresh install?

I'm by no means an expert, but I wonder if your problem has something to do with 3rd party repos in your /etc/apt/sources.list.  If you want to compare, this is the contents of my sources.list which I just used to successfully run the "partial upgrade":


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe

Hope you can get your issue straightened out, good luck to you!

---

### Post by pketch on 2007-04-21
Well,

I decided to go ahead, take the plunge, and do the partial upgrade, since my Feisty upgrade had gone so well from the CD and I was feeling lucky.

It really didn't take too long to download, which surprised me.  It pulled down all 600mb of the files in about 2 hours 30 minutes.  During the upgrade, 4 packages (out of 722) gave an error message that I had to click "Close" to, but other than that the upgrade l went just fine.

After reboot, everything worked great and when I checked the update manager, there was only a single update left, an update to libfuse2 & fuse-utils.  I'd installed ntfs-3g a while back (in Edgy) and used a package from Debian rather than an ubuntu packaged version and that seemed to be the source the problem.  I just removed the packages manually and then reinstalled libfuse2, fuse-utils, & ntfs-config with apt-get and then the updates loaded fine.  It appears that Feisty now has ntfs write support enabled by default and so guess this won't be an issue next time around.

All in all, really no hassle.  I was just scared about breaking my Feisty install with such a humongous update and didn't want to lose the benefit I'd gotten from the upgrade from Edgy.

I have read the forums and know that people have had problems out there upgrading to Feisty, but I have to say that my upgrade using the Alternate CD & then this update-manager update really went off without a hitch, which is surprising considering the amount of extra stuff and customization I'd done to Edgy.  Maybe using the Alternate CD had something to do with my success (Didn't see too many posts about people using that method), but this truly has been the smoothest OS upgrade I've ever had, either Windows or Linux.

All in all, I think Feisty is great - faster, more stable, and with some nice new features.  I hope everyone out there having issues will persevere.

Thanks again for the input.

---

### Post by mattymattysidebyeach on 2007-11-30
apt-get saved my "partial-upgrade" state.
[SIZE="2"][LIST=1]
[*]update manager crashed during update downloads (network was disconnected during upgrade) 
[*]downloads still exist in the apt cache (6 hours worth of downloads in my apt cache)
[*]finishing the update via command line to be safe
[/LIST] [/SIZE]
[SIZE="3"]IMO update manager is misleading when it says "partial upgrade"; maybe its bugged and it ought to say something like:

"previous upgrade attempt failed, part of the entire download of packages has been saved, do you want to resume the upgrade with a partial download (ie the rest of the packages??) "[/SIZE]

i dunno. :confused:
-----------------------------------------------------------------------
in any event :
**apt-get update**
followed by
**apt-get dist-upgrade **

at the command line recognized the partial (botched) upgrade and is at the moment completing my upgrade for me.

---

