---
title: "Bizarre Ubuntu 13.04 amd64 USB install issues making it unusable"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by Metavore on 2013-04-27
I dual-boot Windows 7 and Ubuntu, and decided to upgrade 12.04 to 13.04 "Raring Ringtail". I had a 2GB USB stick but no DVD-R so I opted to use the USB installer provided at pendrivelinux.com as recommended by ubuntu.com after downloading the 13.04 amd64 ISO from the Ubuntu site. I decided to do the overwrite method built into the pendrive instead of upgrading my 12.04 since my 12.04 had some file issues that I didn't want to possibly inherit. I also didn't want to as a novice fiddle with the partitioning and whatnot, and with the pendrive installation I didn't have to.  
  
Anyway, the pendrive seemed to install Ringtail fine, but at the point after installation where it said I have to restart the computer, some weird stuff happened. For one, the boot order said Windows 7 and Ubuntu 12.04, NOT 13.04. When I tried to boot Ubuntu it had some ["missing modules" and "does not exist" warnings]("http://i.imgur.com/i9bZwLQ.jpg"), even though I checked the pendrive disc for errors and it said it was fine. Re-booting from the USB gave me the options ["Reinstall Ubuntu 13.04", or "Erase Ubuntu 13.04 and reinstall"]("http://i.imgur.com/nrxS9KD.jpg"). The first said I [did not select any partitions to use as swap space]("http://i.imgur.com/vVcgpIJ.jpg"), even though previously it had automatically done that for me. The second said the [partitions were too small]("http://i.imgur.com/spV2Xkz.jpg"). These were the auto-selections that seemed to work before. Also, why did it say 12.04 in the boot order if the USB says 13.04 was installed?  
  
I want to make sure this is not an error with the Raring Ringtail amd64 release before I learn to mess with the partitions, which is intimidating. Partition info is [here]("http://i.imgur.com/OA2Lvxi.jpg") and [here]("http://i.imgur.com/vkcxlIP.jpg") if it's relevant (I don't know much about partitioning but probably need to learn it to solve this). What should I do? I'm sort of a novice and have a lot more to learn about Linux...  
  
**TL;DR Ubuntu 13.04 amd64 USB pendrive created bizarre errors, I have no idea what's going on with my partitions now, but it did install something and reads the partitions differently.**

---

### Post by coffeecat on 2013-04-27
*Thread moved to **Installation & Upgrades**.*

---

### Post by grahammechanical on 2013-04-27
Which boot loader is giving you the boot options. If it is the Windows boot loader then it will still have the old label for Ubuntu. Please clarify that you did not install 12.04 using wubi.exe.

Regards.

---

### Post by Metavore on 2013-04-27
I'm not sure on the boot loader, I would assume it's Windows, not sure how to change that; kinda ignorant on that. I'm pretty sure when I installed 12.04 I did not use Wubi, I have a physical disc for it.

---

### Post by darkod on 2013-04-27
First thing first, does the 13.04 usb boot into live mode if you select the Try option? Is live mode working fine?

---

### Post by Metavore on 2013-04-27
Yes I believe live mode seems to work fine, and I chose the check disc for errors option and it was fine.

---

### Post by darkod on 2013-04-27
OK. From the images I can see that you have plenty of partitions, especially for someone not much into partitioning. :)

It should be no issue installing onto an existing partition using the manual method. You want a clean install, and you want to use an existing partition (where 12.04 was). That's easy.

But first, lets see more of these partitions. Can you boot into live mode, open terminal and post the output of:
```
sudo parted -l
```

---

### Post by Metavore on 2013-04-27
Currently typing from live 13.04. When I installed 12.04 when it first came out I followed some online Windows/Ubuntu dual-boot partition guide that I didn't understand too well then nor remember really at all now, but it was one of the top articles on the matter as far as I could tell so I just did what it said. I would like to actually learn though so I don't have this problem again.

 Here's the output:

[INDENT] Model: HP c325w (scsi)
Disk /dev/sda: 2022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2022MB  2022MB  primary  fat16        boot


Model: ATA TOSHIBA MK5059GS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  17.3GB  17.3GB  primary   ntfs         diag
 2      17.3GB  17.4GB  105MB   primary   ntfs         boot
 3      17.4GB  137GB   120GB   primary   ntfs
 4      137GB   500GB   363GB   extended
 5      137GB   138GB   500MB   logical   ext4
 8      138GB   144GB   6268MB  logical   ext4
 9      144GB   148GB   3729MB  logical
 6      148GB   496GB   348GB   logical   ext4
 7      496GB   500GB   3999MB  logical
