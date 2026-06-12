---
title: "Upgrade from LTS 6.06.1 to LTS 8.04 issue"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by cotcom on 2008-05-01
During the upgrade at the stage where I'd typed the command "sudo aptitude install update-manager-core" a message displayed: "Media Change: Please insert the disc labelled 'Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)' in the drive '/cdrom/' and press enter"

I did this and got the following message:

"aptitude_download_signal log.cc:67: virtual bool download_signal_log: :MediaChange(std: :string): Assertion 'rval != -1' failed.
Aborted"

Then the next line was:

root@ubuntu:~#

---

### Post by cotcom on 2008-05-01
Sorry, should have said this is a server installation not desktop.

---

### Post by njparton on 2008-05-01
You probably need to edit your /etc/apt/sources.lst file (I think that's the right path) to remove the CD-ROM entry.

---

### Post by cotcom on 2008-05-01
Thanks nj.

Interestingly, I can no longer use the CD ROM!

I have two files listed: sources.list and sources.list~ and sources.list.d, which  I assume is a directory.

Should I just rename sources.list & sources.list~ as opposed to deleting them and will that give me back access to the CD ROM?

Also, the version has upgraded to 6.06.2 - probably during the course of entering commands such as sudo aptitude install update-manager-core.

As you can tell I'm a newbie!

Thanks for any more assistance you may be able to give.

Richard

---

### Post by cotcom on 2008-05-01
I've renamed sources.list to 1sources.list and sources.list~ to 1sources.list~

I now have use of my CD ROM again.

Would it be easier to overwrite the previous installation with the 8.04 disc I have and if so how would I do this? I haven't used the 6.06 version so wouldn't be "losing" anything.

---

### Post by njparton on 2008-05-02
You can also use synaptic to remove the CD-ROM reference from the repository list.
 
Files with "~" in their names are just old buffers (temp files) and can be safely ignored/deleted.

---

### Post by cotcom on 2008-05-02
Thanks for that nj - I wondered what the ~ stood for.

A little later I'm going to try the upgrade process again - probably this evening.

---

### Post by cotcom on 2008-05-04
Have now attempted the following:

====================
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade

sudo aptitude install update-manager-core

sudo do-release-upgrade
=======================

It upgrades to 6.06.2 but not 8.04.

I tried complete reinstall of 6.06.1 from my original disk. Wiped all partitions with the new install. Wasn't sure how to setup networks so skipped that stage. It said it couldn't set up dhcp server.

Ran upgrade procedure again:

====================
sudo aptitude update
====================

Got the following messages:

=============================
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
 Temporary failure resolving security.ubuntu.com
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg
 Temporary failure resolving gb.archive.ubuntu.com
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg
 Temporary failure resolving gb.archive.ubuntu.com
Reading package lists... Done
=============================

Do I ignore this and carry on with:

=====================
sudo aptitude upgrade
sudo aptitude dist-upgrade
sudo aptitude install update-manager-core
sudo do-release-upgrade
=======================

I guess life was never meant to be easy! Any help appreciated!

Richard

---

### Post by Tiede on 2008-05-04
The temporary failures in resolving the different URLs stem from the fact that the network isn't configured/up.
If you only want to use the cdrom, you can copy your sources.list with ```
cp sources.list sources.list.old
``` for example, and then edit your sources.list to only contain the cd-rom entry (usually at the top of the file). I.e, delete all other entries in the sources.list file.
That oughta do it... I think. :-?

---

### Post by njparton on 2008-05-04
If you did a complete reinstall of 6.06, why not reinstall with 8.04?

---

### Post by Tiede on 2008-05-05
I agree with njparton. If you did a complete reinstall of Dapper, you might as well just download the hardy .iso, burn it, and install without headaches that way.

---

