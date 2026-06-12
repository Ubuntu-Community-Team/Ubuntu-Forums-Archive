---
title: "Edgy Changed fstab swap not mounting"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by CountChocula on 2006-11-04
I upgraded to edgy using the update manager and now my swap will not mount 
resulting in edgy to freeze after a minute of use. here  is the output from fstab(Below). Im not sure how to fix this. Would somebody be able to give me some help. Im pretty fresh to ubuntu so please try and keep it simple.




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=2fdc2c2d-a455-474b-a9fd-809623345dca / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb5 -- converted during upgrade to edgy
UUID=9a0e316a-12d0-4413-a6ad-6f0025141078 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


ps. I also noticed that there is another file in etc that says fstab.pre-uuid can I just revert back to that file. 

here is its output. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by dpm on 2006-11-04
Might this be related to this known bug?:

[https://launchpad.net/distros/ubuntu/+source/util-linux/+bug/66637](https://launchpad.net/distros/ubuntu/+source/util-linux/+bug/66637)

Cheers

---

### Post by CountChocula on 2006-11-04
I do think this is related but im pretty new and dont know how to fix from terminal commands only.

---

### Post by jlchannel on 2006-11-04
I had the same problem.

Probably you can check [here]("http://www.planetmy.com/blog/?p=227").

Good Luck!

---

### Post by cMadman on 2006-11-08
[I found this comment on Bug#66637 solved the issue for me.]("https://launchpad.net/distros/ubuntu/+bug/66637/comments/23")

---

