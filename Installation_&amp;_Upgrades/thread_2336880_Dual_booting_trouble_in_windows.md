---
title: "Dual booting trouble in windows"
date: 2016-09-12
forum: Installation &amp; Upgrades
---

### Post by khansubhan95 on 2016-09-12
I have a Lenovo laptop (640 GB HDD and 4 GB RAM) on which I am attempting to dual boot with Ubuntu 14.04.4 LTS.The hard disk sections on windows(under disk management) look like this in order.

Capacity           Filesystem 

200 MB               NTFS                       Healthy(System,Active,Primary) 
2.48 GB                                                       Unallocated
389.75 GB       NTFS            C:
203.75 GB                                                Unallocated

However during installation ,"Install alongside windows 7" does not appear.Moreover clicking on "Something Else" option gives the following

device                type               size       
/dev/sda                   
/dev/sda1      ntfs                  209 MB
free space                                    2.7 GB
/dev/sda2       ntfs                  418 GB
free space                                    218.8 GB

My questions is why is the above said option not appearing ?Or is this not a problem and can we proceed using the "Something Else" option?Also is the problem caused by the hard disk sections?

---

### Post by oldfred on 2016-09-13
Something wrong with sizes. 209+418+218 > 640 

Post these from terminal in live installer's live mode:
sudo parted -l
sudo fdisk -lu

---

### Post by Bucky Ball on 2016-09-13
What you're seeing in Ubuntu in Gparted or the 'Something Else' installer is a direct, and more accurate, reflection of what you are seeing in Windows.

After sorting out whatever oldfred is asking about, you can and should proceed with Something Else rather than the 'Alongside' option. Safer. Presuming you are intending to install to the 218Gb free space?

---

### Post by khansubhan95 on 2016-09-13
The sizes are 
209.7 MB (0.204 GB)+2.7 GB+418.5+218.8=640 GB(approx)

After running sudo parted -l

```
Model: ATA TOSHIBA MK6465GS (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  211MB  210MB  primary  ntfs         boot
 2      2871MB  421GB  418GB  primary  ntfs
```

```
sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x446588b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2         5606680   822977819   408685570    7  HPFS/NTFS/exFAT
```

@Bucky Ball while I know that proceeding with the "Something Else" option will be safer when compared to "alongside",the "alongside" option doesn't even appear

---

### Post by Bucky Ball on 2016-09-13
> **khansubhan95 said:**
> @Bucky Ball while I know that proceeding with the "Something Else" option will be safer when compared to "alongside",the "alongside" option doesn't even appear

Probably a good thing. Please use code tags for your terminal output. Thanks (see link in my signature for how).

PS: You have two partitions:

```
Number  Start   End    Size   Type     File system  Flags
 1      1049kB  211MB  210MB  primary  ntfs         boot
 2      2871MB  421GB  418GB  primary  ntfs
```

The first one is a boot partition by the looks and the second would be Windows. You have no free space to install Ubuntu. You have two NTFS partitions.

---

### Post by khansubhan95 on 2016-09-13
Running the Windows disc management gives the following
[URL="http://<br /> https://drive.google.com/file/d/0B621iZr0p0N_a3U2eE5vV1NiWHVhZmZYYlpXSkpOd2VnaXV3/view?usp=sharing<br />"]
[/URL][https://drive.google.com/file/d/0B621iZr0p0N_a3U2eE5vV1NiWHVhZmZYYlpXSkpOd2VnaXV3/view?usp=sharing](https://drive.google.com/file/d/0B621iZr0p0N_a3U2eE5vV1NiWHVhZmZYYlpXSkpOd2VnaXV3/view?usp=sharing)

And Gparted gives the following

[URL="https://drive.google.com/file/d/0B621iZr0p0N_Qzd6VVVGUndaQkk/view?usp=sharing"]https://drive.google.com/file/d/0B621iZr0p0N_Qzd6VVVGUndaQkk/view?usp=sharing
[/URL]

---

### Post by Bucky Ball on 2016-09-13
And the problem is? Yes, you have 203Gb of unallocated space to install Ubuntu. Your terminal output will only show partitions.

The empty space is shown in the Windows Disk Management, just not listed (it is in the blocks at the end of that screenshot). That is reflected in the Gparted output.

What you had in your first post:

```
device type size
/dev/sda
/dev/sda1 ntfs 209 MB
free space 2.7 GB
/dev/sda2 ntfs 418 GB
free space 218.8 GB
```

... is correct. Use Something Else, install in the 218Gb of free space. You will need a / partition and a /swap partition. The /swap need only be 2Gb. You can also include a /home partition for personal data, but you may have that already on the Win partition.

I'd have a bit of a think about how you're going to go about this before proceeding. If a legacy Windows install, then you are limited to four partitions and will need to create an extended partition and put Ubuntu on logical partitions inside that. And as mentioned, check how Windows is installed, in legacy or UEFI. Ubuntu needs to be installed in the same mode.

---

### Post by oldfred on 2016-09-13
Missed mixed MB & GB, sorry.

Looks like a typical BIOS/MBR install. Windows only boots in BIOS mode from MBR(msdos) partitioned drive.

If Windows is hibernated, and if Windows 8 or newer it always is hibernated with the fast start setting, the Linux NTFS driver will not see the NTFS.  If that is the case that will explain why you do not get the along side option. It also happens if you just have resized the NTFS and not rebooted into Windows so it can run chkdsk.

---

### Post by khansubhan95 on 2016-09-13
Looks like you were right about chkdsk .I ran it and got the following

```

The type of the file system is NTFS.


WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.


CHKDSK is verifying files (stage 1 of 3)...
 1 percent complete. (101889 of 748544 file records processed)
Attribute record (128, "") from file record segment 113614
is corrupt.
  748544 file records processed.
File verification completed.
  817 large file records processed.


Errors found.  CHKDSK cannot continue in read-only mode.

```

After some digging around in Google I found that 2 options can be used /f and /r,and which one should I use?Can running it cause any damage?

---

### Post by oldfred on 2016-09-13
Really question for Windows forum.

My old XP needed chkdsk once upon a time. I did use a Windows 7 repair flash drive and it ran a better chkdsk than the XP version.
If you have major damage it may move files or bits of files (that are already damaged).
This is why good backups are vital regardless of system used.

       Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

---

### Post by khansubhan95 on 2016-09-15
After running chkdsk and fixing the errors the "install alongside" did not appear.So I decided to go with the "something else" option.So I successfully installed Ubuntu .However whenever I start my computer ,the GRUB screen ,showing the choice of the option does not appear.Could it be that the Windows 7 OS was wiped out?Also if it is of any value,a drive appears in Ubuntu showing all the files of my C: drive of Windows 7

---

### Post by khansubhan95 on 2016-09-15
So I have solved this problem.Upon searching a post in a forum suggested to run 

```

sudo upgrade-grub

```

And soon as the update was complete ,GRUB recognized Windows 7 and now I am able to dual boot between Ubuntu and Windows 7.I will now mark this thread as solved.

---

### Post by Bucky Ball on 2016-09-15
Well done and thanks for marking the thread as solved to help others. 

Happy travels. :)

---

