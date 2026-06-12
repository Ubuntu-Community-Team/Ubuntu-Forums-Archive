---
title: "Possible fstab bug - 'noauto' ignored"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2007-04-30
Any fstab entry with user,noato still automatically mounts!
eg with the line
/dev/hda5  /D  vfat  user,noauto  0  0
hda5 is still mounted automatically on /D at boot!

'noauto' works correctly in Dapper, but appears to be ignored in Feisty.
To stop automounting in Feisty I have to comment out the entry from fstab.

Should I file this as a bug?  Is so how?
Does anyone have any more information on this?

(I have been playing with this for a day,
and don't think I have klutzed anything :-)
(I tried the /dev/hdx entries in there instead of uuid just to compare with Dapper,
using uuid of course makes no difference).

---

### Post by undecidable on 2007-05-03
Am not trying to bump this as it is obviously a bug,
 but just want to and some further information that I hope may be helpful to those trying to fix the issue.
If there is a bug repository to which I ought to be filing this just let me know (I am new to Lx)

1.  If the entry in fstab is user,auto & partition is vfat
.	the partition is mounted
.	it is mounted to the correct mount point
.	owner is root
.	only root can write to it  (bad)
.	only root can umount it.
.	the user can only write to it if root umoutns it first then the user manually mounts it.
.	the partition disappears from the Disk Mounter Panel and Places (good)
* For ext3 the same except the user can write to it.  

2.  If the entry in fstab is  user,noauto
.	the partition is mounted anyway  (bad)
.	it is mounted to the correct mount point
.	owner is root 
.	user can write to it.
.	only root can umount it.
.	the user can mount it if root umounts it first.
.	the partition appears in the Disk Mounter Panel and Places (good)
	and on the desktop (a pain)
* Applies to vfat & ext3.

3.  If the entry in fstab is noauto,user,uid=1000,gid=1000,umsk=000
	(for vfat obviously)
.	the partition is mounted anyway  (bad)
.	it is mounted to the correct mount point
.	owner is the user (1000) and he can write to it.
.	only root could umount it  (bad)
.	user could mount only after root umounted
*For ext3 not necessary to do this - cf 1. above.

4.  I think this is related to the issue that 
if there is no entry in fstab, the partition still appears in Place and Disk Mounter.
(cf [http://ubuntuforums.org/showthread.php?p=2587905#post2587905](http://ubuntuforums.org/showthread.php?p=2587905#post2587905)
& [http://ubuntuforums.org/showthread.php?t=428196](http://ubuntuforums.org/showthread.php?t=428196))

I hope this is useful.

---

### Post by BrownCoal on 2007-09-30
There is a >[bug report]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/120829")< for this issue. I've added this threads url to it for reference.

---

### Post by BrownCoal on 2007-10-07
** This is a repost of my solution originally made at the [_launchpad bug report_]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/120829"). **

Well, I have finally found the problem... It very simply involves the single setting [system>preferences>removable drives and media>storage>mount removable media when inserted]. Deselecting this makes noauto work as usual. I also managed to remove the desktop drive icons; open terminal and type "gconf-editor" and deselect [/apps/nautilus/desktop/volumes_visible].

The question now is why the developer/s decided that a gnome preference (and a non-passworded one at that!) should override fstab... If this has indeed been corrected in Gutsy as Ingo suggested, then hopefully it means that the devs have reverted to the regular approach of giving fstab full command of mounting drives.

---

### Post by undecidable on 2007-10-07
Thanks.  Only problem with that is that I assume Feisty won't then mount my usb drive then when inserted.

---

### Post by BrownCoal on 2007-10-11
Pleasingly, disabling the option [system>preferences>removable drives and media>storage>mount removable media when inserted] still allows usb devices to be mounted automatically :D

---

### Post by undecidable on 2007-10-12
Thanks.

Well, Ubuntu just seems to be full of good turns.

---

