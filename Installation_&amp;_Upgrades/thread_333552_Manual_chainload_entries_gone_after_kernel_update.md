---
title: "Manual chainload entries gone after kernel update"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2007-01-07
I took my Linux PC on a road trip to find some broadband.  Updated Dapper.  It installed a new kernel and deleted all the manual chainloader entries I'd set up in grub/menu.lst just last night.  Dapper is my primary Linux install, on the 1st HDD.  It has an edited menu.lst that directs GRUB to the 3 Linux distros on the 2nd HDD. 

I know this has been covered before, but could someone please verify the fix for me?  I think it has something to do with moving those chainload entries below the "End Debian Automagic" divider or something like that. 

It wasn't a big deal to just re-enter the original chainload directions again.  PCLOS and Mint start up just fine now.  Edgy does not.  With Edgy I get a weird fsck error message (apparently has something to do with what appears to be md5 files on some of the data partitions) and Edgy gives me the opportunity to manually edit the files.  As if.  I'll just try re-installing Edgy and see if the problem goes away.

---

### Post by Bartender on 2007-01-08
I re-installed Edgy.  Got a "no root file system" error until deleting the original Edgy partition, then Edgy re-installed without complaint.

Here's Edgy's fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=62a5b3af-8771-413b-92f0-fd503f0f7371 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=8AEC111FEC1106DB /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=d69bd357-5e20-4e4f-b91a-8061d67967fd /media/hda3     ext3    defaults        0       2
# /dev/hda6
UUID=4593-A5BB  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=efbe450e-f399-4402-826a-cf64fbf7958f /media/hdb2     ext3    defaults        0       2
# /dev/hdb3
UUID=384d2978-c370-4060-bbb5-961ed7d82d5b /media/hdb3     ext3    defaults        0       2
# /dev/hdb5
UUID=4d7e517b-10ea-4d78-a9fc-73384226f92d /media/hdb5     ext3    defaults        0       2
# /dev/hdb6
UUID=45A0-738F  /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=8e654f48-9ebd-4568-a614-95503a4bdaf7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

What's the function of the "UUID" entries?  I think it's some sort of error check? :-k 

Saw a post where someone said to just remove the "UUID=xxxxxxxxxx" part.  Is that kosher?  Would that help to prevent fsck errors when doing kernel updates to other partitions that Edgy mounts?  

Or should I unmount some of the other partitions?  There's nothing to be gained by having one distro mount the other distro's / partitions, is there?

Multi-booting is fairly easy to set up, but it's beginning to appear that once the deed is done complications arise that are beyond my limited abilities...

---

### Post by Bartender on 2007-01-08
Well, now I'm talking to myself and that's not good.

Just tried to boot Mint, one of the 3 distro's on the second HDD.  Got the same weird error

"File system check failed"

It looks like it was checking the mounted partitions, then it just says 

"fsck died with exit status 8"

I'm left with a maintenance shell.  One of the lines says "You will be called upon to help a friend in trouble".  Sounds like one of those black 8-ball fortune-telling thingies we useta play with years ago.

I make a change to one distro and that crashes the other distro.  After reading dozens of posts about multi-boots, I thought the hardest part was setting it up, not keeping it running.

EDIT:  Found some posts about exit status 8 and the new UUID stuff.  Looks like I can just remove the UUID coding.  Wish I knew how from the maintenance shell CLI but don't so will reinstall Mint again then delete UUID's.

---

### Post by confused57 on 2007-01-08
Herman explains it pretty well:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

I had the same problem with Edgy, everytime I installed a different OS on a partition that was automatically mounted by Edgy, I'd get the error message...I just put a # in front of the partitions I didn't want mounted in Edgy...first I determined what the new UUID number was, entered that(in case I wanted it mounted again), then put the # in front of...as you said, probably easier just to remove the UUID's.

---

### Post by Bartender on 2007-01-16
Thanks -
I relied on hermanzone for my first Ubuntu install.  Haven't been back much since. Herman's been busy!

---

