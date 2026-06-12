---
title: "Root file system"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by sdpinokc on 2008-09-22
I am trying to install Ubuntu in an effort to save files from computer using Vista.  It tries to partition the drive 33% to Vista and 67 to Ubuntu.  This gives a message that the partition is too small.  When I go to manual to prepare partitions I get a message 'No root file system is defined.  Please correct this from the partitioning menu.'  

I am lost here.  Can anyone help.  I am not sure how or where to define the root file system.  

Do I need to install Unbuntu within windows? How do I change the partition %.Thanks sp

---

### Post by mikewhatever on 2008-09-22
If all you need is to copy some files from the Vista partition, there is absolutely no need to install Ubuntu. Simply run is from the CD, look for your partitions under Places and reboot when done. Given there isn't much space on the HDD, and that being your first time experience, I very strongly suggest the above solution.

If you insist on installing, one of the partitions you create (root filesystem) must be mounted as /. The other one should be mounted as swap. Perhaps following this guide would clarify things -> [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall).

---

### Post by sdpinokc on 2008-09-23
Thank you for your reply. I apologize for my ignorance of all of this technical info. Windows Vista froze up on me so I was using this to save my files. Fortunately I did have problems and could not install Ubuntu.  This morning I did try to boot from the disk and when trying to access my files got a message 'Cannot mount volume SQ00number'  $Log file indicates unclean shutdown (0.1) Failed to mount '/dev/sda2', Operation not supported.  Mount is denied because NTSF is marked to be in use.  Choose one action:  

The first choice is if you have windows.  The second is to use a 'force' option to type on the command line:  mount-t NTFS-3g/dev/sda2/media/sq004660vo8-0 force or add option to the relevant row in the /etc/fstab file:  /dev/sda2/media/sq004660vo8 ntsf-3g force00.  I do not know what this means and where is a command line to type it on.  

When I close this message, there is another message 'You are not supposed to show G-IO-error_failed_handled in the UI. I do not know what this means either nor do I know what to do about it. 

Your help is greatly appreciated.  Being a novice at this I am stumped.  Thanks again. sp

---

### Post by Idefix82 on 2008-09-23
This is what it means: NTFS is the file system windows uses. When a drive is used by an operating system (like windows) it is marked as used. Another operating system can't claim it for itself at the same time. Normally, when you shut down windows cleanly, it should indicate that it's done with the partition and some other system (like linux) can now use it. Unfortunately, your Vista crashed and didn't have time to free the partition cleanly.

What you can now try is to do as the message suggests: tell Linux "I don't care whether you think that the partition is being used or not, I want you to read it now". This you would do by opening the terminal and typing in the command suggested to you by the message, i.e. "mount..." You should be aware though that you are risking damaging the file system and thus losing the data for good. On the other hand, if there is no hope of reviving Windows, this might be your only option.

For the future: Linux is much more secure and more stable ;)

---

### Post by mikewhatever on 2008-09-23
Use [PhotoRec]("http://en.wikipedia.org/wiki/PhotoRec") to recover your files, instead of Ubuntu desktop CD.

---

### Post by sdpinokc on 2008-09-23
I have copied PhotoRec to a CD.  Can access that drive but cannot get the .exe file to do anything.  Using run doesn't seem to work.  What now?  Thanks sp

---

