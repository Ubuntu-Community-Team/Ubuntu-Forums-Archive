---
title: "Dual boot Windows 7 and Ubuntu 11.04 on GPT"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by marlon_smith on 2011-08-16
Hi everyone,

I've spent the entire day on this and it's driving me insane.  I installed Ubuntu, used it for a few weeks, and then decided to add Windows 7.  I ran into tons of trouble, and ended up in my current situation: neither Ubuntu or WIndows is booting.  I'm writing this message from a LiveCD.

I started gparted and removed windows.  I then moved my Ubuntu partition (which has work stuff on it), to get the following, as reported by gparted:

/dev/sda1 977KiB (unknown filesystem, but I think this is where GRUB2 lives)
unallocated 97.66 GiB
/dev/sda2 1.72 TiB (ext4, my main Ubuntu partition)
/dev/sda3 7.92 GiB (linux-swap)

From this point, I'd like to install Windows 7 in the unallocated space, and then install GRUB2 so that I can dual boot Ubuntu and Windows.

Earlier, before I deleted Windows and it was the only thing booting (since GRUB had been wiped out by it), I reinstalled GRUB, and completely lost access to Windows.  I feel like if I install Windows now, and then install GRUB again, I'll just repeat my previous failure: Windows will be inaccessible.

The drive has a GPT partition table on it, so I think a lot of the forum posts I read about similar problems may not apply.  Fixing my MBR seems to be useless.

Help, please!!

Thanks

Marlon

---

### Post by YesWeCan on 2011-08-17
If your disk is 2TiB or less why not convert it back to MBR so you can greatly simplify your installations? This will erase your GPT header and your existing partitions too:
sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sdx
where x is the letter of your GPT disk

About GPT. There are two boot systems now, the new UEFI and the old BIOS. I understand that on a GPT disk Windows will only install, if at all, to use the UEFI and requires a special efi-system partition. Ubuntu will normally install to use BIOS if you make a special bios-boot partition. There is a version of grub for UEFI booting but I think it is a bit experimental.

So GPT dual boot is complicated. GPT is only (possibly) necessary if your disk is bigger than 2TiB so if it were me I'd make it an MBR disk and use BIOS booting and save myself a lot of hassle. Install Windows first and then install Ubuntu. For greatest flexibility put all you Ubuntu partitions in an extended container.

---

### Post by YesWeCan on 2011-08-17
If you want to get Ubuntu booting again as is you should try this from 11.04 live CD:
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

If that doesn't work would you post the output of
sudo parted -l

---

### Post by srs5694 on 2011-08-18
> **YesWeCan said:**
> If your disk is 2TiB or less why not convert it back to MBR so you can greatly simplify your installations? This will erase your GPT header and your existing partitions too:
sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sdx
where x is the letter of your GPT disk

This is bad advice, for several reasons:


[list]
[*]It's unclear if the system has BIOS or UEFI firmware. If the latter, GPT is the preferred partitioning system, so erasing the GPT data will be pointless at best.
[*]The simple dd command provided wipes the primary GPT header, but ignores the backup GPT header. Leaving the backup GPT header in place creates the potential for confusion or even disaster, since some utilities *do* check for it, report its presence, and even give the option of using it even when an MBR partition table is present.
[*]If the disk is a true legal GPT disk, the specified dd command just damages the GPT data, but since the protective MBR and backup GPT data are left intact, the disk is technically still a GPT disk, and an OS or partitioning tool should be able to recognize the disk as such and use it. (Unfortunately, neither the Linux kernel nor libparted seems to do so, but those are bugs, IMHO. You should *not* rely on a bug for proper functioning of the system!)
[*]The specified dd command wipes the second sector on the disk, which will damage GRUB if the disk is actually an MBR disk rather than a GPT disk and if GRUB is installed. This could complicate recovery. I realize that marlon_smith says the disk is a GPT disk, but I've seen posts in the past where users are mistaken about such things, so I can't recommend a procedure that could go wrong if the user's assessment is incorrect.
[*]A typo in the dd command could wipe out the wrong data, causing unknown problems.
[/list]


More precise diagnostic information is required:


