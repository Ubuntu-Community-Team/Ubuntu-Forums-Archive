---
title: "Seeking a HOWTO on using live cd as repository during a net-based upgrade"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by bradtem on 2008-11-20
I always download the live CD even if I am upgrading, to be sure the new release will work on my hardware.   So when I actually do the upgrade it seems silly to have it pull everything down from the net.  Or to do it again on other machines.

I know that you can use apt-cdrom to make the live-cd's repository get used in an upgrade.  However, my searches don't find any specific howto on the full steps to do this.  Presumably you do it before the upgrade, since you don't really have a chance during the update manager or adept based upgrade.

Note that I am not interested in a CD-only upgrade.  I want to be connected to the internet so I can download upgrades for packages not on the CD, or for any packages updated since the CD.   The few howtos I have seen seem to assume if you are using apt-cdrom that you want to do an install with no connection.   I don't want that.  I want something that looks exactly like an upgrade using a connection, but it fetches the package from the live-cd if it can be found there, and from the net otherwise.

Indeed, I am surprised the standard upgrade program doesn't do this and say "If you have the live or alternate install for this release, put it in your drive now" (or just check to see if it is there.)  This would save the servers lots of bandwidth.

---

### Post by EXCiD3 on 2008-11-20
Don't know if it would help you or not, but you could check out APTonCD, it allows you to make custom discs that work just like repositories. I also am working on a program to download the latest packages onto a USB key to upgrade computers without internet called Keryx (link is in my signature), that might come in handy. I dont know of anything that does specifically what you are looking for, but these might be worth look.

---

### Post by bradtem on 2008-11-22
No, that's not particularly helpful.  The goal is to save time.  I want to do pretty much the normal upgrade procedure with effectively one change:  If the .deb file it wants is on the live-cd I have put in the CD-drive (or put in a mounted loop device ISO on disk) it pulls it from there rather than wasting time and bandwidth getting it from the internet.

Is this hard or trivial to do?

---

### Post by bradtem on 2008-11-23
While I'm at it, something else, sort of related to aptoncd, would be a recording of all the packages I have personally installed with apt-get (or adaept/synaptic.)   I mean what I actually installed, not what was also pulled in as a dependency for those packages.   And a list of what I've removed, if I've removed any standard packages.

The result would be a more compact (and more human editable) list of what to install on top of a fresh system in order to get a system the way I like it.   In addition, it would handle changing dependencies, in that sometimes packages change what they depend on and how, and I just want to know what the human user of the system asked for, not what the tree derived.

Any way to do that, or would the package tools have to be changed?

Need to log anything I manually put in with dpkg as well.

---

### Post by EXCiD3 on 2008-11-23
Sorry i cant help much on the upgrade option, but for your second post i might be able to help. Check out /var/lib/dpkg/ in there is the information that dpkg has, such as your status file which keeps track of all the packages installed. you may also look at the apt folder (i think its /var/lib/apt) and check the files in there, you should be able to use the data in those files/folders to get what you need if you have any programming experience. as for not gathering the dependencies, you could just ignore them correct?

---

### Post by bradtem on 2008-11-24
Yes, I'm aware of the apt folders and have in the past extracted a list of all packages installed, and subtracted it from a list of what comes with a raw distro.  However, that does not attain my goal of isolating what the user has done.   I believe the right way to encapsulate information about changes to a system is to look at what the user asked for, not the consequences of it.   A complete list of packages will included in my case hundreds of them, and as I noted in some cases it will be a wrong list in that dependencies change, though this is fairly rare.

My ultimate goal would be to be able to encapsulate everything needed to turn a fresh install (of a new version typically) into the way a user likes it customized.  The long term way to attain that goal is to convince all systems to maintain owner/sysadmin-changed config in a different filesystem from the root, which is where package-author and distro maintainer changes go.

A dream would be to have a package of files and scripts that knows all packages I want to install, all config files I want to change (as patches that can be applied to the new changed config files that come with the new release) so that with one command you can turn a fresh install into "your" system.  You can do that for stuff that is truly user based (and kept in /home) but not for stuff that is "owner/sysadmin" based.

