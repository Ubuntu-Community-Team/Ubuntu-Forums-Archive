---
title: "Installation does not &quot;see&quot; other partitions / OS"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by rdh61 on 2012-06-13
Hi,

I am trying to install Ubuntu 12.04 from the live CD, on a desktop computer on which I have Windows XP and Ubuntu 10.10 on separate partitions. 

During installation the process does not find any OS already on my computer, and only offers me one device on which to install 12.04, i.e. the whole disk.

How can I proceed with the installation without wiping out my Windows installation?

Many thanks.

---

### Post by coffeecat on 2012-06-13
Hi, I can think of two reasons why the installer cannot see pre-existing operating systems. First - there could be an illegality in your partition table. Second - residual RAID metadata on a hard drive now used as a single drive can also confuse the installer.

Boot up the live CD and choose "try Ubuntu" to get to the live desktop. Open Gparted and take a screenshot (Alt+Print) of the open Gparted window, and post the screenshot. If there is a partition table irregularity, Gparted will probably falsely show the whole drive as "unallocated". Also, open a terminal and post the output of this command:

```
sudo fdisk -lu
```

This will give us the information in your partition table. For pasting the output into your post, you can highlight it with the mouse, right-click -> copy.

Was the hard drive ever used in a RAID?

---

### Post by rdh61 on 2012-06-14
Thanks for your reply.

I had to look up RAID. No I have never done that.

Gparted screenshot attached.

Output from sudo fdisk -lu ...

ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x621e939d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244155869   122077903+   7  HPFS/NTFS/exFAT
/dev/sda2       244155994   488392064   122118035+   5  Extended
/dev/sda3       484488333   488392064     1951866   82  Linux swap / Solaris
/dev/sda5       244155996   484488269   120166137   83  Linux

Disk /dev/sdb: 7873 MB, 7873757184 bytes
243 heads, 62 sectors/track, 1020 cylinders, total 15378432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$

---

### Post by zSeries on 2012-06-14
I had the same problem on one of my installs of 10.04, I have 7 disks in 4 PC's. After booting the Live CD go to Synaptic Package Manager and remove dmraid (assuming you dont want to use raid) and try again.

---

### Post by rdh61 on 2012-06-14
Thanks, but Synaptic tells me dmraid is not installed.

---

### Post by coffeecat on 2012-06-14
First thing - I can't see any illegalities in the partition table in the output of fdisk, but Gparted is showing "unallocated" which is what happens when there is. So I'm somewhat puzzled at the moment.

About RAID and the package dmraid. Simply uninstalling dmraid would not remove RAID metadata which is the other possible problem, even though you are sure the hard drive has not been used for RAID. You say that dmraid is not installed - I assume you mean in your 10.10 installation which would not be surprising since dmraid is not installed by default. And what is or is not installed in 10.10 would be irrelevant to your problem anyway. However, it is present in the live CD session and we can use it to see if there is indeed RAID metadata on your hard drive for whatever reason.

Boot up the live CD and go to the live desktop, open a terminal and run this command:

```
sudo dmraid --raid_devices -v
```

Do you get the message "no raid disks" or "INFO: RAID device discovered:"? If the latter, please post the entire message - there will be another line - and we'll take it from there.

---

### Post by zSeries on 2012-06-14
I just download and burnt a 12.04 Live CD. dmraid is installed. Please check that again. I suggested this because I have never used raid and the disk I had the problem with was already working on one 10.04 machine and I just moved it to another machine for a fresh re-install. It was a while ago I did this but I think this is the link that prompted me to remove dmraid.