[list]
[*]The output (RESULTS.txt file) from the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) or at least the output of the "sudo parted -l" command. This will show us the partitions on the disk and some information on BIOS-style boot loaders, if any are installed. Please post this information between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to preserve legibility.
[*]Whether the computer uses a traditional BIOS or a new UEFI firmware. Unfortunately, this information isn't usually obvious, but it can usually be gleaned from the motherboard's manual. Therefore, the motherboard's make and model number is a useful stand-in.
[/list]


I'll refrain from offering more specific suggestions until you post back with this information. Also, if you understand the difference between UEFI booting and BIOS booting, it would be helpful if you could say which you prefer to use, and why. In many cases you will have a choice in the matter. BIOS booting is usually easier at the moment, especially in a dual-boot environment, but UEFI has some advantages, too.

---

### Post by YesWeCan on 2011-08-18
@srs5694
You seem to be missing the point. If you read the OP you will see that for this specific case my advice is good.
1) It is a GPT disk.
2) I suggest reusing the disk from scratch if it is <2TiB but not with GPT. The MBR partition table will get rewritten as part of the repartitioning. I do not trust the linux MBR formatting tools where GPT is concerned and it would be imprudent not to erase the GPT header before proceeding. Erasing the header as I prescribe is quick and effective.
4) For all practical purposes the residue backup GPT header at the last sector of the disk is irrelevant.

It may be that you are itching to express a view that my specific advice to the OP is not suitable in every case. If so then do say that. But a blanket statement that my advice is bad followed by irrelevant scenarios is not very good spirited of you.



[COLOR="Navy"]"This is bad advice, for several reasons:

It's unclear if the system has BIOS or UEFI firmware. If the latter, GPT is the preferred partitioning system, so erasing the GPT data will be pointless at best."[/COLOR]
What makes you assume the OP's mobo does not have BIOS support?

[COLOR="Navy"]"The simple dd command provided wipes the primary GPT header, but ignores the backup GPT header. Leaving the backup GPT header in place creates the potential for confusion or even disaster, since some utilities do check for it, report its presence, and even give the option of using it even when an MBR partition table is present."[/COLOR]
Exaggeration. A highly unlikely scenario and one that is certainly not likely to be disastrous.

[COLOR="Navy"]"If the disk is a true legal GPT disk, the specified dd command just damages the GPT data, but since the protective MBR and backup GPT data are left intact, the disk is technically still a GPT disk, and an OS or partitioning tool should be able to recognize the disk as such and use it. (Unfortunately, neither the Linux kernel nor libparted seems to do so, but those are bugs, IMHO. You should not rely on a bug for proper functioning of the system!)"[/COLOR]
No. The linux tools which the OP will be using will not recognize the disk as GPT if there is no GPT header. The OP will repartition the disk anyhow.

[COLOR="Navy"]"The specified dd command wipes the second sector on the disk, which will damage GRUB if the disk is actually an MBR disk rather than a GPT disk and if GRUB is installed. This could complicate recovery. I realize that marlon_smith says the disk is a GPT disk, but I've seen posts in the past where users are mistaken about such things, so I can't recommend a procedure that could go wrong if the user's assessment is incorrect.
A typo in the dd command could wipe out the wrong data, causing unknown problems."[/COLOR]
Sigh. My suggestion is to wipe the disk and start again. So Grub is irrelevant. Did you not read my next post where I ask for parted to be run for the case where the OP wants to try to recover what is there?

---

### Post by srs5694 on 2011-08-18
> **YesWeCan said:**
> @srs5694
You seem to be missing the point. If you read the OP you will see that for this specific case my advice is good.
1) It is a GPT disk.

Although marlon_smith claims that the disk is a GPT disk, he posted no evidence to support this claim. As I noted in my original post, I've seen incorrect claims about such things here before, so I'm unwilling to assume that the OP is correct on this score. No offense or disrespect is intended by this; it's just that experience has taught me that conclusions posted by people in this forum are not always reliable. Before offering a course of action that depends on such conclusions, I therefore prefer to have direct evidence to support those conclusions. The parted output (or RESULTS.txt file from the Boot Info Script) that both of us asked for will provide that evidence.

