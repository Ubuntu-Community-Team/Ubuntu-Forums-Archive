---
title: "Moving Ubuntu install"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by crokett on 2006-10-05
I have 4 HDDs in my system, sda, sdb, sdc and sdc.  Ubuntu iscurrently installed on sdc1.  I would like it to be installed on sdb1.  What is the easiest way to move it? livecd->file copy and update grub?

---

### Post by doobit on 2006-10-05
> **crokett said:**
> I have 4 HDDs in my system, sda, sdb, sdc and sdc.  Ubuntu iscurrently installed on sdc1.  I would like it to be installed on sdb1.  What is the easiest way to move it? livecd->file copy and update grub?

Why not open the computer and switch the cables? Just make sure to also change the jumpers on the hard drive to make it a slave, if necessary.
Then update grub.

---

### Post by crokett on 2006-10-05
sdc is a 9GB scsi.  sdb is a 70GB scsi. debian is installed on sdb1.  was trying out both debian and ubuntu and will keep ubuntu.  would rather have it physically on sdb so sdc can be used as a dedicated disk at some point for video capture.

---

### Post by doobit on 2006-10-05
> **crokett said:**
> sdc is a 9GB scsi.  sdb is a 70GB scsi. debian is installed on sdb1.  was trying out both debian and ubuntu and will keep ubuntu.  would rather have it physically on sdb so sdc can be used as a dedicated disk at some point for video capture.

OK, that makes sense. I found a little info on disk cloning here:

[http://linuxgazette.net/issue89/ward.html](http://linuxgazette.net/issue89/ward.html)

I think the way you mentioned should work, but you could also boot the live CD and use Gparted to copy the disk.

Sorry, I should have noticed they were SCSI... I could have sworn your post said hda hdb hdc ...

---