[http://askubuntu.com/questions/56069/ubuntu-install-failing-hard-drive](http://askubuntu.com/questions/56069/ubuntu-install-failing-hard-drive)

I hope it helps.

---

### Post by coffeecat on 2012-06-14
@zSeries, please read my post again. The package dmraid is included in the live CD but it is **not** included in a default installation to a hard drive. The OP reports that synaptic says that dmraid is not installed which suggests to me that the OP is reporting on their permanent installation of Ubuntu 10.10. Besides, synaptic is not included in 12.04 either by default or in a permanent installation. The OP is using the 12.04 live CD so your suggestion to open Synaptic in the live 12.04 session is simply not going to work, because Synaptic is not there.

The askubuntu link you post is interesting but I am trying to determine a slightly different point. Residual RAID metadata can cause the problem the OP is describing, and I have seen threads where the OP thinks they have never used the hard drive in RAID, yet RAID metadata turns out to be the problem. I want to see if this is the case here. The dmraid command I suggested will tell us this. If this turns out not to be the case, I agree it would be a good idea to try to remove dmraid from the live session as suggested in the askubuntu link, but the OP would need to use apt-get from the command line to do this, not Synaptic.

---

### Post by rdh61 on 2012-06-14
@coffeecat

ubuntu@ubuntu:~$ sudo dmraid --raid_devices -v
no raid disks
ubuntu@ubuntu:~$ 

I can confirm that I have never used RAID , I didn-t even know what it was! When I took this computer over from someone else the HD was replaced with a new one, and I am the only one who has used the computer since.

@zSeries / coffeecat

I can confirm that on the pre-existing Ubuntu OS - 10.10 - dmraid is NOT installed.

Thank you for your efforts to help.

---

### Post by coffeecat on 2012-06-14
OK - it was a long shot but useful that we've excluded that as a possibility.

zSeries' suggestion is a good one, so try that next. What you would need to do in the live CD session (12.04) is to open a terminal, and:

```
sudo apt-get remove dmraid
```

(It's in the askubuntu link that zSeries posted.)

Out of interest, once you've run the apt-get remove command and removed the dmraid package, open Gparted and tell is whether it is still showing "unallocated", or whether it is showing your partition layout. Now start the installer and see whether it can now see your Windows and Ubuntu 10.10 installations.

The reason I ask is that the OP in the askubuntu page was able to use Gparted to edit partitions, but you are not, so it will be interesting to see if uninstalling dmraid helps in your situation.

If it doesn't, don't despair. I'll ask some other people to have a look to see if they have any suggestions.

---

### Post by rdh61 on 2012-06-14
After removal of dmraid, gParted still gives unallocated, and the installer still does not see my pre-existing OS.

During removal of dmraid, I got the following message >  update-initramfs is disabled since running on read-only media.
I don-t know if this is relevant.

---

### Post by rdh61 on 2012-06-14
Just a thought. Did you see the last line of my fdisk output? It says 'Device Boot      Start         End      Blocks   Id  System'. Is that important, by any chance?

---

### Post by coffeecat on 2012-06-14
> **rdh61 said:**
> Just a thought. Did you see the last line of my fdisk output? It says 'Device Boot      Start         End      Blocks   Id  System'. Is that important, by any chance?

They're important only in that they are the headings for the figures that follow, but they don't reveal any problem. I'll put the output between code tags so you can see:

```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x621e939d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244155869   122077903+   7  HPFS/NTFS/exFAT
/dev/sda2       244155994   488392064   122118035+   5  Extended
/dev/sda3       484488333   488392064     1951866   82  Linux swap / Solaris
/dev/sda5       244155996   484488269   120166137   83  Linux

```

Code tags preserve formatting which is lost if you post output straight into the main body of your post.

I'll pm someone else to have a look, and see if there is anything else they can suggest.

**EDIT:** sorry, should have added:

> **rdh61 said:**
> During removal of dmraid, I got the following message >  update-initramfs is disabled since running on read-only media.
I don-t know if this is relevant.

You can safely ignore that. The live system is telling you it can't recreate an initramfs which is only needed when first booting up.

---

### Post by oldfred on 2012-06-14
One other issue that I had before was chkdsk on the NTFS partition(s). My old XP would boot, but gparted would not even show drive. Some now see drive but not partition. So try chkdsk on all NTFS partitions.

From Windows install or repairCD.

chkdsk C: /r

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)


Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

---

### Post by rdh61 on 2012-06-14
@oldfred

Thanks for that, but I need clarification.

Do you mean that if I run chkdsk on my NTFS partition, it might correct the source of my problem, or that it might provide useful information about the problem? What should I expect as normal/abnormal results of running chkdsk, and how will it help?

Please could you elaborate?

Many thanks.

---

### Post by oldfred on 2012-06-14
Ubuntu runs fsck on every 40 or 60 reboots. I do not think Windows runs chkdsk unless you schedule it. But will often work even when chkdsk is needed.

Ubuntu & gparted will not mount NTFS partitions that need chkdsk, to prevent further damage that chkdsk may then not be able to correct. 

If files are corrupted chkdsk may move them to a temporary location for you to review. But most of the time it just cleans things up.

chkdsk does not fix everything on one pass, so if it reports any issues, you may need to rerun it until there are no issues. It can take a long time on a large full partition.

---

### Post by rdh61 on 2012-06-15
I have run chkdsk on my NTFS partition twice, first with the /r option, next with the /f option. I am unable to tell whether errors were found and fixed as chkdsk was scheduled at boot, and when finished the report ran before my eyes so quickly I couldn-t read it before Windows began to start up. However, in both cases the process was concluded.

Gparted still gives unallocated and the Ubuntu 12.04 installer still does not see my partitions.

Strangely, when using the preexisting Ubuntu 10.10, I have been trying to run the Disk Utility, and most times it refuses to open. However, after the first run of chkdsk on the Windows partition, it did open and listed both my partitions correctly. However, that only happened once and couldn-t be repeated.

---

### Post by coffeecat on 2012-06-15
Sorry to hear that the various suggestions have not helped. This really is a puzzle. This following is a long shot but it needs to be done in view of the odd behaviour of Disk Utility in 10.10. We need to exclude a failing hard drive.

Boot up the live 12.04 CD and open Disk Utility in the live desktop. Highlight your internal drive and look for the SMART data button in the right pane and click on it. What does it say about the health of the drive? Run a self-test to see if there are any problems. 

Also - while you are in the 12.04 live session, run this command and post the output:

```
sudo parted -l
```

The reason that Gparted is showing unallocated is that something is confusing the backend parted. It might be useful to see exactly what parted has to say about your hard drive.

---

### Post by rdh61 on 2012-06-15
The Disk Utility will not open in the 12.04 live cd session either. If I try to open it in the terminal I get>

[IMG]http://ubuntuforums.org/data:image/png;base64,PCFET0NUWVBFIEhUTUwgUFVCTElDICItLy9XM0MvL0RURCBIVE1MIDQuMCBUcmFuc2l0aW9uYWwvL0VOIj4KPEhUTUw+CjxIRUFEPgoJPE1FVEEgSFRUUC1FUVVJVj0iQ09OVEVOVC1UWVBFIiBDT05URU5UPSJ0ZXh0L2h0bWw7IGNoYXJzZXQ9dXRmLTgiPgoJPFRJVExFPjwvVElUTEU+Cgk8TUVUQSBOQU1FPSJHRU5FUkFUT1IiIENPTlRFTlQ9IkxpYnJlT2ZmaWNlIDMuNSAgKExpbnV4KSI+Cgk8U1RZTEUgVFlQRT0idGV4dC9jc3MiPgoJPCEtLQoJCUBwYWdlIHsgbWFyZ2luOiAwLjc5aW4gfQoJCVAgeyBtYXJnaW4tYm90dG9tOiAwLjA4aW4gfQoJLS0+Cgk8L1NUWUxFPgo8L0hFQUQ+CjxCT0RZIExBTkc9ImVuLVVTIiBESVI9IkxUUiI+CjxQIFNUWUxFPSJtYXJnaW4tYm90dG9tOiAwaW4iPnVidW50dUB1YnVudHU6fiQgcGFsaW1wc2VzdA08L1A+CjxQIFNUWUxFPSJtYXJnaW4tYm90dG9tOiAwaW4iPioqDTwvUD4KPFAgU1RZTEU9Im1hcmdpbi1ib3R0b206IDBpbiI+bGliZ2R1OkVSUk9SOmdkdS1wb29sLmM6MjM3NDpkZXZpY2VfcmVjdXJzZToKYXNzZXJ0aW9uIGZhaWxlZDogKGRlcHRoICZsdDsgMTAwKQ08L1A+CjxQIFNUWUxFPSJtYXJnaW4tYm90dG9tOiAwaW4iPkFib3J0ZWQgKGNvcmUgZHVtcGVkKQ0gCjwvUD4KPC9CT0RZPgo8L0hUTUw+AA==[/IMG]   	 	 	 	 	 	   ubuntu@ubuntu:~$ palimpsest 
 ** 
 libgdu:ERROR:gdu-pool.c:2374:device_recurse: assertion failed: (depth < 100) 
 Aborted (core dumped) 





Gparted tells me>


   	 	 	 	 	 	   
ubuntu@ubuntu:~$ sudo parted -l 
 Error: Can't have overlapping partitions.                                  
  
 Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1 
 has been opened read-only. 
 Error: Can't have a partition outside the disk!

---

### Post by coffeecat on 2012-06-15
There appears to be an image in your post but something has happened to the URL. Rather than my interfering with it, could you edit your post and see if you can get it visible?

Anyway - we make some sort of progress!

> **rdh61 said:**
> ubuntu@ubuntu:~$ sudo parted -l 
 [COLOR="Red"]Error: Can't have overlapping partitions.[/COLOR]                                  
  
 Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1 
 has been opened read-only. 
 [COLOR="Red"]Error: Can't have a partition outside the disk![/COLOR]

That was one of the things I expected right at the beginning, and it would explain your problems, but I couldn't see that in the output of fdisk. Perhaps I missed something. I shall have another look and post again.

---

### Post by rdh61 on 2012-06-15
There is no image in my previous post. Just an inadvertent space!

At my next boot into 10.10, Disk Utility opened the first time (but not subsequent times). SMART data said my hard drive is healthy. Short self test gave OK with no errors reported.

My partitions (NTFS and dev/sda1) were listed correctly but the dev/sda1 partition was given as "unmounted" (??).

**EDIT: Correction - I now realise the NTFS partition IS dev/sda1 - it appeared to me they were listed side by side. If I can get Disk Utility to open again, I'll have a better look.**

From Gparted I got: 

robert@robert-desktop:~$ sudo parted -l
Error: Can't have overlapping partitions.

---

### Post by coffeecat on 2012-06-15
I've had another look at your fdisk output (reposted in code tags in my post #14) and I simply cannot find evidence of overlapping partitions or a partition outside the disk. Nevertheless, that is what parted is grumbling about and they are precisely the partition table irregularities that I was looking for originally.

Sorry - but time to boot up the live CD again. Run this again and post the output:

```
sudo fdisk -lu
```

Just to be sure that the output is still the same or if it is now showing the problems that parted refers to. Next, go to this page:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Download and install the app fixparts (**not** gdisk as Rod warns on that page!). Make sure you run the sfdisk command to backup your present partition table, and save the text file to a separate medium. You need to run "sudo sfdisk...." where Rod tells you to run sfdisk from a root prompt. Now run fixparts ("sudo fixparts /dev/sda") and simply 'w' at the fixparts prompt to rewrite the partition table and exit. Had we been able to diagnose precisely the partition table problem from fdisk, I was going to suggest fixparts anyway, but the advantage it has is that it "automatically (and silently) make(s) adjustments for certain problems it finds" so that you often only have to 'w' and exit. Hopefully that will fix whatever is ailing the partition table.

---

### Post by coffeecat on 2012-06-15
> **rdh61 said:**
> There is no image in my previous post. Just an inadvertent space!

Nope. Definitely an intended image. This is what I am seeing in the raw BBCode:

> **rdh61 said:**
> [noparse] If I try to open it in the terminal I get>

[IMG]http://ubuntuforums.org/data:image/png;base64,PCFET0NUWVBFIEhUTUwgUFVCTElDICItLy9XM0MvL0RURCBIVE1MIDQuMCBUcmFuc2l0aW9uYWwvL0VOIj4KPEhUTUw+CjxIRUFEPgoJPE1FVEEgSFRUUC1FUVVJVj0iQ09OVEVOVC1UWVBFIiBDT05URU5UPSJ0ZXh0L2h0bWw7IGNoYXJzZXQ9dXRmLTgiPgoJPFRJVExFPjwvVElUTEU+Cgk8TUVUQSBOQU1FPSJHRU5FUkFUT1IiIENPTlRFTlQ9IkxpYnJlT2ZmaWNlIDMuNSAgKExpbnV4KSI+Cgk8U1RZTEUgVFlQRT0idGV4dC9jc3MiPgoJPCEtLQoJCUBwYWdlIHsgbWFyZ2luOiAwLjc5aW4gfQoJCVAgeyBtYXJnaW4tYm90dG9tOiAwLjA4aW4gfQoJLS0+Cgk8L1NUWUxFPgo8L0hFQUQ+CjxCT0RZIExBTkc9ImVuLVVTIiBESVI9IkxUUiI+CjxQIFNUWUxFPSJtYXJnaW4tYm90dG9tOiAwaW4iPnVidW50dUB1YnVudHU6fiQgcGFsaW1wc2VzdA08L1A+CjxQIFNUWUxFPSJtYXJnaW4tYm90dG9tOiAwaW4iPioqDTwvUD4KPFAgU1RZTEU9Im1hcmdpbi1ib3R0b206IDBpbiI+bGliZ2R1OkVSUk9SOmdkdS1wb29sLmM6MjM3NDpkZXZpY2VfcmVjdXJzZToKYXNzZXJ0aW9uIGZhaWxlZDogKGRlcHRoICZsdDsgMTAwKQ08L1A+CjxQIFNUWUxFPSJtYXJnaW4tYm90dG9tOiAwaW4iPkFib3J0ZWQgKGNvcmUgZHVtcGVkKQ0gCjwvUD4KPC9CT0RZPgo8L0hUTUw+AA==[/IMG]   	 	 	 	 	 	   ubuntu@ubuntu:~$ palimpsest [/noparse]

---

### Post by rdh61 on 2012-06-15
> **coffeecat said:**
> Nope. Definitely an intended image. This is what I am seeing in the raw BBCode:

Well I have no idea what that is about - I didn't intend to include any image!

Re your previous post, thank you, I have been busy this afternoon so haven't been able to attend to it. I'll get back to this tomorrow morning.

Have a nice evening.

---

### Post by rdh61 on 2012-06-16
```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x621e939d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244155869   122077903+   7  HPFS/NTFS/exFAT
/dev/sda2       244155994   488392064   122118035+   5  Extended
/dev/sda3       484488333   488392064     1951866   82  Linux swap / Solaris
/dev/sda5       244155996   484488269   120166137   83  Linux

```   	 	 	 	

Looks the same to me. I-ll now proceed to your suggestion to download, install and run fixparts.

---

### Post by rdh61 on 2012-06-16
I ran fdisk as instructed {following Rod-s instructions, I think, to the letter}, but now at boot I am getting a black screen saying...

error. no such partition
grub rescue>_

Help!

BTW, 
1. How do I get to my files from the live cd?
2. How do I get into my removable media from the live cd?

---

### Post by rdh61 on 2012-06-16
Now...

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x621e939d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244155869   122077903+   7  HPFS/NTFS/exFAT
/dev/sda2       244155995   484488269   120166137+   f  W95 Ext'd (LBA)
/dev/sda3       484488333   488392064     1951866   82  Linux swap / Solaris
/dev/sda5       244155996   484488269   120166137   83  Linux

```

---

### Post by coffeecat on 2012-06-16
First - an apology. The partition table irregularity was there all along, and I didn't see it for looking. If you look at your earlier fdisk output, either in my post #13 or your post #25, you'll see that sda3 is "inside" your extended partition sda2. By definition, sda3 is a primary partition and cannot be inside an extended partition. Fixparts has now fixed that for you by changing the extended partition boundaries and sda3 is now outside the extended partition, and  your partition table is now OK (although I'll double-check this again, since I missed that problem before). The primary inside an extended irregularity would have caused the Gparted and installer problems you saw before, and if you go to Gparted in the live CD, hopefully you should now see your partitions.

But you have a new problem for some reason:

> **rdh61 said:**
> I think, to the letter}, but now at boot I am getting a black screen saying...

error. no such partition
grub rescue>_

This is probably grub in the mbr complaining that it cannot find the Ubuntu root partition. Running fixparts would not have caused this because your Ubuntu root partition, sda5, is still there and fixparts would not have changed the UUID. We need to investigate. Boot up the live Ubuntu CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page but there is one error, see below - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The error is that the bootinfoscript file is now named "bootinfoscript", not "boot_info_script.sh", so you need to move it to your live desktop and run:

```
sudo bash ~/Desktop/bootinfoscript
```

> **rdh61 said:**
> 
BTW, 
1. How do I get to my files from the live cd?
2. How do I get into my removable media from the live cd?

To rescue personal files from the hard drive using the live CD, open a Nautilus file browser window in the live session and look for your Windows partition in the left pane. Click on it and it will be mounted and the filesystem shown in the main pane of the file browser. Plug your USB drive in and it will be automounted and another Nautilus window will open. Simply copy by drag and drop to backup.

For your Ubuntu partition, you will run into permissions problems with your personal files, so you need to do the following. Click on the Ubuntu partition where it appears in the left pane of a file browser. Now ctrl-L and take a note of the mount path as it appears in the address bar. It will be "/media/something", where something is either the partition label or the UUID of the partition, a long alphanumeric string. You can close that window. Now from a terminal:

```
gksu nautilus
```

Click on File System in the left pane, and then open the /media folder. Now open the folder named whatever "something" was, now /home, and now the folder with your Ubuntu username. That is your home folder and you can backup your files by drag and drop to the USB drive file browser window.

---

### Post by rdh61 on 2012-06-16
Thanks for that. 

The situation has changed. Before I read your post above I tried to restore grub. Grub now appears at start up but when I try to boot Ubuntu, I get a black screen with the following error messages>

error> no argument specified
error> no such partition
error> you need to load the kernel first

However, I have just run bootinfoscript, and this is the output in the results file>

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda2 and looks at sector 1 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   244,155,869   244,155,807   7 NTFS / exFAT / HPFS
/dev/sda2         244,155,995   484,488,269   240,332,275   f W95 Extended (LBA)
/dev/sda5         244,155,996   484,488,269   240,332,274  83 Linux
/dev/sda3         484,488,333   488,392,064     3,903,732  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        80D83638D8362D32                       ntfs       
/dev/sda3        4b60c048-ee0b-4a31-ac2b-3e77907ffa95   swap       
/dev/sda5        4be83463-1b99-4c09-98ea-ca8fd716deef   ext4       
/dev/sdb         AE8D-C9FE                              vfat       ADATA
/dev/sr1                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 4be83463-1b99-4c09-98ea-ca8fd716deef
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 4be83463-1b99-4c09-98ea-ca8fd716deef
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 4be83463-1b99-4c09-98ea-ca8fd716deef
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=4be83463-1b99-4c09-98ea-ca8fd716deef ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 4be83463-1b99-4c09-98ea-ca8fd716deef
    echo    'Loading Linux 2.6.35-32-generic ...'
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=4be83463-1b99-4c09-98ea-ca8fd716deef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 4be83463-1b99-4c09-98ea-ca8fd716deef
    linux    /boot/vmlinuz-2.6.35-31-generic root=UUID=4be83463-1b99-4c09-98ea-ca8fd716deef ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 4be83463-1b99-4c09-98ea-ca8fd716deef
    echo    'Loading Linux 2.6.35-31-generic ...'
    linux    /boot/vmlinuz-2.6.35-31-generic root=UUID=4be83463-1b99-4c09-98ea-ca8fd716deef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-31-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 4be83463-1b99-4c09-98ea-ca8fd716deef
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 4be83463-1b99-4c09-98ea-ca8fd716deef
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 80D83638D8362D32
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=4b60c048-ee0b-4a31-ac2b-3e77907ffa95 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.35-31-generic              2
               =                boot/initrd.img-2.6.35-32-generic              1
               =                boot/vmlinuz-2.6.35-31-generic                 1
               =                boot/vmlinuz-2.6.35-32-generic                 1
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

I gave the installer a trial run and notice that it now recognises my Windows XP and Ubuntu 10.10 OSs. As this is becoming quite frustrating, I am tempted now just to try to go ahead with the installation without further ado. Is there any reason why I should not do this? If it fails, I am now resigned to pressing the red button and reinstalling both my OSs from scratch.

---

### Post by coffeecat on 2012-06-16
> **rdh61 said:**
> 
I gave the installer a trial run and notice that it now recognises my Windows XP and Ubuntu 10.10 OSs. As this is becoming quite frustrating, I am tempted now just to try to go ahead with the installation without further ado. Is there any reason why I should not do this? If it fails, I am now resigned to pressing the red button and reinstalling both my OSs from scratch.

I'll examine your boot script output in detail and post back with my thoughts later, but in the meantime that's a perfectly good idea. Whether you install 12.04 to the old 10.10 partition, or whether you make room for 12.04 and set up a triple-boot, the 12.04 installer will install grub to the mbr and set up a grub menu in the 12.04 partition with boot options for all the OSs on your hard drive.

I notice that grub has been installed to the extended partition, sda2, which is a mistake, but it's probably not doing any harm there, or anything at all for that matter. But as I said, I'll get back when I've looked in more detail.

---

### Post by coffeecat on 2012-06-16
I've found a problem which would prevent you from booting Ubuntu 10.10, but it throws up another mystery. The contents of your sda5 Ubuntu /etc/fstab are:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR="Red"]/dev/sda6       /               ext4    errors=remount-ro,user_xattr 0       1[/COLOR]
# swap was on /dev/sda5 during installation
UUID=4b60c048-ee0b-4a31-ac2b-3e77907ffa95 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I've highlighted the problem line in red, which defines your root partition as sda6. It isn't, it's sda5, and you did not have a sda6 partition when you started this thread according to the information you posted, so I do not understand how you were able to boot Ubuntu at all.

Have you ever edited /etc/fstab yourself?

This is fixable from the live CD. If you intend to make a Windows/10.10/12/04 triple-boot, you would need to fix this before the new 12.04 grub menu will be able to boot 10.10. Let me know what you intend to do and we'll take it from there.

---

### Post by rdh61 on 2012-06-16
> **coffeecat said:**
> 
Have you ever edited /etc/fstab yourself?


I wouldn't have thought so. What might be a reason for doing so?

Anyway, what I've done is this. I installed 12.04, initially opting to replace 10.10 (not upgrade). At the end of the process, which appeared to be going on normally, I got thrown something about grub being installed on /dev/sdb, which wasn't right, and asking me were it should be installed. I chose /dev/sda, but on reboot I got a black screen with a lot of gobbledegook. At that point I was just on my way to my tool box to fetch a large hammer, when it occurred to me to try again, but this time to change the partition table. 

I selected "do not use this partition" for sda5, before changing it back to "ext 4", ticking the box to format the partition, and selecting the mount point /. This time the installation worked, both 12.04 and Windows boot successfully, and I have a working system. Thank you so much. I could never have done it without you.

Any reason you can think of for the initial illegalities in my partition table?

Is this all right now?

```
robert@robert-desktop:~$ sudo fdisk -lu
[sudo] password for robert: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x621e939d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244155869   122077903+   7  HPFS/NTFS/exFAT
/dev/sda2       244156414   484487167   120165377    5  Extended
/dev/sda3       484488333   488392064     1951866   82  Linux swap / Solaris
/dev/sda5       244156416   484487167   120165376   83  Linux

Disk /dev/sdb: 7873 MB, 7873757184 bytes
243 heads, 62 sectors/track, 1020 cylinders, total 15378432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by coffeecat on 2012-06-16
With regard to /etc/fstab, it's odd that your root partition appears as /dev/sda6, rather than with a UUID reference. This used to happen (perhaps it still does) with the alternate CD installer and was not a problem so long as the partition didn't change number. If you look at your new 12.04 /etc/fstab, you'll see that the root partition line is identified with the UUID for the partition. This means that even if the partition number changes, things will still work. The fact that your swap partition was /dev/sda5 originally, but is now sda3, suggests that you have used a partitioning tool at some time and that this renumbered some of the partitions. Which leads to....

> **rdh61 said:**
> 
Any reason you can think of for the initial illegalities in my partition table?

A primary inside an extended suggests a Windows-based partitioning software to me. Some of them are prone to do this. Have you used a Windows-based partitioner? If so, what did you get it to do?

> **rdh61 said:**
> Is this all right now?

```
robert@robert-desktop:~$ sudo fdisk -lu
[sudo] password for robert: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x621e939d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244155869   122077903+   7  HPFS/NTFS/exFAT
/dev/sda2       244156414   484487167   120165377    5  Extended
/dev/sda3       484488333   488392064     1951866   82  Linux swap / Solaris
/dev/sda5       244156416   484487167   120165376   83  Linux
```

That looks OK to me. You have a primary partition after the extended partition, and only one logical in the extended, which is not particularly tidy, but there's no real problem with it. It's a result of having to repair the original illegality with fixparts.

Is everything working now? :)

---

### Post by rdh61 on 2012-06-16
> **coffeecat said:**
> Have you used a Windows-based partitioner? If so, what did you get it to do?

God only knows - I'm sure I might not even remember a thing like that!

> **coffeecat said:**
> Is everything working now?

Fine thank you. I'm marking the thread solved.  ):P

---

### Post by coffeecat on 2012-06-16
Good luck! :)

---

