---
title: "NFS mounts and autofs in Hardy Heron"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by jrickard on 2008-04-29
Upgraded two machines today to 8.04 using the UPGRADE button.  Fairly flawless if lengthy upgrade process.

I had been using NFS to access directories between machines and had used AUTOFS to automatically setup and maintain the connection.  Worked flawlessly for months.  

After upgrade, the NFS shares do not appear.  They had been in /mnt for a series of five machines actually. 

IF I enter sudo /etc/init.d/autofs restart, the files and subdirectories actually appear under /mnt - for about 3 seconds.  Then they disappear before my eyes - simply wipe off the screen in nautilus places.  I can enter the command again and they do it again.

Something in the upgrade has broken autofs.  I can still put things in exports and manually mount them.  But I can't use autofs.

This happened on BOTH the machines I upgraded.  Clearly some kind of software was added or changed that has killed it.  But I don't know what.

I also see a problem that just seems to be a bug.  If I try to restart from either SYSTEM/ADMIN or just from the reboot button on the toolbar, the machine freezes and simply will not respond.  All screens are locked.

Jack Rickard

---

### Post by balix on 2008-04-30
Jack,

I have the same problem. The log file (/var/log/messages) shows that somehow the name of the host is passed to NFS as a mount option:
 kernel: [19674.389482] NFS: unknown mount option: EarthCluster
My way around this was to edit auto.master uncomment the auto.net mounting and set up auto.misc to mount exports from the server. This is not as nice as the auto.net but at least it works. have you reported it as a bug, yet?

Balazs Nemeth

---

### Post by jrickard on 2008-05-05
Actually, I had an entry to auto.ubuntumini in auto.master.  That file contained the mounts to /mnt.

So how did you modify auto.misc to mount the exports?

No, I haven't filed a bug report yet.  Hoping to get more information.  Surely we're not the only two to use autofs to mount NFS shares????

Jack Rickard

---

### Post by pro003 on 2008-05-05
Download through Synaptic "ntfs-config" and "ntfs-3g".

that has done pretty good job for me...

---

### Post by balix on 2008-05-05
I was mounting two directories (export and export1 ) from the host name EarthCluster under /mnt/nfs.
When it was mounted the path was for export was:
/mnt/nfs/EarthCluster/export

To get the same path with a fixed mount, I commented out the original auto.net mounting in auto.master and added the line shown below.
 #/mnt/nfs        /etc/auto.net EarthCluster
/mnt/nfs/EarthCluster        /etc/auto.misc

Then I added the following to auto.misc
export  -fstype=nfs,hard,intr,nodev,nosuid,nonstrict,async EarthCluster:/export
export1 -fstype=nfs,hard,intr,nodev,nosuid,nonstrict,async EarthCluster:/export1

It would be nice to get the auto.net back! That is a lot cleaner solution and would track if anything changes on the nfs server EarthCluster.

Balazs

---

