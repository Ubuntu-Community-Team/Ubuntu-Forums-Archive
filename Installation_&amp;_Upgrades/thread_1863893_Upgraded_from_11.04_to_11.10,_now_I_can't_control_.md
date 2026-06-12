---
title: "Upgraded from 11.04 to 11.10, now I can't control my USB hard disks"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by nickyw on 2011-10-18
I upgraded, when invited to do so, from version 11.04 (that was a fresh install) to version 11.10 on my aging Dell OptiPlex GX270.

The upgrade took a long time but appeared to work smoothly.

However, I now find that I cannot write to folders on my external USB hard disks because the permissions have been changed, for some reason.  

In addition, some files, when I double-click on them, cause Banshee to be started, which is odd when a non-media file is selected!

My USB disks is my biggest headache.  I've subsequently booted Xubuntu from a live disk and that does not have issues with file permissions.  In Ubuntu, I get error messages like: "The permissions could not be changed. Sorry, could not change the permissions of "(name of) Drive": Error setting permissions: Read-only file system" on the NTFS partition where my name is the "Owner". On the other (ext3/4) partition, root is the "Owner" and I can't even get an error message.


What on earth is happening?  I'd be grateful for step-by-step instructions on how to fix this.  I have searched, alright, I Googled, but I can't find a simple explanation/solution.

---

### Post by Jmob on 2011-10-20
Seconding this problem.  I have a 500gb external drive with an NTFS file system.  Oneric (apparently, unless something else happened, it's been a bit since I've used it) has reduced me to read-only permission.   Can't seem to change access through Properties dialogue.  

I have w7 on this box as well, so I'd like to keep the FS, and I'm not sure about taking ownership/permissions in NTFS.  Can someone give some assistance?

---

### Post by jimbo99 on 2011-10-20
I hate to say this, but welcome to the party pal.

This release is especially poorly done.  And Canonical hasn't made efforts from what I can see to redress them yet.  One must wonder why they let such a poorly done piece of work get out their doors.

---

### Post by enigmaingr on 2011-10-20
I have also experienced this in 10.04. The problem started for me about four months ago. I'm guessing that it may have something to do with some update along the lines. 

As I haven't been able to find any solution, I'm in the process of doing a clean install to see what happens.

---

### Post by oldfred on 2011-10-21
How are you mounting partitions? Default has not been read/write for several versions as I remember. I had to add to fstab with permissions to make it work for me.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by ReginaldPerrin3 on 2012-02-21
I recently upgraded from 11.04 to 11.10. I have several  external hard drives, and now I cannot change anything on them: the  permissions have seemingly been altered to read-only.
  When I look at the "Properties" of each drive in Nautilus, it shows  me as the owner, yet I can only "Access files". When I try to change  this to Create and delete files, it shows an error message "Sorry, could  not change the permissions of "124E43F04E43CAE5": Error setting  permissions: Read-only file system".
  I have tried to alter file permissions by starting Nautilus with "gksudo nautilus", but it doesn't work. I have tried to change permissions for the whole drive using the chmod and/or chown command in terminal. Still no success.
  I am not a noob, but I am at a loss as to what to do next. Can anyone  help? My back-up destination is one of the external drives, and I  cannot back-up until this is fixed.
  Thanks in advance.

---

### Post by ReginaldPerrin3 on 2012-02-21
Ok, I seem to have fixed my problem of incorrect permissions.
I asked the same question here: [http://askubuntu.com/questions/106355/permissions-changed-on-upgrade-to-11-10-now-read-only](http://askubuntu.com/questions/106355/permissions-changed-on-upgrade-to-11-10-now-read-only) , and one of the answers was:

"If the external drives are formatted in NTFS, most of the time they  are, you will need to install ntfs-3g and ntfsprogs to access with write  permissions.  sudo apt-get install ntfs-config"

[FONT=Verdana]Now, my drives correctly allow me to create and delete files. Not sure what it has done, but my back-up now works, so I am happy.[/FONT]

---

