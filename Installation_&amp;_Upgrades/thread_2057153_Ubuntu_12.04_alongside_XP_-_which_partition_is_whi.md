---
title: "Ubuntu 12.04 alongside XP - which partition is which?"
date: 2012-09-13
forum: Installation &amp; Upgrades
---

### Post by wood_jl on 2012-09-13
I searched the forums, and I didn't see anybody with this issue.   It seems I'm in the minority dual-booting XP.

This is a very simple issue.   The installer (in dummy mode, for a dummy like me) has dumbed down excessively.  The last time around (10.04LTS) it was smart enough to at least label which side was which.

[IMG]http://i539.photobucket.com/albums/ff357/gbasp/DSC06909.jpg[/IMG]


I assume the left side is Windows, and right is Linux.   Resizing partitions isn't something I like to do based on simple assumption.

I understand that with newer versions of Windows, you must resize the partition from Windows, so you make the decision then and never see this.   Perhaps that's why I didn't see a million answers to this question when Google-ing for answers.

Any help much appreciated!

Thanks.

---

### Post by jerrrys on 2012-09-13
I don't recognize the pic you posted.  Things must of got changed around again.  Anyhow, try this instead:

Fire up you Ubuntu install disk (the live CD) and choose "try ubuntu without installing".  Then in the menu select Gparted (thats the partitioning software) and you should see windows listed as your NTFS partition.  From there shrink it to whatever size you want.  I would suggest something like 30 or 40 gig left over for the Ubuntu install.

Then install Ubuntu.  During the install process it will give you the option to install Ubuntu to the free space, and you can skip this partition process you are now trying.

[http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-resize-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-resize-partition)

And it is always a good idea to have backup in place when partitioning.  Never know when Murphy's law will kick in.

If you need further instruction, let me know.  Tis better to ask before then after :)

---

### Post by Mark Phelps on 2012-09-14
You're shrinking an existing partition to make room.  So, since XP is already on the drive, it's the one on the LEFT.  The space on the right will be the new unallocated space that will be used for Ubuntu.

---

