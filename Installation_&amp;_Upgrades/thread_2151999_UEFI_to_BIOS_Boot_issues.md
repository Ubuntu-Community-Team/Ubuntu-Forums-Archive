---
title: "UEFI to BIOS Boot issues"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by jimclake on 2013-06-05
I just purchased an Acer Aspire V3-771G-9441 with Windows 8 pre-loaded.  So started my lesson on UEFI booting and the latest MS requirements for PC makers!

I removed Windows 8 and loaded Windows 7 with little problem.

In the process, I switched from the UEFI boot back to legacy BIOS and disabled the secure boot.  I can find no option for the “fast boot” I’m reading about, though.  I also partitioned the bulk of the drive for Windows and left about 40-45 GB unused for my Ubuntu install.  When I check the partition layout in Windows Storage Management, it shows my almost 900 GB Windows partition and my 40 or 45 GB empty partition…just as I expected.

I then created a Ubuntu 13.04 install CD and booted into it.

However, when it shows me the partitions, it shows the entire 1 TB drive as empty! 

Rather than installing, I choose to let the CD boot into Ubuntu for me so I can take a look around.

I check folders and files and it shows me my Windows folders as well as the software I had already installed (Office 2013, for example).

So what am I missing that the CD can see my Windows files and folders, yet it cannot see the partitions correctly?

Thanks!
 
Jim

---

### Post by oldfred on 2013-06-06
Welcome to the Forums.

Moved to your own thread as Boot issues are almost always unique.

If you Installed Windows in BIOS on a previous UEFI system, it also converts from gpt partitioning to MBR(msdos) partitioning. But Windows only deleted the primary gpt partition table and not the backup gpt partition table. Then Linux gets confused as it sees both MBR & gpt and does not know what to do.
You can delete the backup gpt data with fixparts. Then gparted or the installer should correctly see your current Windows.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by jimclake on 2013-06-07
Thanks, oldfred! It seems I have a lot to learn about Linux and Ubuntu in particular!

Dumb question time: I am trying to run fixparts from a command prompt within Windows and trying all sorts of device names with no success.  I've tried 0:, 1:, sda, \dev\sda, C:...all sorts of combinations without success.

I've check Disk Management but all it gives me is C:.

Is there a way to find out how fixparts sees my single hard drive or for it to give me a choice of devices it sees?

Thanks again!

Jim

---

### Post by oldfred on 2013-06-07
I did not think fixparts runs in Windows. I only know the Linux version.

You should use the Ubuntu liveCD or flash drive live version or just about any Linux based repairCD. Then download fixparts.

---

### Post by jimclake on 2013-06-07
It does run in Windows...assuming you are signed on as Administrator! DUH!

I had just finished the Win 7 install and not activated my Administrator account yet...

Just loaded the Ubuntu install DVD and now it does recognize the existing Windows 7.

Many thanks...I'm sure I'll be back here often...this forum looks to be very active and full of information.

---

### Post by jimclake on 2013-06-07
It runs fine in Windows as long as you run it signed on as Administrator...

I had just finished the Win 7 install and hadn't gotten around yet to enabling the Admin account...as soon as I did that, fixparts worked fine!

And now I see the Ubuntu install CD also sees the Win 7 installation...thanks!

This forum looks pretty active and full of information...I'm sure I'll be back soon.

Thanks again!

---

### Post by oldfred on 2013-06-07
Glad it worked. :)

Did not know fixparts worked in Windows.

See my signature on Solved.

---

