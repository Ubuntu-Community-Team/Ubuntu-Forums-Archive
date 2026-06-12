---
title: "installation drive partitioning with multiple existing NTFS partitions"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by codenameSQL on 2013-06-28
Hi guys,
Absolute newbie here (which will likely be quite obvious).  I have conducted multiple searches of this forum and could not find an answer to this drive partitioning question.

I'm running on the Lubuntu 13.04  live CD as I type.  Seems to run better than fine, even from the CD.  I have an older XP machine with Intel P4 on which I want to install.  My question concerns the drive partitioning.  When I try to do an auto install, I'm given a slider to select the size of the Buntu partition.  Well, my main drive already has three NTFS partitions and the slider/install doesn't show those existing partitions, but only the two sides of the slider which increase/decrease moving left to right and vice versa.  So, I stopped the install and came here.  

So, I guess my question is, do I need to use a tool such as Easus to resize/create a new partition for Lubuntu?  If so, then how do I bypass the slider and tell it to install to that new partition?

Or will the slider option create a new partition WITHOUT destroying the existing multiple partitions?  If so, is there a way to specify which one of the existing partitions to resize?  I'm sure it works perfectly if the drive only has one existing partition, but with three -- seemed more prudent to ask for assistance prior to causing myself some major grief.. 

Hope this made sense.  
Thanks!
Dave

---

### Post by Mark Phelps on 2013-06-28
Using the slider has an unfortunate history of corrupting Windows -- but that has happened primarily with Vista, Win7, and Win8.  I don't know that will happen with XP.

In my own experience, Windows utilities work best with Windows filesystems; Linux utilities with Linux filesystems. The Minitool Partition Wizard folks used to offer a free Minitool Partition Wizard Boot CD ISO file you could download, burn to CD, and boot from that to safely do Windows partitioning.  With v7.8, they changed that so that now, you have to download their app (still free), install in Windows, and create the Boot CD/USB from their app.  Same results, just more work involved.

If you have EASUS, you can use that instead -- to shrink an XP partition to make room.

So you know, the slider WILL shrink an existing Windows NTFS partition, there's just no guarantee that it won't result in filesystem corruption in the process.

Once you have the unallocated space, boot into the Ubuntu install media and use the "something else" option to manually create the filesystem partitions.

---

### Post by codenameSQL on 2013-06-28
Thanks!  Okay, I have my free space (putting Lubuntu on its own disk instead of screwing with the NTFS partitions)  and using the "something else" option.

SO, setting the partition as "primary", "ext4 journaling", and the mount point at "/".

I've saved some free space on this disk to add another flavor of Linux later but I'll deal with that later after I learn a bit  more about the OS.


My remaining question here is.. since I didn't use the "install alongside windows" option,  will Lubuntu still add itself to the boot menu alongside XP for selection? or do I need to do something extra so that it doesn't wipe the existing boot menu and just adds itself?

---

### Post by Bashing-om on 2013-06-28
codenameSQL; Woahh !
That option uses the entire disk and wipes out your windows install !

---

### Post by Bashing-om on 2013-06-28
codenameSQL; Good !

That will work ... you need to make a "swap" partition -- depending on how much ram you have ... the more ram the less now-a-days space in swap is needed, unless you intend to hibernate then will need a bit more in swap than there is ram on board.

Keep in mind using the "msdos" partitioning can only have a max of 4 primary partitions per disk... for long term you may want to consider at this point to make a separate partition for /home... think about setting up an extended partition and in that extended partition the two partitions, /home and swap as logical partitions. -- the extended partition counts as 1 of the max four primary partitions... one may have as may logical partitions within the extended partition as one wants.

Remember to think about how you want to boot up the operating systems. If you place grub onto the MBR of the primary booting disk then can chainload windows ... having the choice in grub which system to boot up... else leave Windows' boot code alone, install grub onto the disk that holds 'buntu and one must choose the system to boot from setting the boot order in bios.

sorry for delay in getting back ... did not see your last ... was in a worry you were going to overwrite Windows ... and was really watching for your reply ....

[INDENT][INDENT]it is all good now
[/INDENT][/INDENT]

---

### Post by codenameSQL on 2013-06-28
LoL.. well, I guess it's a good thing I went to dinner before completing the install. 

Okay, here is where I am... 

WinXP is on sdc1  (the primary SATA boot drive).. I want to dual boot

I freed up a disk different disk by wiping the partition with gparted.  This is the primary IDE sda and I have not created a new partition yet. It's just free space.


I began the install and chose "something else"

I'm now trying to partition and install Lubuntu on 20G of the free space on the sda disk -- and want to, perhaps, install another flavor of linux on a second partition of sda  (sda2 I would surmise) at a later date or perhaps just use the extra unallocated space as a partition for data. Not sure yet.. but I'll worry about that later after I am much more comfortable with the OS

So...

The settings I mentioned in my second post above are the ones keyed in and ready to click "install now". 

So, how do I install to this new drive without wiping out XP and the ability to dual boot?

---

