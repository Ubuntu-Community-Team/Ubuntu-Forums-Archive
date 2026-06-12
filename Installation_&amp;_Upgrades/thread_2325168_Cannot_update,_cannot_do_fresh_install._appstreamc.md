---
title: "Cannot update, cannot do fresh install. appstreamcli at 100% cpu"
date: 2016-05-19
forum: Installation &amp; Upgrades
---

### Post by The Cog on 2016-05-19
I am trying to install Xubuntu 16.04 32-bit but am unable to do so. The installer is stuck on "Retrieving file 48 of 48" and top shows appstreamcli stuck at 100% CPU.

So then I tried to install without downloading updates as it went. The install worked, but a post-install apt-get update hung, again with appstreamcli stuck at 100% CPU.

So then I thought I'd try apt-get update on my main 64-bit desktop and guess what: It hangs, and top shows appstreamcli stuck at 100% CPU.

Does anyone know of a way to fix this? Obviously, reinstalling isn't going to work. It looks to me like a recent update has borked something.

---

### Post by Brandon_MacEachern on 2016-05-19
Yep, I just wiped out a hard drive to install Ubuntu 16.04 same EXACT issue.

I can install by telling it not to do updates, and turning off wifi, but then I can't run apt-get update later.  It just freezes at hit 4.

---

### Post by The Cog on 2016-05-19
FIXED!

While the update/install is running, open two more terminal windows. In one terminal run the command **top**. In the other terminal, every time top shows appstreamcli, run the command **sudo pkill appstreamcli**.
Of course, you can't do that if you choose to "install" from the live installer - you have to choose to try before installing, and then use the install icon on the desktop.

---

### Post by Brandon_MacEachern on 2016-05-19
You'll still end up however without being able to update the install afterwards.  The server is down.

---

### Post by The Cog on 2016-05-19
That's probably a good thing. I guess they've done that to stop it issuing updates until they can rustle up a fix.

---

### Post by Brandon_MacEachern on 2016-05-19
It's however put production here at a stand still.  We can't install .deb packages because we can't even satisfy the dependencies, that we usually can.

LTS shouldn't be interrupted like this.

---

### Post by The Cog on 2016-05-19
Actually, the UK mirrors are still up. 
I also tested replacing the /usr/bin/appstreamcli executable with an executable empty file, and that gets rid of all the nasty errors in apt-get update. But I don't recommend doing that.
I presume that another update soon will replace that executable with a better behaved version.

---

### Post by Brandon_MacEachern on 2016-05-19
Well if the binary itself is the problem, this should not have made it in an LTS release.  Because now how do you update something required to run the updater?  This is literally like a meme.

"Yo dawg I heard you like updates, so I updated your updater to update your updates".

---

### Post by The Cog on 2016-05-19
I think it's likely a combination of bad metadata and an executable that doesn't handle it well. In which case they should both be fixed, but fixing either would make the current problem go away.
But I'm guessing, I really don't know.

---

### Post by Brandon_MacEachern on 2016-05-19
Well, I'm gonna go back to drinking my Scotch, tell my boss stuff's broke, and it ain't my fault.  lol

---

### Post by Bashing-om on 2016-05-19
et all ; Yuk

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845)

in the appstream package ->  check-all-the-things (source: check-all-the-things): check all of the things!. In component universe, is optional.

Seeing this issue also on IRC.

[INDENT][INDENT]it's broke
[/INDENT][/INDENT]

---

### Post by Jonathan Provost on 2016-05-19
Simply removing the faulty package worked for me.

[FONT=courier new]$ dpkg -S appstreamcli[/FONT]
[FONT=courier new]appstream: /usr/bin/appstreamcli[/FONT]
[FONT=courier new]appstream: /usr/share/man/man1/appstreamcli.1.gz[/FONT]
[FONT=courier new]$ sudo apt remove appstream[/FONT]

---

### Post by Brandon_MacEachern on 2016-05-19
Should I really be issuing the sudo rm command while drunk?

Maybe bad idea.

EDIT: Even worse, you didn't say to use sudo rm.  Yea, I'm done with terminal for now.

---

### Post by waipeng on 2016-05-19
> **Jonathan Provost said:**
> Simply removing the faulty package worked for me.

[FONT=courier new]$ dpkg -S appstreamcli[/FONT]
[FONT=courier new]appstream: /usr/bin/appstreamcli[/FONT]
[FONT=courier new]appstream: /usr/share/man/man1/appstreamcli.1.gz[/FONT]
[FONT=courier new]$ sudo apt remove appstream[/FONT]

Thanks this works!

---

### Post by forums-etarq on 2016-05-20
> **Jonathan Provost said:**
> Simply removing the faulty package worked for me.

[FONT=courier new]$ dpkg -S appstreamcli[/FONT]
[FONT=courier new]appstream: /usr/bin/appstreamcli[/FONT]
[FONT=courier new]appstream: /usr/share/man/man1/appstreamcli.1.gz[/FONT]
[FONT=courier new]$ sudo apt remove appstream[/FONT]

What does this app do, exactly?

I've disabled the auto update for apt on my mythtv backend server to prevent this from taking up all the CPU.  But I am not sure I should uninstall this package since I'm not sure what effect it will have on mythtv working?

Thanks!

---

### Post by vasa1 on 2016-05-20
> **forums-etarq said:**
> What does this app do, exactly?
...
You can read about it here: [https://www.freedesktop.org/wiki/Distributions/AppStream/](https://www.freedesktop.org/wiki/Distributions/AppStream/) and check *man appstreamcli* if you have appstream installed. I don't. It isn't part of Lubuntu :)

Seems it's something since 15.10 that > provides the foundation to build software-center applications, by providing metadata necessary for an application-centric view on package repositories. AppStream additionally provides specifications for things like an unified software metadata database, screenshot services and various other things needed to create user-friendly application-centers for (Linux) distributions. ...

The specification now also contains a description of DEP-11, which is a YAML-based version of the distro XML specification used by Debian and its derivatives.
I was wondering about this DEP-11 business.

*apt show appstream* indicates that this thing is part of the following DEs:```
ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-full, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, 
mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, 
ubuntustudio-desktop, ubuntu-gnome-desktop, ubuntukylin-desktop
```

---

### Post by forums-etarq on 2016-05-20
Thanks, I guess I better not remove it!  I am using xubuntu-desktop for the mythtv-backend since the mythtv setup requires a GUI as far as I know to set up tuners, etc.

---

