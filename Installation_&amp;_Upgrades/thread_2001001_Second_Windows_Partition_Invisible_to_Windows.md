---
title: "Second Windows Partition Invisible to Windows"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by llanitedave on 2012-06-10
I recently purchased a Toshiba Satellite laptop, and the first thing I did was to install Ubuntu 12.04 on to it.  Since I will use the laptop for both home and work, I decided to create a separate ntfs partition to hold most of my documents and shared files.  That way I should be able to access them from both the Windows and the Ubuntu sides.  The partitions hosting Ubuntu and Windows 7 are both fairly small, with the idea that those will hold mostly applications and files that are specific to those systems.

Problem is, although I can see and access the ntfs partition in Ubuntu, and it's correctly identified as ntfs, the partition doesn't show up on the Microsoft side.  When I run the Microsoft partitioning utility, it detects the partition, but doesn't recognize it as ntfs.

How do I get Windows to recognize a second partition in its own format?

---

### Post by sudodus on 2012-06-10
I guess you don't have many files on that data partition yet, so it is easy to back up those files (and directory structure).

Then I suggest that you let Windows format the ntfs partition. It is a native operation to Windows, so it is recommended to create (format) it with Windows.

Restore the files (and directory structure). Now it should be easily managed by Windows, and I am pretty sure that Ubuntu can read/write it too.

---

### Post by nowaibro1 on 2012-06-10
Have you checked drive management? You probably just have to assign it a drive letter.

---

### Post by roelforg on 2012-06-10
I always use the following fist-rule for creating filesystems:
A fs shall be created by the os it was made for. (e.g. fat* and ntfs by win and the others by linux).

---

### Post by flemur13013 on 2012-06-10
What sudodus said. You might be fix it with "chkdsk /F" on windows, or with "Partition Wizard" (from MiniTool).

---

### Post by llanitedave on 2012-06-10
The Windows Drive Management tool's menus wouldn't allow me to reformat or do anything else to the partition, only delete it.  But when I tried to do that it gave me an "unknown error".  So I booted into Ubuntu and deleted the partition from there, turning into free space.

Went back to Windows, and then I was able to format the partition as a "simple volume", made it ntfs and labled it drive E.  All seemed to be well.  It showed up on the system and I was able to save to it.

Then I did a restart, and everything fell apart.  Formatting that volume in Windows somehow hosed Grub!  Now I can't boot at all, except from my ubuntu installation usb device.

Is there a way to repair Grub from the installation volume?

---

### Post by darkod on 2012-06-10
Reinstalling bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But on the same note, you better post a screenshot of Gparted or similar, so we can have a look at your partitions. Deleting that partition and recreating it shouldn't have affected grub2 at all. You might have some weird setup.

You don't have grub2 installed on a partition, do you?

Or you didn't delete all partitions, including the ubuntu partitions, instead of only the ntfs partition?

And the most important question, are you running ubuntu or wubi inside windows? If we are talking about wubi then deleting ntfs partitions might affect it, otherwise if you have proper dual boot of ubuntu and windows, I really can't see a relation between grub2 and ntfs partitions. Note that the above link about reinstalling grub2 is NOT used for wubi, only for proper dual boot.

---

### Post by llanitedave on 2012-06-10
I didn't think I had a weird setup, and I sure didn't think Grub would be on that partition -- in fact, it couldn't have been, since i was able to reboot after deleting it, but before formatting it.

When things like this happen, I usually end up just blaming Bill Gates personally.

Anyway, I found the instructions for downloading and using Boot-Repair, and I used it in the recommended mode from the installation stick.  It locked up my screen at the end, so I was afraid I'd messed up something else, but I shut the computer down and then rebooted.

Success!  I can see, save, and retrieve files from the ntfs partition using either system!  Looks like I'm ready to roll now.  Thanks, all!

---

### Post by sudodus on 2012-06-11
I'm sorry you had those problems but I'm glad it works now :KS

 If you feel that the problem is solved, please click on **Thread Tools** at the top of this page and mark the thread as SOLVED!

---

### Post by roelforg on 2012-06-11
> **llanitedave said:**
> I didn't think I had a weird setup, and I sure didn't think Grub would be on that partition -- in fact, it couldn't have been, since i was able to reboot after deleting it, but before formatting it.
 

 
Ever seen the partition layout of a standard windows (>= vista) install? Not pretty, let me tell you that.
 
You could reboot because gparted didn't touch anything but that partition, windows tends to muddle with some others as well (sometimes, as a sideeffect, erasing the mbr).

---