> 2) I suggest reusing the disk from scratch if it is <2TiB but not with GPT. The MBR partition table will get rewritten as part of the repartitioning. I do not trust the linux MBR formatting tools where GPT is concerned and it would be imprudent not to erase the GPT header before proceeding. Erasing the header as I prescribe is quick and effective.First, my own recommendation was to obtain more data before proceeding. With more data, a solution tailored to the actual problem, rather than to your or my or anybody else's *assumptions*, can be created.

Second, do you know of a case in which libparted has failed to erase GPT data when writing a new MBR header? If so, then please elaborate. If not, then doing a partial job of it is *not* an acceptable alternative! It's true that fdisk doesn't delete the GPT data, but if the solution ultimately to be created were to employ fdisk, some other method of properly wiping the GPT data could be used first. For instance, one could first use a libparted-based tool to create the MBR data or wipe the GPT data with gdisk or fixparts. These methods will all wipe the GPT data more completely than will the method you advocate.

> 4) For all practical purposes the residue backup GPT header at the last sector of the disk is irrelevant.***No it's not!!!!*** The GPT spec (in the UEFI 2.3.1 spec, p. 103) explicitly states:

> **GPT specification]If the primary GPT is corrupt, software *must check* the last LBA of the device to see if it has a valid GPT Header and point to a valid GPT Partition Entry Array. If it points to a valid GPT Partition Etnry Array, then the software *should restore the primary GPT* if allowed by platform policy settings (e.g. a platform may require a user to provide confirmation before restoring the table, or may allow the table to be restored automatically.[/quote]

(Emphasis added.) In other words, the GPT specification *explicitly states* that the backup data should be restored, optionally with user confirmation beforehand. The fact that the Linux kernel does *not* do what the GPT specification states it should do means that if you rely on this behavior, you're taking a grave risk. The developers might change it at any time to make the kernel more conformant with the standard. Furthermore, some OSes do conform more closely to the spec. I just checked, and both Windows and FreeBSD do give access to the GPT partitions when fed a disk that's been damaged in the way you advocate, although neither repairs the disk automatically.

Widening the scope of software to partitioning tools, libparted-based tools handle this type of damage very poorly by claiming that the disk has no recognized partition table said:**
> It may be that you are itching to express a view that my specific advice to the OP is not suitable in every case. If so then do say that. But a blanket statement that my advice is bad followed by irrelevant scenarios is not very good spirited of you.

The trouble is that this is not an academic exercise. Somebody's real hard disk is involved, and it's unclear from marlon_smith's post whether the existing partitions contain valuable data or what will be done with the disk going forward. Some of what you call "irrelevant scenarios" could come into play in the future. Even if the MBR is rewritten to be a valid MBR disk, if the backup GPT data remains intact and if gdisk or some other utility that's designed for recovering GPT data is run on the disk in the future, then a mistake in using these programs or a bug in the program could easily result in the destruction of MBR data. This scenario might not be very likely, but it's definitely possible, and I've seen posts from people who've trashed their disks because of less probable mistakes.

If you want to delete GPT data, ***do it right by deleting it ALL***. Using dd to wipe one sector of GPT data is doing less than half the job and creates the potential for problems in the future. The fact is that there are tools and procedures that will do it correctly, including libparted-based tools, gdisk, and more complex dd-based procedures (although these more complex dd procedures have their own risks, at least unless they're implemented in a script).

Given additional information, I might recommend deleting the GPT data in one of these more thorough ways. I didn't provide details because doing so would be jumping the gun -- it's first necessary to determine how the computer is booting (or is *not* booting) now and what's most appropriate for partitioning going forward.

> [COLOR=Navy]"This is bad advice, for several reasons:

It's unclear if the system has BIOS or UEFI firmware. If the latter, GPT is the preferred partitioning system, so erasing the GPT data will be pointless at best."[/COLOR]
What makes you assume the OP's mobo does not have BIOS support?What makes you think it does?

Although, to the best of my knowledge, all modern UEFI systems include a BIOS compatibility mode, I don't know for certain that they all do, and certainly some older EFI implementations lack this support. Unless and until marlon_smith posts hardware details, we can't know what hardware and firmware is involved.

Even if the computer has a modern UEFI implementation, marlon_smith may have reasons for wanting to boot in UEFI mode. If dual-booting with Windows, this will necessitate use of GPT.

> [COLOR=Navy]"The simple dd command provided wipes the primary GPT header, but ignores the backup GPT header. Leaving the backup GPT header in place creates the potential for confusion or even disaster, since some utilities do check for it, report its presence, and even give the option of using it even when an MBR partition table is present."[/COLOR]
Exaggeration. A highly unlikely scenario and one that is certainly not likely to be disastrous.No it's not. Ignoring the possibility is reckless, as detailed earlier (and in earlier threads you've read).

> [COLOR=Navy]"If the disk is a true legal GPT disk, the specified dd command just damages the GPT data, but since the protective MBR and backup GPT data are left intact, the disk is technically still a GPT disk, and an OS or partitioning tool should be able to recognize the disk as such and use it. (Unfortunately, neither the Linux kernel nor libparted seems to do so, but those are bugs, IMHO. You should not rely on a bug for proper functioning of the system!)"[/COLOR]
No. The linux tools which the OP will be using will not recognize the disk as GPT if there is no GPT header. The OP will repartition the disk anyhow.If marlon_smith is planning to install Windows as the next step, then the fact that Windows recognizes disks damaged in the way you're suggesting as valid GPT disks is highly relevant to the discussion. Likewise if he ends up using gdisk under Linux as a next step.

If the disk is converted to MBR format, then one of two things will be true:


[LIST]
[*]The conversion will be done with a tool that properly eradicates the old GPT data, in which case converting directly from the original starting point will work as well as will wiping the data partially and then doing the job properly. In fact, it might work better, since there's no telling how an unknown tool will react when asked to convert a damaged GPT disk to MBR format.
[*]The conversion will be done with a tool that does *not* properly eradicate the backup GPT data, in which case it will be left behind and pose the potential for problems in the future.
[/LIST]


Because of that second possibility, doing half a job of wiping the GPT data now creates a risk in the future.

> [COLOR=Navy]"The specified dd command wipes the second sector on the disk, which will damage GRUB if the disk is actually an MBR disk rather than a GPT disk and if GRUB is installed. This could complicate recovery. I realize that marlon_smith says the disk is a GPT disk, but I've seen posts in the past where users are mistaken about such things, so I can't recommend a procedure that could go wrong if the user's assessment is incorrect.
A typo in the dd command could wipe out the wrong data, causing unknown problems."[/COLOR]
Sigh. My suggestion is to wipe the disk and start again. So Grub is irrelevant. Did you not read my next post where I ask for parted to be run for the case where the OP wants to try to recover what is there?Granted, you did say that this would wipe the disk. Nonetheless, it deserve reiteration and clarification, particularly in case marlon_smith was mistaken about the disk being a GPT disk.

---

### Post by YesWeCan on 2011-08-18
@srs5694
Are you trying to win my friendship and influence me? If so, you need to radically change your tactics. 

Most of your long post is not conducive to comment.

> *Originally Posted by GPT specification*
**[COLOR="Red"]If the primary GPT is correct[/COLOR]**, software must check the last LBA of the device to see if it has a valid GPT Header and point to a valid GPT Partition Entry Array. If it points to a valid GPT Partition Etnry Array, then the software should restore the primary GPT if allowed by platform policy settings (e.g. a platform may require a user to provide confirmation before restoring the table, or may allow the table to be restored automatically.
Is this a transcription error?
Please post the preceding paragraphs of the spec. or preferably a link to the spec.

The hypothetical scenario you seem to be hysterical about is where some unspecified software that the OP may or may not use in the future will automatically look for a backup GPT header at the last sector of any disk and if it finds one there it will automatically, and without user permission, copy it to the sector 1+ area of the disk, regardless of what else is on the disk such as a valid MBR sector and partition table with non-GPT entries. And I presume you are also assuming it would wipe the valid MBR without even making a backup of it. And this on a disk that is not large enough to have to be GPT formatted.

I think if you are going to be consistent you should write a post to warn the OP of the onerous likelihood of a disaster caused by one of multiple, potential disk drive failures that could unexpectedly destroy all his valuable data and that you strong advise against using a mechanical disk and he should use an array of SSDs. And perhaps a post strongly advising him to take statins too. ;)


> Granted, you did say that this would wipe the disk. Nonetheless, it deserve reiteration and clarification, particularly in case marlon_smith was mistaken about the disk being a GPT disk.

Then why did you not write a polite post to the OP to emphasize this so he was in no doubt rather than starting an argument with me?

---

### Post by srs5694 on 2011-08-18
> **YesWeCan said:**
> @srs5694
Are you trying to win my friendship and influence me? If so, you need to radically change your tactics.

No, I'm not. I'm posting to try to provide useful information.

> Most of your long post is not conducive to comment.

In other words, my reasoning and arguments are correct.

> **srs5694][quote=GPT specification][COLOR=Red]If the primary GPT is correct[/COLOR], software *must check* the last LBA  of the device to see if it has a valid GPT Header and point to a valid  GPT Partition Entry Array. If it points to a valid GPT Partition Etnry  Array, then the software *should restore the primary GPT* if  allowed by platform policy settings (e.g. a platform may require a user  to provide confirmation before restoring the table, or may allow the  table to be restored automatically.[/quote]

Is this a transcription error?

Yes said:**
> Please post the preceding paragraphs of the spec. or preferably a link to the spec.

You can download the document from [here.](http://www.uefi.org/specs/agreement)

> The hypothetical scenario you seem to be hysterical about is where some unspecified software that the OP may or may not use in the future will automatically look for a backup GPT header at the last sector of any disk and if it finds one there it will automatically, and without user permission, copy it to the sector 1+ area of the disk, regardless of what else is on the disk such as a valid MBR sector and partition table with non-GPT entries. And I presume you are also assuming it would wipe the valid MBR without even making a backup of it. And this on a disk that is not large enough to have to be GPT formatted.

Please refrain from hyperbole; although that *is* a possible scenario, it's not a likely one, and I never claimed it was. I explicitly laid out others in my earlier post. (Perhaps they were what was "not conducive to comment...?") Try this as a scenario that's much more likely:


[list=1]
[*]Start with a GPT disk.
[*]Damage it in the way you recommend. According to you, the disk is effectively now blanked out and ready to be used as an MBR disk, so...
[*]Reboot the computer into the Windows 7 installer, using BIOS mode so as to use MBR on your "blank" disk. The result is as shown in the attachment: Windows disagrees with you that the disk is blank; it thinks it's a GPT disk and, if the computer is booted in BIOS mode, refuses to install.
[/list]


That's just one of many possible problems that could occur down the line. This one is quite likely; since the usual advice is to install Windows before Linux, the steps I've outlined are the logical way to proceed given your advice.

Another possibility would be to try to install Ubuntu first rather than Windows. The trouble with this is that, although the Ubuntu installer will see the disk as unpartitioned, it won't give you a choice of GPT vs. MBR. Since marlon_smith's disk seems to be at least 2 TB, and since the Ubuntu installer creates GPT by default on disks of that size, installing Ubuntu first will put marlon_smith back at square one, if his goal is to convert to MBR. (At least, I *think* it will -- I haven't tested this scenario.)

Thus, *if* the goal is to install a dual-boot Windows/Ubuntu system in BIOS mode using MBR on the disk, using dd as you suggest will result in a disk that can't be used for the task without further work. Of course, these problems can be overcome, but doing so requires going back and doing it *right* rather than doing less than half the job with dd. For instance:

```

sudo parted /dev/sda mklabel msdos

```

This command reliably erases the entire set of GPT data and creates a fresh MBR partition table on the disk. Windows should then install reliably (in BIOS mode). I'm not positive, but I *think* that Ubuntu will install on such a disk using MBR partitions. (There's a chance that it will convert to GPT if no partitions are defined, though. I've never tested this detail. To be positive, use fdisk or parted after creating the MBR to create at least one MBR partition.)

Of course, this is all going down just one path. Perhaps marlon_smith wants or needs to use UEFI boot mode or GPT for reasons that we don't know; or maybe the existing Ubuntu installation is heavily customized or has important personal data that must be recovered. That's why I asked for the information I did in the first post in this thread. Either using dd to damage the GPT data or parted to create a fresh MBR is inadvisable until more is known about the system.

---

### Post by YesWeCan on 2011-08-20
> **srs5694 said:**
> No, I'm not. I'm posting to try to provide useful information.
No, if you were just posting useful information then you would. Instead you are being alarmist and contrary and ill-mannered...

> In other words, my reasoning and arguments are correct.
...and arrogant.
Childish.

> Please refrain from hyperbole; although that *is* a possible scenario, it's not a likely one, and I never claimed it was.

The bottom line is that you have no arguments at all to support your hysterical claims of doom about leaving the backup GPT header in place. So until such time as you do, please stop taking pot-shots at my posts.



The "arguments" you just made are irrelevant to this thread.

> 

[LIST=1]
[*]Start with a GPT disk.
[*]Damage it in the way you recommend. According to you, the disk is effectively now blanked out and ready to be used as an MBR disk, so...
[*]Reboot the computer into the Windows 7 installer, using BIOS mode so as to use MBR on your "blank" disk. The result is as shown in the attachment: Windows disagrees with you that the disk is blank; it thinks it's a GPT disk and, if the computer is booted in BIOS mode, refuses to install.
[/LIST]


That's just one of many possible problems that could occur down the line. This one is quite likely; since the usual advice is to install Windows before Linux, the steps I've outlined are the logical way to proceed given your advice.
This example has nothing whatsoever to do with your fantasy future problems. It might cause an immediate problem that simply requires a disk reformat. Big deal.

> Another possibility would be to try to install Ubuntu first rather than Windows. The trouble with this is that, although the Ubuntu installer will see the disk as unpartitioned, it won't give you a choice of GPT vs. MBR. Since marlon_smith's disk seems to be at least 2 TB, and since the Ubuntu installer creates GPT by default on disks of that size, installing Ubuntu first will put marlon_smith back at square one, if his goal is to convert to MBR. (At least, I *think* it will -- I haven't tested this scenario.)
Irrelevant, this has nothing to do with your fantasy future problems .



Make a coherent argument or keep your criticisms to yourself.


There are four statements you could have made at the start of this thread without any recourse to attacking my post in any way and without causing me to have to waste time replying to you when I could be helping members with real issues, not fantasy ones.

1. You could have reiterated my statement that eliminating the GPT header would trash the disk.
2. You could have recommended that the disk be reformatted with a fresh MBR PT so that Windows would not object to installing, or more simply set count=2 and seek=0.
3. You could have informed the OP that if the disk is over 2TB and if he should choose "use entire disk" that Ubuntu installer would default to GPT without consulting him and so he would be advised to choose "something" else and set up the partitions manually.
4. Show how you would do it: use fixparts in this way <procedure> to eliminate all GPT information.


I should not have to be teaching you how to use netiquette here. It is wearing thin with me.

---

### Post by Cpierce on 2011-08-20
This should be easy. If you are only using Win7 and Ubuntu, then you shouldn't need a GPT disk, just write over it with a program like "wipe drive". Install windows, then install Ubuntu. If you are going to include OSx, then it needs to be GPT. At that point you need to run "gptsync" to sync MBR and GPT programs. I just went thru this making a triple boot of OSx, Ubuntu, and Win7.

---

### Post by srs5694 on 2011-08-20
YesWeCan,

There are many possible ways this can play out. Since marlon_smith hasn't posted back with details about what he wants to do, it's impossible to say with certainty what scenario is relevant to his specific problem. The two scenarios I posted in my post #8 (installing Windows or Ubuntu directly after damaging the GPT data) are extremely relevant to the sort of path you'd have marlon_smith pursue. Since you seem to believe that leftover GPT data can never cause a problem, try this, which begins with a valid GPT disk:

```
$ sudo parted /dev/sdd print
Model: USB Driver (scsi)
Disk /dev/sdd: 8015MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  4296MB  4295MB  ntfs         Microsoft basic data
 2      4296MB  8015MB  3719MB  xfs          Linux filesystem
```Note that's a GPT disk with two partitions. Now damage the disk in the way you recommend....

```
$ sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sdd
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00401078 s, 128 kB/s
```This is where your advice ended. My post #8 suggested a couple of possible paths that would lead to problems, or at least a need to go back and do it right. Here's another possible path: Use fdisk to delete the 0xEE protective partitions and create new partitions in its place. In this example, I'll create just one, for simplicity's sake....

```
$ sudo fdisk /dev/sdd

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Command (m for help): p

Disk /dev/sdd: 8015 MB, 8015314944 bytes
65 heads, 36 sectors/track, 6690 cylinders, total 15654912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1    15654911     7827455+  ee  GPT

Command (m for help): d
Selected partition 1

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4, default 1): 1
First sector (2048-15654911, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-15654911, default 15654911): 
Using default value 15654911

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

At this point, the disk is technically a legal MBR disk, but the GPT backup data remain at the end of the disk. To verify the disk's MBR status, you can check it with parted....

```
$ sudo parted /dev/sdd print
Model: USB Driver (scsi)
Disk /dev/sdd: 8015MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8015MB  8014MB  primary  ntfs

```Note that it's identified it as having an "msdos" (MBR) partition table and one partition.

Now, suppose the disk is used for a while, and down the line a utility that's intended to recover damaged GPT disks is used on the disk. This is an inappropriate thing to do, but somebody who doesn't understand partitions very well might do this, and tell the tool to do inappropriate things because of a misunderstanding, a faulty memory, bad advice on a Web forum, or whatever....

```
$ sudo gdisk /dev/sdd
GPT fdisk (gdisk) version 0.7.2

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 2

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT).
The operation has completed successfully.
```At this point, the disk has now reverted to its original GPT state, with the original two partitions....

```
$ sudo parted /dev/sdd print
Model: USB Driver (scsi)
Disk /dev/sdd: 8015MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  4296MB  4295MB  ntfs         Microsoft basic data
 2      4296MB  8015MB  3719MB  xfs          Linux filesystem

```This example shows intact (or at least recognizable) NTFS and XFS filesystems in the partitions, but if new filesystems were created and used, that probably wouldn't be the case in a real-life scenario. At this point, the correct MBR data would be gone, and the only way to recover the data would be with TestDisk or a similar utility, or by guessing correctly at the placement and sizes of the disk's partitions. TestDisk doesn't always work correctly, though, and even if it did there's a possibility that the conversion back to GPT would damage important data on the disk. GRUB 2's post-MBR code would be overwritten, for instance, and there's a possibility (albeit a very slim one) that the GPT backup partition data would overwrite data at the end of the last partition on the disk.

I'm perfectly willing to grant that getting to this state requires a series of mistakes or just plain bad luck. The problem can be avoided in a number of ways, such as:


[LIST=1]
[*]Completely erasing the GPT data in the beginning
[*]Using partitioning tools or other utilities between the initial damage to the GPT data and the use of the GPT recovery tool that erases the GPT backup data
[*]Not using the GPT recovery tool or using it appropriately rather than inappropriately
[/LIST]


Since this thread is supposed to be about advising marlon_smith about what to do *now*, the only one of these three options that's relevant is #1. As I've posted before, it's not difficult to use parted to completely eliminate the GPT data from the start. I posted the command in post #8 in this thread, and it's even shorter than the dd command you recommended. Once the backup GPT data are removed from the picture, there's no chance of this specific scenario coming to pass. The much more likely problems I described in my post #8 will also be bypassed by using an appropriate command at the start (with the caveat that I'm not 100% positive how the Ubuntu installer will react to an MBR disk with no partitions if the disk is over ~1 TiB in size).

You can dismiss my scenarios as a "fantasy" or "hysterical" if you like, but the fact is that this forum is filled with threads about problems that occur only because of a series of software bugs or user mistakes that are at least as improbable as the sequence I've just described. There is *no justification* for knowingly leaving such a configuration in place when you know of a way to avoid it that's at least as easy as the method that makes it possible.

Marlon_smith,

I'm sorry your thread has degenerated into this unpleasant and tedious exchange. I hope that you may have at least learned a thing or two from it. If you need more specific advice about what to do, please post the information I requested earlier, in this thread's post #4; or PM it to me if you prefer.

---