---

### Post by EXCiD3 on 2008-11-26
Looks like quite a task. Everything is the user chooses to install will have to be monitored closely and that could take some work. As far as i know, you would almost have to manually write down each package and the dependencies it needed and make a list yourself and then make a custom iso using APTonCD and then throw in some scripts for those configuration files you need to be edited. You could also install them in those scripts but the best i can think of is just writing down all the changes you want starting with a base install. I sort of did this for a network i setup over the past summer using APTonCD and the like.

---

### Post by bradtem on 2008-11-26
> **EXCiD3 said:**
> Looks like quite a task. Everything is the user chooses to install will have to be monitored closely and that could take some work. As far as i know, you would almost have to manually write down each package and the dependencies it needed and make a list yourself and then make a custom iso using APTonCD and then throw in some scripts for those configuration files you need to be edited. You could also install them in those scripts but the best i can think of is just writing down all the changes you want starting with a base install. I sort of did this for a network i setup over the past summer using APTonCD and the like.

A lot of work for a user to do, that's the point.  Trivial for the package management tools to do, all they would have to do is record a log or list of what the user asked for.  It's like one extra logging statement for them.  For extra credit a database where deleted entries are removed would be good.

But I know I'm not alone here.  How many others have blanched at the choices we now get -- either do upgrades, with all the problems they entail (as well as the perpetuation of old problems you hope to be rid of) or do fresh installs with a ton of work to remake the system as you like it, with all the added packages and changed configuration files.  Anything to make that easier is a big plus.

---

### Post by EXCiD3 on 2008-11-26
Yeah but thats problem is most likely going to stick around in the future sadly. With software comes the ability to do anything you want...which means that you dont have to stick to anyones standards no matter how nice it would be to have them. I am about to release my next version of Keryx and would love to help implement some of these features if they would help you at all. For example, choosing to download a package such as Firefox, we could configure it to log that the user chose Firefox and then list all the dependencies that were downloaded for it. Contact info is on my profile if you would like to chat over IM or via email on this or anything else. :)

---

### Post by bradtem on 2008-11-26
Keryx sounds handy for those in that situation.  But bandwidth I am not tremendously short of, like your users.  It is time I am short of, and we all spend too much time sysadmining our boxes.   Yes, we love to tweak them and configure them, but this does not mean we have to give up ease of maintenance, or should not mean it.    

In fact, many packages have been moving in the direction I describe.  The big packages like apache and several others have moved to storing localized configuration info in a special directory for example, which you can grab and move to another system fairly easily.  (They just need to go the last step and move this directory out of root filesystem space and into a filesystem that is changed only by or for the sysadmin.   I use /local for that on my systems, though I have a much grander plan.

---

### Post by ugm6hr on 2008-11-27
I am not an expert on upgrades etc, but I thought I might offer my views:

A LiveCD cannot be used to upgrade.  Presumably something to do with all the files being compressed, but I don't know.  The AlternateCD can be used, but doesn't have the benefit of allowing you to check if your hardware works OK.

If you keep a separate /home partition, a LiveCD can be used to do a fresh install, while preserving your /home files and settings, in addition to installing all the Ubuntu default apps.  However, you do have to reinstall all your manually installed apps (which is obviously an issue for you).

The issue of keeping a list of user installed apps (without all dependencies) seems a good idea.  I have no idea if this is possible.  However, when you upgrade, all of the installed packages are updated in any case, so changes in dependencies don't make any difference.

You can easily create a list of (all) installed packages, and issue a single command to install them all after a fresh reinstall with this: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

deborphan will identify any unused libraries, so you could remove them after an upgrade (or before):
sudo aptitude remove `deborphan`

---

### Post by bradtem on 2008-11-27
Thanks.  Seems like being able to cache packages from the livecd would be a big win for ubuntu just in bandwidth during upgrades, as well as being faster for users.   I don't know enough about the package system yet to contribute code for that, however.

My long term goal is that there should be almost no difference between a fresh install and an upgrade.   People have been working in this direction on many packages, as well as those who seek to build systems where the root filesystem is mounted read-only.  But this is all still far away.

---

