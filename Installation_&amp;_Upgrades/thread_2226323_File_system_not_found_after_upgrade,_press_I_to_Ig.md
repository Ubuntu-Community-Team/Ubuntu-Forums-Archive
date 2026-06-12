---
title: "File system not found after upgrade, press I to Ignor, S to Skip, M for manual"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by Subdla on 2014-05-26
14-May-26  Monday

I upgraded to Ubuntu 14.04.  Everything looked fine until I rebooted.

I have a Windows 7 x64 computer.  I installed Ubuntu using WUBI and last fall upgraded to version 13.10.  After the upgrade to 14.04, I tried to boot to Ubuntu.  This resulted in errors.  After hours of attempts to fix the problem, I deleted Ubuntu from Windows, and reinstalled Ubuntu.  I created a Ubuntu disk.  I copied the WUBI file from the DVD to my hard drive.  I successfully installed version 14.04.  This resulted in the same boot problems.

When I boot, I get the message "Serious errors were found while checking the disk drive for /.  Press I to ignore, S to skip and M for manual recovery."  Pressing Skip, I get the error "Root filesystem check failed.  /tmp not ready or found."  After reinstalling Ubuntu, the boot allowed me to select recovery mode.  I believe a new GRUB has been installed.

From recovery mode, I ran System Information to see my disk drive names.  I ran FSCK to check for file system problems.  It said it would remount RW.  FSCK.ext4: operation not permitted while trying to open /dev/loop0.  You must hafve R/W access to the file system or be root mountable: FSCK/ [646] terminated with status 8.  Mountall: Unrecoverable FSCK error: Mountall.  Skipping mounting since Plymouth is not available.  I tried options FailsafeX, Enable Networks (it said Modemanager was S/D).  I tried CTRL-C.  Somehow, I ended up with the root@ubuntu prompt.  I tried FSK again, and it said everything was clean.  I tried "mount -o remount/rw /" and it said rootr.disk was write protected.

Thee seems to be a problem with the latest upgrade.  Perhaps it does not like to see UBUNTU intalled as a file in Windows.  I could try to partition the disk and install UBUNTU there.  Any other ideas?  I found the WUBI installation in the past to be the best option and error free.

---

### Post by ben-schweitzer on 2014-05-26
Wubi is not supported anymore. You should partition the disk and do a full install to that partition.

---

### Post by philinux on 2014-05-26
Wubi was only ever meant as a short term way to trial Ubuntu without having to partition a hard drive.

---

### Post by bcbc on 2014-05-26
Change your boot entry from "ro" to "rw" (hold down Shift when booting, press E to edit, Ctrl+x to boot).

[http://ubuntuforums.org/showthread.php?t=2217829](http://ubuntuforums.org/showthread.php?t=2217829)

---

### Post by Subdla on 2014-05-26
Thanks for the help.  Changing the boot entry to "rw" has worked!  In future I will consider partitioning the disk and installing Ubuntu that way.
How do I close this thread?

---

### Post by deadflowr on 2014-05-26
> **Subdla said:**
> 
How do I close this thread?

You don't, but you can mark it as solved.
Go to the top above the first post, to Threads Tools.
Click on it and select "mark this thread as solved".

---

### Post by bcbc on 2014-05-26
Look under thread tools

---

### Post by Subdla on 2014-05-27
Now I know how to use thread tools.  Thanks.  However, perhaps you can tell me how to permanently change the grub boot entry from ro to rw.  I tried boot-repair, but that did not seem to do anything.  Perhaps boot-repair advanced options?  I have also heard about "grub-customize".  It seems that I have Grub 2 and most of the help is not for it.

---

### Post by bcbc on 2014-05-27
That link I posted... read post # 9. It has a 'permanent' fix. I recommend you read the entire thread.

---

### Post by Subdla on 2014-05-27
I read the thread.  That worked just fine.  Thank you very much.

---

