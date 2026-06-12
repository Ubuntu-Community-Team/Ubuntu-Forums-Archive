---
title: "Error  message on install of 7.04 xfce from cd"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by mick99 on 2007-06-17
I hope you're all feeling fantastic

Using a live install cd of 7.04 xubuntu that I have confirmed has no defects:

When I select "guided - use entire disk" on the "prepare disk space" menu, and begin the installation process, the "installing system" window will get to the point of "*Creating ext3 file system for / in partition #1 of SCSI 1 (0,0,0) ...* then I will get an error message: "Failed to create a file system", "the ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

Bizarrely at this point; multiple "disk - file manager" windows will open and take a while to close (because the live cd is so slow)

Going back to the "Prepare disk space" step:
When I select either "Guided - resize SCSI1 (0,0,0), partition #1 (sda) and use freed space" and  then attempt to proceed to the next step, I get a message titled "go back to the menu and correct errors?" "the test of the file system with type ext3 in partition #1 of SCSI1 (0,0,0) (sda) found uncorrected errors. If you do not go back  to the partitioning menu and correct these errors, the partition will be used as is." a second error message titled "resize operation failure" arrears, saying "An error occurred while writing the changes to the storage devices.  the resize operation was aborted."

At the next step, "Prepare partitions", I try to continue but get an error message stating "No root file system is defined.  Please correct this from the partitioning menu" but nothing I have tried from editing partitions has  allowed me to go ahead.

When I select "Manual" from the "Prepare disk space" menu, I get the same "No root file system is defined" message, but not the two before that.

I have all my data backed up, so I just want this to work, please help me out!

---

### Post by mick99 on 2007-06-18
hmmm

I got this to work somehow, but if anyone knows what went wrong feel free to post.

---

