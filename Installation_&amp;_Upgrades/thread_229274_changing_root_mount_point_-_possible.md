---
title: "changing root mount point - possible?"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by cmtorres on 2006-08-04
Let me start by saying that I am a bonehead... and I know only enough to be dangerous:mad: .  I thought I was going to be slick when I installed Dapper and set up a boot drive (hda1) and a data drive (hdb1).  However, I got my a's and b's backwards and now my fstab looks like this:

 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

when what I really wanted was "/" to be the mount point for hda1.  I wanted to kep hdb2 dedicated to handling the video files I'll be working with to minimize the amount of reads/writes.

Is is possible to just modify fstab, changing hda1 to hdb1 and vice versa, then copy all folders and files from hdb1 to hda1?  Right now, I'm thinking the only thing to do is to wipe everything and reinstall (and get it right this time).  I really don't want ot do this since I've spent a fair amount of time tweaking thinks to my liking and would have to have to do it all over again (though I would if I had to).

Any help would be greatly appreciated.

Regards,
Craig

---

### Post by eXisor on 2006-08-04
Just modifying fstab is not going to do it. There are ways of moving partition data from one to the other, but I'm not too sure these will work for root. Take at look at [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

I suggest you start over if you can't live with it. There is no inherent problem with have root on dhb1.

---

### Post by cmtorres on 2006-08-04
TRhanks for the quick reply.  I guess I'm just going to have to start over.  I'm a bit of an "order" freak, and it would just drive mem nuts everytime I looked at it, knowing that it's not the way I wanted it.

-Craig

---

### Post by eXisor on 2006-08-04
I'm a bit like that myself. :)

---