### Post by Greslore on 2008-05-05
I am having the same exact issue.  /net automounting will intermittently show mount points that I need to access.  One second the mount point is there, the next, its gone.  This really screws me up because I use autofs to mount install dirs for new configs and moreover to mount home dirs for users.  :(

---

### Post by jrickard on 2008-05-06
I think I found it.  I don't know WHY I found it.

Check /var/logs/syslog.  It was barfing on rsize=8192.  I removed those, and I'm back to automounting under /mnt.

My auto.master contains:

```
/mnt  /etc/auto.ubuntumini --timeout 300 --ghost
```

My auto.ubuntumini contains:

```
ubuntumini  		-fstype=nfs,wsize=8192,hard,timeo=14,rw,tcp        169.254.200.200:/home/jrickard
ubuntuminiwww  		-fstype=nfs,wsize=8192,soft,timeo=14,rw,tcp        169.254.200.200:/var/www
videomonster  		-fstype=nfs,wsize=8192,soft,timeo=14,rw,tcp        169.254.200.230:/home/jrickard
videomonsterwww  	-fstype=nfs,wsize=8192,soft,timeo=14,rw,tcp        169.254.200.230:/var/www
#miniTX  		-fstype=nfs,wsize=8192,soft,timeo=14,rw,tcp        169.254.200.201:/
macintosh		-fstype=nfs,wsize=8192,hard,timeo=14,rw,tcp,       169.254.200.225:/
```


Apparently there are some changes to autofs options.  On another machine, it was barfing on timeo14 and wanted timeo=14.  

One odd thing I noticed in the logs is a constant attempt to mnt .TRASH and .TRASH-1000.  Where did THAT come from????

In any event, at a command line, enter 
```
sudo /etc/init.d/autofs restart

```
And then go check /var/logs/syslog.   It should give you a pretty clear indication as to what options you're using that autofs now for some reason doesn't like.



Jack Rickard

---

### Post by rolfpal on 2008-05-08
I am having trouble with an nfs share as well, the share is on a router equiped with a 500 gb usb drive (asus wl500W with oleg firmware) my machine doesn't see the mount, see following

I tried mounting it with sudo mount 192.168.1.1:/tmp/mnt/disc0_1 /media/nfs
 
no go but it still sees it

showmount -e 192.168.1.1
Export list for 192.168.1.1:
/tmp/mnt/disc0_1 *

the router thinks it did mount ("192.168.1.11")

showmount -a 192.168.1.1
All mount points on 192.168.1.1:
192.168.1.11:/tmp/mnt/disc0_1
media:/tmp/mnt/disc0_1

Another machine mounts it OK ("media")

---

### Post by pro003 on 2008-05-09
i was having problems too with mounting nfs share and my samba network sees every single computer on wireless network isp and does not see the xp in my son's room which is connected through lan. i tried everything that i found on internet regarding samba configuration but still could not see xp machine in my other room....:lolflag:

---

### Post by Ancientmtk on 2008-05-09
Anyone have more on this issue?  I have the same problem with autofs...

I have everythign setup according to the doc and yet autofs isn't mounting the network drive.  I read daemon.log and it has alot of failed mount with .Trash and .Trash-1000

---

### Post by couzin2000 on 2008-06-23
I have been wondering why I was having such a hard time with autofs. Now I know I'm not the only one with this problem. Please keep in mind I'm not too familiar with this stuff.

I have 2 computers:```
sebastien-laptop
sebastien-desktop
```
In [FONT="Courier New"]sebastien-desktop[/FONT], there are 3 drives, 1 has Ubuntu, the others are storage: [FONT="Courier New"]Downloads[/FONT] & [FONT="Courier New"]Video[/FONT]. Both computers are on a router, both are setup with static IPs, and both are accessible to each other - at least manually. I can, without a hitch, type into my laptop```
sudo mount 192.168.0.102:/media/Video /home/sebastien/sebastien-desktop-video
``` and it will mount.

The way I read this is, I must sudo into [FONT="Courier New"]/etc/auto.master[/FONT] and edit the lines at the bottom so that designated mount points on the local pc will refer to a file, [FONT="Courier New"]auto.*[/FONT]. Then I could create a file with any suffix I want and have multiple mounts.
So I created [FONT="Courier New"]/etc/auto.video[/FONT] and added the line:```
*                  192.168.0.102:/media/Video
```
Hopefully this would work when I refer to it in [FONT="Courier New"]auto.master[/FONT]:```
/home/sebastien/sebastien-desktop-video         /etc/auto.video
```

For awhile, this worked automatically, but now that I have something a little bit more elaborate (2 separate mount points for 2 networked drives), I get this problem: the drives dont mount properly and disappear. Also, I do get [FONT="Courier New"].Trash, .Trash-1000, .hidden[/FONT] icons that appear on my desktop. What gives here?

I checked [FONT="Courier New"]/var/log/syslog[/FONT], but didn't find much in the file except for the fact that the laptop tries to mount [FONT="Courier New"].Trash[/FONT] &etc. So I'm back to square one.

I googled [FONT="Courier New"]autofs[/FONT] and found stuff in _[http://help.ubuntu.com/community/Autofs]("http://help.ubuntu.com/community/Autofs")_, in _[http://www.autofs.org/]("http://www.autofs.org/")_, and a few other sites - but none of the info is more recent than 2004 (4 years old), which is practically *4 versions of Ubuntu* ago. Perhaps the software has changed and there is a better way to "automount" to a networked drive? (Anyone has a suggestion, please let me know).

---

### Post by mgazb on 2008-07-01
We have found this problem here. We use autofs to mount user directories and common storage facilities.

The directories work fine with the older 7.04 computers, but get wrong fs type with 8.04.

The same is true if I mount the directories by hand.

> mount -t nfs sun:/export/vol /vol
mount: wrong fs type ...

dan

---

### Post by klossner on 2008-09-03
I had a similar problem: I could manually mount NFS directories, but autofs couldn't do it for me.

I found a Debian bug report that autofs is passing the grpid option to mount and the newer kernels won't accept that.  If this is your problem, you'll find the message "NFS: unknown mount option: grpid" in /var/log/syslog.

Here's how I worked around this.  I renamed /sbin/mount.nfs to /sbin/mount.nfs.elf and made /sbin/mount.nfs be this Python script:

```

#!/usr/bin/python

# mount.nfs: a wrapper for the real /sbin/mount.nfs
# In Ubuntu 8.04, autofs insists on passing the grpid option to mount.nfs,
# but NFS rejects that and the mount fails.  This wrapper strips out that
# option and invokes the real /sbin/mount.nfs, which is renamed to
# /sbin/mount.nfs.elf

import os
import sys

# Look for and delete ',grpid'.
argv = [ word.replace(',grpid', '') for word in sys.argv[:] ]

cmd = '/sbin/mount.nfs.elf'
argv[0] = cmd
os.execv(cmd, argv)

```

Then I made the script be executable, and the problem was solved.

---

