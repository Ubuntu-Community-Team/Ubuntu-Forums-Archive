---
title: "Breezy: porting my Hoary settings to a fresh install"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by megamania on 2005-10-07
A few months ago I installed Hoary on my secondary hard disk and loved it. I almost never boot to windows anymore, except for when I need to use skype (I'm having problems with the linux version), palm desktop and acdsee (I need the batch renaming options).

I will fresh-install Breezy on my primary hard disk (and move windows to the removable hard drive :) ), and would like to import at least my basic settings, such as desktop themes, wallpaper, customized bars, terminal window transparencies.

I know all of these things are easy to replicate, but importing them would save me a lot of time, especially considering that my linux skill from 1 to 100 is 0.9...

Any advice will be much appreciated.

-------------------------------------------------------------------------
Edit: sorry about the duplicate - I received an error msg on my first attempt

---

### Post by jasmuz on 2005-10-07
Just copy your /home directory, wich contains most of your personal configuration files.-

---

### Post by megamania on 2005-10-07
That's a quick reply!

Is that really all I have to do? Will settings be automatically applied? That's good news...

Thanks!

---

### Post by Joey French on 2005-10-07
After copying the old Hoary /home folder (and doing the fresh install), would one just replace the fresh Breezy /home folder with the old one, and call it a day? Could someone elaborate on exactly how to accomplish this?Is it really that simple? I am in the same boat, need to move old Hoary settings to fresh Breezy install.

Thanks!

---

### Post by blueturtl on 2005-10-07
> After copying the old Hoary /home folder (and doing the fresh install), would one just replace the fresh Breezy /home folder with the old one, and call it a day? Could someone elaborate on exactly how to accomplish this?Is it really that simple?

The safest way would be to just redo all the setting up, since Breezy contains newer versions of certain apps and writing their config files with older ones could potentially cause problems.

If you guys want to go ahead with the backup plan note this:
Most of the applications you use store their settings and data in hidden folders under your /home folder. The folders are hidden with a "." in front of the folder name, so for example your MPlayer settings folder might be /home/youruser/.mplayer

Instead of just backuping all the files in your /home folder look for the app spesific settings folders and copy those, onto a CD-RW, or a USB-memory stick or whatever (can even be a second hard-drive). Then after you're done installing the new OS just move the files into your home folder.

For example I'd propably be wanting to backup

.evolution (for my emails, contacts etc)
.xmms (for skins and playlist etc)
.mozilla (my bookmarks, skins etc)

but there's also a lot of stuff, that's non-important, so why risk breaking things?

Also, make sure if you back up the files on a new volume that the ownership and group info on the files is coherent with your new groups and usernames. If you change usernames during the new install, the files after backup can still retain their original ownerships if backuped on a permissions-capable file system, and thus you'd be denied access to them.

Hope this clarifies things for you a bit.

---

### Post by Joey French on 2005-10-07
Hmmmm...

:chinscratching:

---

### Post by megamania on 2005-10-07
[QUOTE=blueturtl]The safest way would be to just redo all the setting up, since Breezy contains newer versions of certain apps and writing their config files with older ones could potentially cause problems.

Instead of just backuping all the files in your /home folder look for the app spesific settings folders and copy those, onto a CD-RW, or a USB-memory stick or whatever (can even be a second hard-drive). Then after you're done installing the new OS just move the files into your home folder.
...
but there's also a lot of stuff, that's non-important, so why risk breaking things?

Also, make sure if you back up the files on a new volume that the ownership and group info on the files is coherent with your new groups and usernames. If you change usernames during the new install, the files after backup can still retain their original ownerships if backuped on a permissions-capable file system, and thus you'd be denied access to them.

[/QUOTE]

You *did* clarify things. My main concerns were (a) that I would end up copying stuff related to applications that I don't need anymore and (b) messing things up with data that I *do* still need.

Also, the problem of file ownership is BIG in my opinion - thanks for pointing that out because I had overlooked it.

In the end, these are my (temporary) conclusions:
-it's better to fresh-install everything, copying only data-files such as thunderbird mail folders.
-if you don't want to set up your configuration from scratch, it's better to upgrade rather than export the configuration files to a Breezy fresh-install.
-upgrading is not 100% safe either because it may cause compatibility problems.

