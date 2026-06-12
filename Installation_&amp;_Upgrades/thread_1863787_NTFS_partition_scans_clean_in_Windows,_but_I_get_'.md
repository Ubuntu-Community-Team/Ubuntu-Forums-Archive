---
title: "NTFS partition scans clean in Windows, but I get 'Serious errors were found' at boot"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by megamasha on 2011-10-18
I've found several similar threads, none with seemingly satisfactory outcomes :-/

I have a dual boot system (through grub)
I've upgraded to Kubuntu 11.10 from 11.04. Before the upgrade, Kubuntu booted fine.
Now I get 'Serious errors were found while checking the disk for /NTFSFTW' on booting Kubuntu.
The partition is NTFS, and it scans completely clean under windows, plus I doubt the upgrade touched it, as there are no system files on there, so it is likely COMPLETELY fine, but the system THINKS it's faulty and halts startup. Then I press 'I' for ignore, and continue using the system completely as normal (including the NTFS partition in question).

It happens EVERY Kubuntu boot, and scans clean under Windows every time.

This is an annoyance.
Has anyone got any suggestions for a workaround?
Has anyone reported this bug?
If not, does anyone know where it should be reported?

I would be most thankful for any help!

MM

---

### Post by Leaf on 2011-10-18
I am having this same problem too.
Both my NTFS partitions are getting the serious error dialog at startup.  No problems found with chkdsk in windows, or fsck.  SMART status is fine, no errors/bad blocks/bad sectors.

I'm using ubuntu 11.10 after upgrading from 11.04

---

### Post by keegandoig on 2011-10-25
Hi guys.

I struggled with the same problem when I upgraded to 11.10. After many an hour googling, I followed the advice in this post [https://answers.launchpad.net/ubuntu/+source/util-linux/+question/175474](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/175474) and have had no problems since with mounting my ntfs drive at boot up.

---

### Post by Mark Phelps on 2011-10-25
These very problems are the reasons why I've found it was a good idea to NOT mount NTFS partitions as part of the startup operations.  Any problems with them, and you can't boot anymore.

---

### Post by megamasha on 2011-11-01
Thanks [keegandoig]("http://ubuntuforums.org/member.php?u=1479640"), but I have ntfs-3g installed, and have tried reinstalling it.
I still have the same problem.

---

### Post by megamasha on 2011-11-01
Perhaps...
My system isn't unbootable though - I have the choice of ignoring the erroe, and the partition mounts perfectly normally.
And there doesn't actually seem to be anything krong with the partition! Windows (and if anything can tell me if there's a problem with the drive, it should be Windows) says there's nothing wrong with it, which leads me to assume that it's not the partition that's the problem, but rather some part of ubuntu 11.10 that THINKS there's something wrong with it. After all, it mounted fine before I upgraded from 11.04.

Can anyone shed any more light on this?

---

### Post by megamasha on 2011-11-25
BUMP!
Problem still exists.

I pressed ESC to see what was going on, and it seems the error happens because a call is being made to fsck.ntfs.
I get:

fsck.ntfs: not found.

Well, as far as I know, (I did a bit of googling), fsck can't do ntfs.
So what? Don't throw an error about it and halt boot!
There is nothing wrong with my ntfs disk - I've been using it from linux and windows for months, it scans clean.

This error is coming up NOT because there's an error on the disk, but because some automatic boot procedure is trying to execute a command that doesn't exist!
Surely something can be done about this?
Can anyone help?
Or do I need to report a bug somewhere?

MM

---

### Post by megamasha on 2011-11-25
Oh, by the way,
the ntfs-3g package didn't show up as installed in apper.
II have un- and re-installed the ntfs-3g package using apt-get, but in apper, it still doesn't show up as installed.
I got some output from atp-get suggesting it had been installed, so I don't know if this is just a problem with apper not showing it as installed (apt-get claims latest and greatest is already installed if I try to install it again)

---

### Post by mastablasta on 2011-11-25
it's the linux way of telling you to use LTS :-)
 
yeah definatelly report a bug on launch pad (if it's not there already).
 
Also i guess scanning could be turned off at boot. just i don't know how. but that might solve the issue.

---

### Post by megamasha on 2011-11-27
I didn't find any similar bugs on launchpad, so I've opened a new bug report here: [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/896944](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/896944)

---

### Post by megamasha on 2011-11-27
I have found a fix for this problem (but not for the cause, which *may* be to do with the upgrade from 11.04 to 11.10):

In your fstab file (/etc/fstab), there is a line that mounts the NTFS partition.

Mine looked something like this:

UUID=01CB45A7106719A6  /NTFSFTW            ntfs    defaults 0       1

To stop the error appearing, you can change the last number to 0.

To edit the fstab file, you need to open it with root permissions:

Press [Alt] + [F2]
then,
in Kubuntu type:
kdesudo kate /etc/fstab

in Ubuntu type:
gksudo gedit /etc/fstab

For other variants, I'm not sure.

MM

---

