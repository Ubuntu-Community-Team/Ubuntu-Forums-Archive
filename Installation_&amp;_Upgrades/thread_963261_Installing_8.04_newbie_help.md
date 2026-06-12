---
title: "Installing 8.04 newbie help"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by pjfan84 on 2008-10-30
Hi all,

I want to install 8.04 release, however.

I currently have windows xp installed on primary parition and have a data partition, picture below:

[[IMG]http://img207.imageshack.us/img207/8951/drivedetailsle3.th.jpg[/IMG]](http://img207.imageshack.us/my.php?image=drivedetailsle3.jpg)[[IMG]http://img207.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php) 

Can someone please instruct me if possible on how to install without destroying the data partition and leaving it intact in order to mount it when I install.

Any help greatly appreciated.

Thankyou.

---

### Post by meindian523 on 2008-10-30
Do you want Windows XP as a dual boot or only Ubuntu on your computer?

---

### Post by pjfan84 on 2008-10-30
Aplologies should of been more clearer.

I want to remove/over-write xp.  Thanks.

---

### Post by meindian523 on 2008-10-30
Then it's easy.In Disk Management(where you got that screenshot from),delete C: and reboot with the Ubuntu CD in the drive.At the partitioning step(step 5,If I remember correctly),select Use Largest Continuous free space.Make sure it selects the 178 GB you just freed up.Then sit back and let the installer run it's course.

Caution:
1]Back up your data when modifying your partitions.You don't want a wrong mouse click to delete your data.
2]Your My Documents,My Pictures etc reside on C: in C:\Documents and Settings\username\ on Windows XP.Back them up too if you want them.
3]Remember,nothing on your HDD is touched till you select Ok on the final screen,so you can abort the installation at the last step if you are not sure.

---

### Post by pjfan84 on 2008-10-30
Hi,

Thanks for that reply, emergency so only just got the reply.

In disk management in xp it won't let me "delete" the c: partition as u mention etc.  

Can you please advise.

---

### Post by meindian523 on 2008-10-31
Hmm.Reboot into the CD.For this,you will have to adjust the boot order in the BIOS so that CD is on top.
Once booted(Try Ubuntu without any change to your computer),you will find Partition Editor in System>>Administration.You can delete C: from there.Make sure you save all your My Docs,etc as mentioned above.Then follow the steps as mentioned.

---