This confuses me a little bit, as I had always read that Linux in general doesn't need to be reinstalled at all - and now I find myself having to fresh-install every six months in order to have the newest versions.

Is that correct?

---

### Post by blueturtl on 2005-10-07
> In the end, these are my (temporary) conclusions:
-it's better to fresh-install everything, copying only data-files such as thunderbird mail folders.
-if you don't want to fresh-install, it's better to upgrade rather than export the configuration files to Breezy.
-upgrading is not 100% safe either because it may cause compatibility problems.

This confuses me a little bit, as I had always read that Linux in general doesn't need to be reinstalled at all - and now I find myself having to fresh-install every six months in order to have the newest versions.

Is that correct?

Well it is possible to never have Linux reinstalled. I mean if you have a working system, all you need to do is install newer versions of the applications you want. You can even install and run a custom kernel if you want. It's totally possible to install applications not supported by the Ubuntu team. Just compile and install from source code and make sure you have all the necessities. The thing is, it's so nice when someone else does all the testing and packaging for you. ;) Configuration can be a headache, and Ubuntu has superb out-of-the-box functionality. This is why for some reinstalling is a good option.

I'm going to be upgrading to Breezy once it's out because I'm sure it'll be even more polished and functional than Hoary, and I like fiddling with things. As for the need, there really is none for me. Everything I want already works with Hoary. You don't have to upgrade for the sake of upgrading in the Linux community. Only if there are fixes or improvements you like.

Consider this: if you set up your system smartly, you won't have to do much work at all during the installation of a new OS upgrade. Case in point:

When I'm going to upgrade to Breezy, I'm going to partition my system so that my /home folder is separate from everything else. This will allow me too keep all my files and settings intact even in the case of a totally new installation as the /home doesn't have to be formatted!

---

### Post by megamania on 2005-10-09
I decided I'll fresh install Breezy on my primary hard drive, then copy all the data I need from the secondary hard disk (the one which currently holds Hoary) to Breezy.

I'm still thinking about the file ownership problems: I have 130Gb worth of data, so copying them to a memory stick, cd or dvd is crazy. What do I have to do to get sure I'll be able to access my hoary's home directory from breezy?

---

### Post by blueturtl on 2005-10-10
> What do I have to do to get sure I'll be able to access my hoary's home directory from breezy?

Well. If you create a username different from your old Hoary user, you can always use superuser rights to firstly copy the files over to your new hard-disk (if required). You can then change the file ownerships as well. If you're not going to be moving the files, just change their ownerships if you don't have the same username anymore.

Start up a console, or switch to a text mode terminal with CTRL+ALT+F1

Copying the files can be accomplished with a **sudo cp -R /sourcedir /targetdir**

The **-R** (recursive) parameter will ensure all your subdirectories and files will be copied also.

Say I created a new username such as newuser. However all my old files in /shared would be owned by olduser. I could easily change the ownership of all the required files with a

**sudo chown -R newuser /shared**

and the same for file groups:

**sudo chgrp -R newuser /shared** (don't do this, if you have spesified custom groups)

If you're afraid of the commandline, I'm sure there must be a way to do this in Gnome too, although I wouldn't recommend it. It's so much faster and handier this way. ;)

edit: note that if you use 'sudo' you will have to enter your password before the system permits any action to take place.

---

### Post by FLeiXiuS on 2005-10-10
I don't know about you guys, but I tweak everything, a good 6 hours worth of tweakings and testing.  Most of which aren't done in ~/.  

I'd prefer to do the dist-upgrade.  I have yes encountered one problem, which was fixed by the updates today!

It'll aleviate a lot of pain you may have redoing everything.

---

### Post by megamania on 2005-10-11
Thanks. Quite a lot of useful information. Like many of us, I grew up with the DOS command line interface, so I'm not afraid of it at all, but I just lack Linux knowledge.  :( 

Anyway, I'm not going to change username, so it looks like I'll just be able to copy my data straight from one hard disk to the other one.

Thanks again,
gianfranco

---