[/INDENT]

---

### Post by darkod on 2013-04-27
OK. So, as you can see, partitions 5-9 are linux partitions. Three are ext4, and two I suppose should be swap area.

Now, the main question: Do you have any data you want to get out of these partitions (all of them), or not???

If not, just open the disk with parted and start deleting them:
```
sudo parted /dev/sdb
rm 5
rm 8
rm 9
rm 6
quit
```

That should delete all except #7 and quit parted. I left #7 on purpose to use it as swap.

After that start the installer again, and select the manual method (Something Else or whatever it's called in 13.04). When it shows the partitions list, you should see the three ntfs partitions, then free unallocated space, and then the 4GB partition.
From the free unallocated space create one big logical partition (it might not ask you if you want it as logical since that's the only option). In the Use As select ext4, the mount point /.
When back to the list, select the 4GB partition and click the Change button below. Select Use As swap area, there is no mount point for swap.

The device for bootloader option should show /dev/sdb, without any number in it.

That should be it.

If you do have data to get out, before starting the above procedure and deleting them, copy it somewhere.

---

### Post by Metavore on 2013-04-27
The only things I want to save are the Windows partitions, I spent a ton of time yesterday copying all of my Linux data for the new install. There's no chance that following your instructions should touch the Windows data at all, correct? I haven't backed my Windows data up, but it seems like there should be no special reason to if I do this properly.

Do you think there could still be an issue with the boot order, as [ 						 							]("http://ubuntuforums.org/member.php?u=1087323")[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") mentioned?

Thank you so much for the partitioning help!

---

### Post by Metavore on 2013-04-27
I will update after trying the re-partitioning within an hour.

---

### Post by darkod on 2013-04-27
As long as you are careful with the rm commands in the parted prompt, the windows partitions should be fine. You can use print in the parted prompt to print the table at any moment.

In fact, in live mode you can use Gparted which is a GUI tool where you can delete the partitions more easily. Open it and try there if you want to. Don't forget to click the green button to execute the changes at the end.

---

### Post by Metavore on 2013-04-27
So I followed instructions and am down to the fewer partitions, did the install, it said again need to restart to finish, did so, boot still shows Windows and 12.04 with 12.04 as the second in the list but the default highlighted. I might have changed some boot setting a long time ago and forgotten about it?

---

### Post by Metavore on 2013-04-27
I clearly messed something up (posted from a live 13.04 CD version of amd64):[INDENT=3]Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  17.3GB  17.3GB  primary   ntfs         diag
 2      17.3GB  17.4GB  105MB   primary   ntfs         boot
 3      17.4GB  137GB   120GB   primary   ntfs
 4      137GB   500GB   363GB   extended
 5      137GB   496GB   359GB   logical   ext4
 6      496GB   500GB   3998MB  logical


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

[/INDENT]

---

### Post by Metavore on 2013-04-27
In Gparted I changed the weird partition to "linux swap". No effect. I'm lost. The USB and the DVD both had the same outcome of installation, so either Ubuntu's amd64 source file is buggy or there's some secret boot menu that I don't know about that's choosing a fake 12.04 instead of 13.04.

---

### Post by Metavore on 2013-04-28
Since I didn't have any responses for awhile I made a disc of Raring Ringtail in 32-bit and installed it successfully. I really don't understand what happened with the amd64 source file, but my computer does run 64-bit architecture just fine otherwise, including my Windows OS. I don't think I will bother with 64-bit Ringtail, but the issue is still unresolved. Thanks Darko for the partitioning help.

---

### Post by darkod on 2013-04-28
It might have been a bad ISO. You can download it again, best from torrent because it checks for corruption during download.
Also, never burn OS install disks at max. People just leave burning at max, but that's very bad because it can create small errors (that even verify wouldn't show), but which can mess up your install with a corrupted file.

Always burn CDs at 8x-10x, not more, and DVD to 2x or 4x. You will wait few minutes more but you will have a good OS install media.

---

### Post by Metavore on 2013-04-28
Yeah for any ISO discs, especially something like an OS, I write it slowly. I think the only three options are that pendrivelinux was not prepared to handle the file properly, that the amd64 file from Ubuntu's website had an issue, or that the "check disc" option did not detect an existing error. Either way, would it be useful for me to try the "report as bug" to Canonical or whoever?

---

### Post by darkod on 2013-04-28
But if you can't reproduce it now, you can't report it. If you want to, you can give 64bit a shot again, before you have too much data and personal configuration done in the 32bit version. If it works this time with a new ISO, better to continue using 64bit right?

---

