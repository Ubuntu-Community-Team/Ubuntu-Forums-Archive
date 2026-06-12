---
title: "Put /home on a separate drive or relocate the Docs, Pictures etc files?"
date: 2018-06-11
forum: Installation &amp; Upgrades
---

### Post by bobsone on 2018-06-11
Hi
 I am experimenting with installing 18.04 and am currently exploring options for the repositioning-placement of the home folder or moving the data folders (Documents, Pictures etc) to another drive.

 From what I have read there is a general opinion that any reinstall-upgrade is easier when the home folder is on a separate drive because it can be left in place and reconnected to the new system.
 I have also seen some comments indicating that locating the data folders on another drive-partition outside the home folder makes backups easier.
 
 
 I have successfully installed 18.04 (both bios and uefi) with /home on a different drive but how to create new data files on a different drive, have them linked to the ones in the home folder and have them auto-mount at boot?
 
 
 I would be interested if anyone has any views-cautions, links etc about placing the home folder on a separate drive vs moving the data files vs leaving everything alone :-).

Thanks

---

### Post by yancek on 2018-06-11
When you say "drive" do you mean an actual separate hard drive or do you simply mean another partition on the same drive?  Usually, a separate home partition will be used on the same drive as the filesystem and then an upgrade can be done and the personal files can be maintained.  Generally accessing data on a separate physical drive requires changing ownership and/or permissions.  I've never done a home partition on a separate physical drive so I'm not sure what would be expected in that case.  Auto-mount at boot requires an entry in the /etc/fsab file.  If you have done an install with a separate /home partition, I would expect this to be done during the install.

---

### Post by bobsone on 2018-06-12
Thanks for the reply.
I want to move the data to a new/separate drive.  I have the OS on a relatively small SSD and would like to have the user data (Music, Pictures etc) on a separate HDD.

I am still experimenting, I have successfully installed the OS with the home folder on the same install SSD and I have also successfully installed with the home folder on a separate HDD.  I was wondering if it is better to install with the whole home folder on a separate drive or install /home on the SSD and link the user data (Music, Pictures etc) to the HDD?

Also, r.e.   *"...an entry in the /etc/fsab file*."    am I correct in my thinking (guess) I would use this; [B]sudo pluma /etc/fsab
[/B]
But then what, from what I have read, I will need to add the UUID# of the new storage area and then... still searching for answers to this...

Thanks.

---

### Post by yancek on 2018-06-12
Simpler to have the /home partition on the same drive.  If you have a lot of data such as Pictures, Movies, Music you could also create a separate partition on the secondary drive and store those on that drive.  You should be able to find countless tutorials on creating an fstab entry for an external drive partition, both on these forums and online.

---

