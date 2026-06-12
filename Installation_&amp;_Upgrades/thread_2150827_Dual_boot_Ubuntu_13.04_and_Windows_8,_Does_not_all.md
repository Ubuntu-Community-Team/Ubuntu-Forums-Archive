---
title: "Dual boot Ubuntu 13.04 and Windows 8, Does not allow to access Windows 8"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by Anvin on 2013-06-02
Hello,

I have an 80GB hard disk and three partition in it. I was using Windows 7 and Windows 8 on it through dual boot. Windows 8 was on the C drive. Windows 7 on the D drive and E drive was empty. 

I installed Ubuntu 13.04 according to the steps shown in this video. [http://www.youtube.com/watch?v=MWYjZ2j7HrE](http://www.youtube.com/watch?v=MWYjZ2j7HrE)

Now, I can see the grub menu where it shows list of OS to boot. It shows Ubuntu and Windows 8. Ubuntu works fine but when I try to boot Windows 8, It shows Automatically Repairing and then Diagnosing but cannot go to the Start screen. It does show me Advanced options but one of the options I tried and it shows Windows drive is locked. It allows me to switch to Windows 7.

When I check Windows 7. I can see the Windows 7 drive as C:drive which is of 18GB  and Ubuntu on D Drive which is of 27.9 GB and the other drive is missing. When I check disk management. It shows the 27GB drive but does not show any file system. How can I retrive it. I used to use only Windows 8. All my works are on it. Please guys help me.

Thanks,
Anvin

---

### Post by Mark Phelps on 2013-06-02
Only MS Windows uses drive letters; Linux does not.  The ONLY way you can install a Linux distro to a Windows filesystem partition is using Wubi -- which requires installing from INSIDE Windows.  

You said that Win8 used "D:" but then later, you said Ubuntu uses "D:".  If both are true, then Ubuntu is in a virtual filesystem on the Win 8 partition.

To confirm (or deny) that, since it looks like you can boot into Win7, take at look at the Win8 partition and see if there is a "root.disk" file there. If there is, you installed using Wubi.

If you can boot into Win7 but can't access the "D:" drive, AND if it still has an NTFS filesystem on it, you should use CHKDSK in Win7 to attempt to repair the filesystem.  You can do that from Computer -- by right-clicking the "D" volume and selecting the option to check and fix the filesystem.

---

### Post by Anvin on 2013-06-03
Mark, thank you for your reply.

I had download ISO file of 13.04 Ubuntu and made a bootable USB. Then I did according to the video link here.... [COLOR=#333333][FONT=Ubuntu] [/FONT][/COLOR][http://www.youtube.com/watch?v=MWYjZ2j7HrE](http://www.youtube.com/watch?v=MWYjZ2j7HrE)

I did not use Wubi for sure. Sorry for confusion. At the time of installation.. on my C drive Windows 8 was present and on my D drive Windows 7 and E drive was empty. Since it was empty I thought of installing Ubuntu on E drive and I did according to that video.

When I boot, I can see the grub list menu, where it shows Ubuntu and Windows 8 loader in the list. When I select Windows 8, it shows automatic repairing and diagnosing your PC and then it leads me to other troubleshooting options like System Restore, System Image, and so on. None of them works. There is one Reset your PC option. When I choose it, it shows 'The drive where Windows is installed is locked.."

When I access Windows 7, it only shows C drive which belongs to Windows 7 and D drive which contains Ubuntu. Have a look at the Windows 7 disk management attachment
If you see the disk management, the drive which contains Windows 8 is being shown as 100% free but I am sure it still contains all my files.

Since the drive which contains Windows 8 is not showing in Windows 7's my computer, I can't perform chkdsk.











> **Mark Phelps said:**
> Only MS Windows uses drive letters; Linux does not.  The ONLY way you can install a Linux distro to a Windows filesystem partition is using Wubi -- which requires installing from INSIDE Windows.  

You said that Win8 used "D:" but then later, you said Ubuntu uses "D:".  If both are true, then Ubuntu is in a virtual filesystem on the Win 8 partition.

To confirm (or deny) that, since it looks like you can boot into Win7, take at look at the Win8 partition and see if there is a "root.disk" file there. If there is, you installed using Wubi.

If you can boot into Win7 but can't access the "D:" drive, AND if it still has an NTFS filesystem on it, you should use CHKDSK in Win7 to attempt to repair the filesystem.  You can do that from Computer -- by right-clicking the "D" volume and selecting the option to check and fix the filesystem.

---

### Post by fantab on 2013-06-04
If you can boot Ubuntu (if not, then use Ubuntu DVD/USB) then open Terminal [ctrl+alt+T], run the following command and Post its output:

```
sudo fdisk -l
``` 
and
```
sudo parted -l
```

---

### Post by Mark Phelps on 2013-06-04
Need to get some terms straight to prevent confusions ...

What MS insists on calling "drives" are actually "partitions" -- formatted  chunks of space on an actual disk drive.

You can NOT install Ubuntu from USB or CD/DVD to an NTFS partition.  That is an MS Windows filesystem and Ubuntu MUST be installed to a Linux filesystem. 

The Disk Management screenshot shows only two NTFS partitions -- the 953MB and 27GB partitions are not NTFS.  So, my guess is that the 27GB partition actually contains Ubuntu.  There's also 74GB partition at the beginning of the drive -- that could have been where Win8 was installed.

If you already had Win7 on your PC and then installed Win8 along side it, Win8 will update the boot loader files in the Win7 partition.  Thus, unfortunately, if the partition containing the Win7 boot loader files gets damaged, you won't be able to boot into Win8.

The commands requested by fantab will give us a Linux filesystem view of the partitions on your drive.

---