### Post by codenameSQL on 2013-06-28
Ooops, I appreciate it, Bashing-OM, I guess we posted at nearly the same time.. thanks for the elaboration...  let me absorb what's there...

---

### Post by Bashing-om on 2013-06-28
All good .. except ya have no provision for swap ... 

Now You are absolutely sure that Windows is on that second disk ... that the first disk is to have ubuntu ... you are correct ... 1st disk is sda .. 1st disk 1st  parttion = sda1, 1st disk 2nd partition =sda2 ;second disk -ubuntu talk-  is sdb ; third disk/device sdc.

Now that said ... the primary boot drive you refer to as sdc ... confusing as the primary boot drive is generally in ubuntu sda.

is it too late to look at the disk nomenclature and see what is what before hitting that "do it" button ?

And yeah 20 gigs is plenty for a starter ... with the unallocated space on the disk ... gives elbow room for future expansion to whatever.

[INDENT][INDENT]do it right the first time[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-06-29
codenameSQL; Hey..
I have not heard from you... hope all is/went well...
If at this time there exist uncertainty ...from "try ubuntu" -> desktop; key combo ctl+alt+t ->terminal:
in terminal do:
```
sudo fdisk -lu
``` will relate what the disk are and the partitioning;
Device identifier (ie sda) and partitioning; NTFS = Windows. Will be easy to cross relate to disk usage then.

Preparing to call it a night, will check on your status in my afternoon... I will be away from the keyboard 'till the afternoon.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by codenameSQL on 2013-06-29
> **Bashing-om said:**
> All good .. except ya have no provision for swap ... 

Now You are absolutely sure that Windows is on that second disk ... that the first disk is to have ubuntu ... you are correct ... 1st disk is sda .. 1st disk 1st  parttion = sda1, 1st disk 2nd partition =sda2 ;second disk -ubuntu talk-  is sdb ; third disk/device sdc.

Now that said ... the primary boot drive you refer to as sdc ... confusing as the primary boot drive is generally in ubuntu sda.

is it too late to look at the disk nomenclature and see what is what before hitting that "do it" button ?

And yeah 20 gigs is plenty for a starter ... with the unallocated space on the disk ... gives elbow room for future expansion to whatever.[INDENT][INDENT]do it right the first time[/INDENT]
[/INDENT]


Sorry for my delay.. we had a massive thunderstorm here and I needed to power everything down for a bit.. I really appreciate the help.

Okay windows is actually on disk 3 (this is basically a drive server for the home network so there are a bunch of drives connected via SATA, IDE, USB and even FireWire)..  disk 3 shows the three partitions as mentioned in the first post and is indicated as sdc1, sdc2, sdc3 with XP being installed on sdc1  ..  I will unmount all but the necessary ones prior to install, but there all mounted now so I could run that command you sent and see exactly how they are all mapped by Linux.

I have 4G of RAM, so I've created a 2nd"swap"  partition of 5G on sda which is now showing as sda5 "Linux Swap"..  I had the choice of primary or logical and the "logical" choice for the swap seemed to be the most logical.  ;) but let me know please if it needs to be primary.  There was no "extended" option.

Here is the result from that fdisk -lu  .. 

```


lubuntu@lubuntu:~$ sudo fdisk -lu


[COLOR=#ff0000]---- disk I'm trying to install Lubuntu on -- no partitions created yet  ---
[/COLOR]
**[COLOR=#000000]Disk /dev/sda: 61.5 GB, 61492838400 bytes[/COLOR]**
**[COLOR=#000000]255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors[/COLOR]**
**[COLOR=#000000]Units = sectors of 1 * 512 = 512 bytes[/COLOR]**
**[COLOR=#000000]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]**
**[COLOR=#000000]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]**
**[COLOR=#000000]Disk identifier: 0xd879e908[/COLOR]**


   Device Boot      Start         End      Blocks   Id  System

[COLOR=#ff0000]------- disk with XP ----- [/COLOR]
**Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes**
**255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors**
**Units = sectors of 1 * 512 = 512 bytes**
**Sector size (logical/physical): 512 bytes / 512 bytes**
**I/O size (minimum/optimal): 512 bytes / 512 bytes**
**Disk identifier: 0xee16ee16**

**   Device Boot      Start         End      Blocks   Id  System**
**/dev/sdc1   *          63   142143119    71071528+   7  HPFS/NTFS/exFAT**
**/dev/sdc2       142143120   450558989   154207935    7  HPFS/NTFS/exFAT**
**/dev/sdc3       450558990  1953520064   751480537+   7  HPFS/NTFS/exFAT**


[COLOR=#ff0000]-- and the slew of other disks -- included just because the info there and may be useful?? ...[/COLOR]
WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0e314c61


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0450044f


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   234436544   117218241    7  HPFS/NTFS/exFAT


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6349a1b


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  1953523119   976760536    7  HPFS/NTFS/exFAT


Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb075412e


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   976768064   488384001    7  HPFS/NTFS/exFAT


Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6a6862f


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63   976768064   488384001    7  HPFS/NTFS/exFAT


Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7fe15203


   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1           16065  1953520064   976752000    f  W95 Ext'd (LBA)
/dev/sdh5           16128  1953520064   976751968+   7  HPFS/NTFS/exFAT


Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0489b913


   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1              63  3907024064  1953512001    7  HPFS/NTFS/exFAT
lubuntu@lubuntu:~$ 


```


So is it cool to run with the install as is stands? or should I tweak something in a more beneficial way?

---

### Post by Bashing-om on 2013-06-29
codenameSQL;

Yeah... You are good to go ... I agree that sda is the 'buntu install drive... as long as you are careful and watch that the install is to sda, there is no real need to pull all those drives.. be slow and watch to see that all reference in installing are "sda"...inclusive of grub to sda .... not to a partition on that disk (as in sda1)... install grub to the MBR of sda. The grub install will probe for all operating systems and chainload them onto grub. 

Swap on a logical partition is a good thing... 4 partitions max for msdos partitioning on the hard drive.

Loss of power at a critical time has bit me more than once; you were wise to power down and wait !

[INDENT][INDENT]good things happen[/INDENT][/INDENT]

---

### Post by codenameSQL on 2013-06-29
Adding...
At the bottom of the partitioning window there is a drop down for "Device for boot loader installation"...  should that remain as the default of sda1?  or does it need to be changed to sdc1 to be "alongside" windows?  Definitely don't want to wipe the windows MBR via impatiently ignorant button clicking, so I'll wait a little while to hit that button... :p


edit: Adding again.. patience is indeed a virtue... after reading your post more closely I see that you already answered the above question with reference to 'grub' which I didn't get at first -- that grub is actually the boot loader.  Hey, none of you snickering readers knew what the heck that was either --  until you, uh, knew... 

So, you're indicating that I should change the "Device for boot loader installation" from the default of "dev/sda1" to "dev/sda    ATA Maxtor etc. etc" -- Correct?

Then the install occurs and will find XP and create the boot menu which I take it will list Lubuntu and XP..  which, if actually the scenario, brings me to yet another question...  if I select XP, does grub then pass to the existing XP menu or will it launch directly into XP?    Currently there are three options at boot - XP Pro, Recovery Console, XP Pro 3GB switch.  I need to make sure those remain available or understand how/what to edit to get them back.

---

### Post by Bashing-om on 2013-06-29
codenameSQL;
I am back...sooner than I expected ...good deal !

How are you looking ? Done the install ? Did you find that so long as grub is installed to the stand alone sda, the other systems boot loaders are untouched. Grub's os-prober finds the other OSs and gives you the menu to choose what to boot (sda as the boot drive !).

I do not recognize the term "XP Pro 3GB switch"... I expect that maybe to be a bootloader for several other OSs ?? To be honest...grub deals with most boot codes... but not all .

Oh yes...making the transition to linux is a learning curve ,,,none will snicker or laugh ! None were born knowing what we know ...
Here there is no such thing as a dumb question,,,,this is open source -> no secrets -> one for all and all for one ! -the only dumb question is the one that is not asked - 'Nuff said ?

Documentation is in over abundance ...'buntu is constantly evolving and what was pertinent, no longer applies. Learning where to make that distinction is a milestone.

[INDENT][INDENT]progress, one step at a time
[/INDENT][/INDENT]

---

### Post by codenameSQL on 2013-06-29
Yep, the system is up and running now. Only a minor glitch in that the install hung at the reboot shutdown -- possibly because of the number of physical disks attached, but that's just a wild guess.  I let it sit long enough to be 99.9% sure she was hung and then reset.

A note for something which should be obvious prior but I didn't catch until I was forced to think about it is that the machine first booted up into the usual WinXP menu..  That was a bios setting. I needed to set the bios boot priority to point at the "grub" disk rather than the XP disk and all appears to be running fine now.  I suppose I could edit the WIN loader to point to Lubuntu, but doesn't seem much of a necessity or even benefit.

Yeah, it was pretty smooth overall.

as an aside, the 3GB switch, nutshell  version., is just an optional argument when launching XP which limits the OS to a gig of memory and allows programs/services which are specifically written to utilize the extra memory (3GB) to do so, e.g., SQL Server, some graphic/video editors.  More of a specific circumstance tool.

The recovery console and 3GB switch options are not listed in the grub menu but they are definitely available if I change boot priority back to the XP drive in the bios.  That's good enough for me in those rare instances I'd need either of those secondary options...

I appreciate the assistance.  Thus endeth the deer in headlights phase and now onto that learning curve. Hopefully it won't be too slippery of a slope.  :KS

---

### Post by Mark Phelps on 2013-06-29
Two points ...

First, it is always a SAFE option to disconnect all the other drives with installing an OS. Not necessary, but it prevent the problem of accidentally overwriting an MBR on another drive and/or writing GRUB to the "wrong" drive.  And yeah, it's a pain to do this --but you're only doing it once, for the OS installation.

Second, if you're going to use an entire physical drive, there is no need to use "something else". Just let the installer default and it will create two partitions -- one for the root filesystem, and a second one for swap.

---

