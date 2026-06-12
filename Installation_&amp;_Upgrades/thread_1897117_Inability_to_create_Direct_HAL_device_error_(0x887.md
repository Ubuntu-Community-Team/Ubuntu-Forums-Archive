---
title: "Inability to create Direct HAL device error (0x8876086) and ‘phantom’ Ubuntu bootup o"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by Phoenix Jewel on 2011-12-18
Please forgive the length of this – I want to give as clear a picture as possible, in order to resolve the issues and get started with Ubuntu.
  

I tried to install Ubuntu with Wubi and received the message [INDENT]                   An error occurred.
                  No such file or directory.
                  For more information, please see the log file.
                  C;\users\****\appdata\local\temp\wubi-11.10-rev245.log
[/INDENT]This said (a):[INDENT]   Ubuntu 11.10 installation error: Could not create DirectX HAL device (0x8876086)
[/INDENT]I then uninstalled the program, removed all remaining files and rebooted.
  
On reboot I saw an option to use Ubuntu, but proceeded as normal with Windows 7.
  I checked that there were no left over items, created a system restore point and tried again to reinstall with Wubi
  
Again, I received the same message.
  
I tried to use System Restore rather than uninstall Ubuntu and noticed that the Recovery folder now stated:[INDENT]                   There is not enough space to restore the disk.
[/INDENT]I then did a Disk Cleanup – as a (novice’s) way of trying to see if the System Restore Recovery folder would have free space! – and rebooted
  The following message appeared:[INDENT]   Windows Boot Manager
Windows failed to start. A recent hardware or software chance might be the cause. To fix the problem: 
1. Insert your windows installation disc and restart your computer.
2. Choose your language settings and click "Next."
3. Click "repair your computer."

 The boot selection failed because a required device is inaccessible. 
  \cUbuntu\winboot\wubildr-mdr
  0xc000000f
[/INDENT]Ubuntu now appeared twice.
  
I choose Windows 7 and then uninstalled Ubuntu again – (having decided to sort out the System Restore Recovery folder mystery later on).
  
On checking for remaining files I found that the file mentioned was still present on C drive.
  However, while looking for it, knowing I had 420Gb free space, I was alarmed to see the amount was now reduced to 402GB.
  Interesting, as the install for Wubi was allocated 18GB.
  
Following another reboot which offered Windows 7 and 2 Ubuntu options, I am left with the following questions:
  
What did I do wrong?
  What do I do about the Wubi installation error message (a)?
  How can I recover lost disk space?
  How do I remove the 2 Ubuntu options from bootup?
  If I chose to install by USB – could I use an 8GB one and still be able to add other documents, picture etc to it?
  
In replying, please remember that I am a novice.
   
  Thank you
   
Phoenix Jewel

---

### Post by bcbc on 2011-12-19
[Uninstalling Wubi]("https://wiki.ubuntu.com/WubiGuide#Uninstallation") will reclaim the space - normally you do this from the Control Panel and add/remove programs, select "Ubuntu". I'm not sure whether that will work after your restore attempts. But try it first.

After that you might have to manually uninstall (see the above link). The main size of a Wubi install is in the \ubuntu\disks folder and removing the \ubuntu directory will reclaim that.

In order to remove the two boot entries for Ubuntu you'll have to either use windows' command line tool bcdedit or use something like easyBCD to edit them. To use bcdedit, go to an administrative prompt, run:
bcdedit

This will show you all entries including the Ubuntu ones. They'll each have a GUID identifier that looks like {xxxx-xxxx-xxxx-xxxx}
Remove each with:
bcdedit /d {xxxx-xxxx-xxxx-xxxx}
(copy and paste the guid)

As to what caused the original problem, I can't say. I've never seen that particular message. It might help if you post your log file, or maybe [file a Wubi bug]("https://bugs.launchpad.net/wubi/+filebug") and post it there.

---

### Post by Phoenix Jewel on 2011-12-19
Hi 

Thank you for your reply bcbc.

I manually removed the remaining Wubi files and rebooting occurred as normal for Windows 7.

Great!

However:
1 -  There is still reduced disk space which I would like to know how to retrieve prior to trying to install Ubuntu again.

2 - A  search showed that the log about the Direct[SIZE=2]**X**[/SIZE] device has been deleted from the system, but  wubidr.mbr (MBR File 8KB) and wubidr (File 132KB) still remain.
Neither have File Name or File Path.


Thanks in advance for replies.

Phoenix Jewel

---

### Post by bcbc on 2011-12-19
Wubi will only place files in the *\ubuntu* directory, in the root of drives for *wubildr* and in C:\ for *wubildr.mbr*. Also a bunch of python stuff including the log file in the %temp% directory.

But the main space that's taken is all in \ubuntu. Once that's deleted you will see all the space recovered.

The only time that is not true is when there is some NTFS corruption and CHKDSK moves the files to a hidden \found.000 directory (or .001, .002 etc.). So, if you think there is space missing first run CHKDSK on the drive in question, and then check the \found.nnn on the same drive and delete whatever is in there (or you should actually check the files to make sure it's nothing you want to keep). But if there's an 18GB file in there called chk0000.chk, or a directory dir0000.chk and a root.disk inside that, then it's clear you can delete them.

Note, you can't see \found.nnn directories as they are hidden by default. Either change Explorer settings to display hidden and protected OS files/dirs, or use an administrator command prompt.

---

