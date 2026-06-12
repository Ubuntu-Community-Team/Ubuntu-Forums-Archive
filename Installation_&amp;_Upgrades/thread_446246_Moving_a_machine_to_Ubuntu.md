---
title: "Moving a machine to Ubuntu"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by leona on 2007-05-16
Hi there.

I wonder if anyone could tell me the best / easiest way to do this.

I have a machine running Suse 10, and I wish to move it to Ubuntu, its easier if I only have to support one Distro :)

But I do not wish to loose any data, personal settings, etc, so when I've installed Ubuntu the system should be mostly up and running with access to network shares and the users documents.

Now /home is on a separate partition if that helps.

Now assuming, if I make a backup of the /etc dir, (for the files I need), then whack the Ubuntu CD in, install and ensure it leave /home alone (don't know how I'll tell since I don't think it mounts them, that could be an issue?) and then install it.

My fears are that the user will not then have access to their files becuase the uid / gid will be different, can I ensure that this is maintained?

Anything else I need to consider?

Thanks

---

### Post by leona on 2007-05-17
Oh dear, is it that hard to do?

---

### Post by IgnorantGuru on 2007-05-17
> **leona said:**
> Hi there.

I wonder if anyone could tell me the best / easiest way to do this.

I have a machine running Suse 10, and I wish to move it to Ubuntu, its easier if I only have to support one Distro :)

But I do not wish to loose any data, personal settings, etc, so when I've installed Ubuntu the system should be mostly up and running with access to network shares and the users documents.

Now /home is on a separate partition if that helps.

Now assuming, if I make a backup of the /etc dir, (for the files I need), then whack the Ubuntu CD in, install and ensure it leave /home alone (don't know how I'll tell since I don't think it mounts them, that could be an issue?) and then install it.

My fears are that the user will not then have access to their files becuase the uid / gid will be different, can I ensure that this is maintained?

Anything else I need to consider?

Thanks

I would make backups of /etc/fstab and /etc/exports - in fact just backup the whole /etc folder for reference like you said.  And certainly /etc/X11 - always handy to have the xorg.conf for your hardware.  (This came in mighty handy when moving from SUSE, because Ubuntu didn't configure my video hardware as well.)

Then install Ubuntu but don't tell it about the /home partition, just let it put /home on /.  The installer should mount your old home partition as something like /media/hdax (I would verify this though - it may detect it as a home partition?)

Then carefully compare new and old fstab files and modify as desired.  Copy exports.

Also note that SUSE installs some things by default which Ubuntu does not, such as nfs-server and ssh-server, so you may need to add those.

Now create the users.  If you create them in the same order the uids should be the same, but you can double check that.  As long the uid/gid matches then it should be happy.  If not, just change the ownership of the home folders and contents (before mounting as /home) - simple enough.

I would backup the old /home before directing Ubuntu to use it.  I'm a KDE user and when I moved from SUSE to Kubuntu I chose to start from scratch, home folders and all.  There are some differences, but I don't know what the details are.  I did copy some of the program configuration subfolders, but the core KDE stuff I reconfigured from scratch.  In my example, SUSE and Kubuntu set up KDE a bit differently, so I didn't want the hassle of dealing with a lot of weird config issues later.  That said, maybe it would have worked.  ???

You may also want to backup your SUSE partition - never hurts...
[http://kubuntuforums.net/forums/index.php?topic=13735.0](http://kubuntuforums.net/forums/index.php?topic=13735.0)

---

### Post by leona on 2007-05-18
Arrr lovely, thanks very much, that's all seems in order, it'll be moving it from Suse (KDE) to Ubuntu (Gnome) you think I'll have any issues doing this?

Right time to find my external hard drive and do some backing up, thanks :) actually thinking about it, its not a big drive I could just ghost an image, hum.

---

