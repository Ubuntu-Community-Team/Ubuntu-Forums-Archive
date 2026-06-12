---
title: "Unable to boot into ubuntu 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by t_anvesh on 2009-11-15
I'm unable to boot into ubuntu 9.10.
It's fresh install on ext4 partition.

The problem while booting is that it gives an error message saying 

*"Mounting /sys /**root/*[I]sys failed"

 [/I]and root shell is shown... even rescue mode also does the same.....

What I found out is the file system is mounted as ReadOnly making it impossible to create /sys?

I did fsck on the partition from LiveCD and the contents of fstab file are
[I]
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=98f53a4e-c595-4d9b-affe-9111143659ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=23c20c6f-b1f2-4864-a0d9-ae1cb14f7093 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/I][I]

plz help.......

thanks in advance.......
[/I]

---

### Post by t_anvesh on 2009-11-15
Should I reinstall  again???

Plz provide a slution that does not require a reinstall......

---

### Post by dandnsmith on 2009-11-15
That looks like errors may be present at boot - was anything shown up on the fsck?
and did you get the fsck to fix the errors?
and then do another fsck, just to check?

---

### Post by t_anvesh on 2009-11-15
FSCK displayed that it fixed an error when I ran it for the first time........

subseqent runs of the command didn't display any errors.........

---

### Post by t_anvesh on 2009-11-15
I try to search on google but in vain.......

any idea..how to make it bootable again???

---

### Post by dandnsmith on 2009-11-16
Now I don't know what to suggest.
Technically it is bootable, but it just isn't runnable - so googling for things regarding booting won't help.
There seems to be some check which is failing - but I haven't experienced this, and haven't an installation of 9.10 to hand to check it out. Booting it without the 'quiet' option might show a relevant message (I'd make it nosplash as well).

---

