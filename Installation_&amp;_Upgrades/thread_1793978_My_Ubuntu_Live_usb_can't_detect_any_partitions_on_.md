---
title: "My Ubuntu Live usb can't detect any partitions on the HDD"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by ntnkj on 2011-06-30
I installed Windows 7, shredded the main partition for about 40 gigs (I made them unallocated), rebooted, Win7 works perfectly. THEN I tried booting Linux from a Live usb, and it doesn't recognize any partitions, it sees the whole HDD as unallocated space.
This is the result of "sudo fdisk -l" done from the Live session: (I just copied the HDD info, not the usb)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc1cdd547

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       33692   270527488    7  HPFS/NTFS



PLEASE help, I tried some workarounds, but no luck.

Btw, I am something of a noob, this is my first post, so be gentle :)

---

### Post by dino99 on 2011-06-30
follow this little help to install

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by gordintoronto on 2011-06-30
sda1 and sda2 are partitions, so you can see that Linux recognizes the partitions just fine.

What does this mean: "shredded the main partition for about 40 gigs (I made them unallocated)"?

---

### Post by ntnkj on 2011-06-30
It means that I used MiniTools Partition wizard to shrink the second (the biggest) partition, I reduced it by 40 GB and converted those 40 GB to unallocated space, in order to install Ubuntu there

---

### Post by ntnkj on 2011-06-30
> **dino99 said:**
> follow this little help to install

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)


GParted doesn't recognize any partitions also.
I CAN mount the HDD in Ubuntu live, AND view files
BUT Gparted and Ubuntu installer don't see the partitions, they only see unallocated space, an empty hard drive.

---

### Post by ntnkj on 2011-06-30
I guess it could be a problem with the partition table, I tried fixing it with Testdisk, ended up removing Win7 booter, I barely recovered it

---

### Post by YesWeCan on 2011-06-30
Fascinating. Would you mind posting the window of Disk Utility you when you have selected the HD?

---

### Post by ntnkj on 2011-06-30
> **YesWeCan said:**
> Fascinating. Would you mind posting the window of Disk Utility you when you have selected the HD?

Here is the screenshot, no problems there, only Gparted and the installer don't see it

---

### Post by YesWeCan on 2011-06-30
Bizarre. Windows, fdisk, GParted, the Ubuntu installer and Disk Utility all use the partition table to identify the contents. But GParted and the installer think the disk is unformatted?

---

### Post by ntnkj on 2011-06-30
> **YesWeCan said:**
> Bizarre. Windows, fdisk, GParted, the Ubuntu installer and Disk Utility all use the partition table to identify the contents. But GParted and the installer think the disk is unformatted?

Gparted:

---

### Post by ntnkj on 2011-06-30
And the installer doesn't offer to install Ubuntu side-by-side with Win7, it's format HDD or Other.
I go to other, and I see an empty HDD

---

### Post by YesWeCan on 2011-06-30
Is this the 11.04 installer?
Have you got an earlier Ubuntu installer you could try? Just to see if its partitioner has its glasses on?

---

### Post by ntnkj on 2011-06-30
> **YesWeCan said:**
> Is this the 11.04 installer?
Have you got an earlier Ubuntu installer you could try? Just to see if its partitioner has its glasses on?

It is 11.04, I don't have an earlier installer, but I'll make one and give it a shot tomorrow morning (it's 11pm where I am)
Thanks

---

### Post by ntnkj on 2011-06-30
I'm having a problem finding an ISO for older Ubuntu Live installers, all the links I've found are dead/obsolete

---

### Post by westie457 on 2011-06-30
> **ntnkj said:**
> I'm having a problem finding an ISO for older Ubuntu Live installers, all the links I've found are dead/obsolete

hi take a look at this link:[http://releases.ubuntu.com/]("http://releases.ubuntu.com/") for all the available releases

---

### Post by ntnkj on 2011-06-30
> **westie457 said:**
> hi take a look at this link:[http://releases.ubuntu.com/]("http://releases.ubuntu.com/") for all the available releases
Thanks!

---

### Post by oldfred on 2011-06-30
Even a new windows install in NTFS may need chkdsk especially after a resize.

Gparted will not see a drive that is NTFS that needs chkdsk, as it does not know problem and does not want to make it worse.

Have you tried chkdsk on your NTFS partitions. You have to rerun until there are no errors as it does not fix everything on one pass.

chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by ntnkj on 2011-06-30
1) I tried the older live cd, specifically 9.10, no success.

2) I will try the chkdsk, but it's a brand new HDD, with a clean Win7 installation. I'll try it anyway, I'm getting desperate...

Thanks, people!

---

### Post by ntnkj on 2011-07-01
No luck with chkdsk... :(

No errors in the disk, no bad sectors, nothing

---

### Post by oldfred on 2011-07-01
From liveCD post this, just to see partition table in detail:

```
sudo fdisk -lu
```

---

### Post by ntnkj on 2011-07-01
> **oldfred said:**
> From liveCD post this, just to see partition table in detail:

```
sudo fdisk -lu
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc1cdd547

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   541261823   270527488    7  HPFS/NTFS

---

### Post by oldfred on 2011-07-01
Nothing there, that I can see. Did your partitioning tool convert from basic to dynamic? Or perhaps some BIOS setting. I would review BIOS settings to see if something is non-standard. Generally Linux works better with some odd BIOS than Windows.

---

### Post by ntnkj on 2011-07-01
> **oldfred said:**
> Nothing there, that I can see. Did your partitioning tool convert from basic to dynamic? Or perhaps some BIOS setting. I would review BIOS settings to see if something is non-standard. Generally Linux works better with some odd BIOS than Windows.
Hmm.. I'm not sure about basic/dynamic. I didn't ask for it, anyway, I don't know what it means, actually :D

And I think my BIOS is fine, I combed through the options, and didn't see anything fishy, you might be more specific if possible?
T

---

### Post by YesWeCan on 2011-07-01
A long shot: was this disk ever part of a Windows RAID set up? Or any other unusual previous use?

---

### Post by oldfred on 2011-07-01
These are comments posted by others that only may be related. You have to review to see if they apply. These were more related to booting, not gparted issues.

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

---

### Post by ntnkj on 2011-07-01
Re: My Ubuntu Live usb can't detect any partitions on the HDD
A long shot: was this disk ever part of a Windows RAID set up? Or any other unusual previous use?

No

---

### Post by ntnkj on 2011-07-01
> **oldfred said:**
> These are comments posted by others that only may be related. You have to review to see if they apply. These were more related to booting, not gparted issues.

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.
I checked the BIOS settings, it was already set to AHCI, it offers either AHCI or IDE, no SATA, no compatibility mode. I don't know how to set the AUTO/LDA thing, I don't even know what it means, sorry
And I also don't know how to set disk access to "Large" 

And yeah, thanks for helping!

---

### Post by oldfred on 2011-07-01
Different BIOSs call it different things but it is LBA or large block allocation. Actually the standard for years, so the old IDE only setting should not be used anymore, but is for compatibility with some old drives.

---

### Post by ntnkj on 2011-07-02
UPDATE:

I tried installing WUBI in Win7, and everything worked fine until I rebooted and chose to boot Ubuntu. It almost finished the installation, and then I got error message:

"No root file system is detected.
Please correct this from the partitioning menu"

and I wasn't able to do anything else but reboot.

---

### Post by ntnkj on 2011-07-02
> **oldfred said:**
> Different BIOSs call it different things but it is LBA or large block allocation. Actually the standard for years, so the old IDE only setting should not be used anymore, but is for compatibility with some old drives.
I updated my BIOS, absolutely no options concerning LBA in it. I found this online, though:

"A Phoenix BIOS generally does not have setup options for Large and
LBA but Phoenix has traditionally used Large (bit shifting) CHS
translation."

---

### Post by oldfred on 2011-07-02
The error message you got was for a standard install with partitions, not wubi. But something is not correct on your wubi install as it is Ubuntu set up to look like a normal install but just in a file in your windows system. I do not know wubi enough to help.

---

### Post by ntnkj on 2011-07-02
> **oldfred said:**
> The error message you got was for a standard install with partitions, not wubi. But something is not correct on your wubi install as it is Ubuntu set up to look like a normal install but just in a file in your windows system. I do not know wubi enough to help.
No, it wasn't a standard installation, it's a Wubu installation under Windows. It's a standard misconception that WUBI is a virtual machine, but actually it's not. It installs Ubunutu as a stand-alone system, but inside a Windows partition, and it is governed by Windows (When you boot, Win7 booter {and not grub} asks you if you want to boot into Win or Ubuntu)

---

### Post by Rubi1200 on 2011-07-02
Hi ntnkj,
oldfred asked me to comment on your situation and help out.

Without going over each post again, here is a basic summary of the situation:

various tools such as fdisk, GParted, and Disk Utility are reporting conflicting results regarding the state of your partitions.

In most cases, the GParted screenshot would suggest something like stray GPT data, old RAID metadata etc. left over on the disk.

You have still not answered certain questions that were asked and before you proceed with anything please do the following:

1. take a screenshot of how the Windows Disk Management utility sees your drives and post it here

2. boot the computer with a LiveCD and run the following command:
```
sudo dmraid -r -E /dev/sda
```
This will check the drive for RAID metadata. At this point, just let us know what it reports rather than removing the metadata.

The error message you got with the Wubi install is, in fact, consistent with your situation. Something, we still need to determine what, is causing these various tools problems with seeing your drive.

Once you have posted the information I asked for, we can proceed.

Thanks.

---

### Post by ntnkj on 2011-07-02
> **Rubi1200 said:**
> Hi ntnkj,
oldfred asked me to comment on your situation and help out.

Without going over each post again, here is a basic summary of the situation:

various tools such as fdisk, GParted, and Disk Utility are reporting conflicting results regarding the state of your partitions.

In most cases, the GParted screenshot would suggest something like stray GPT data, old RAID metadata etc. left over on the disk.

You have still not answered certain questions that were asked and before you proceed with anything please do the following:

1. take a screenshot of how the Windows Disk Management utility sees your drives and post it here

2. boot the computer with a LiveCD and run the following command:
```
sudo dmraid -r -E /dev/sda
```
This will check the drive for RAID metadata. At this point, just let us know what it reports rather than removing the metadata.

The error message you got with the Wubi install is, in fact, consistent with your situation. Something, we still need to determine what, is causing these various tools problems with seeing your drive.

Once you have posted the information I asked for, we can proceed.

Thanks.

```
ubuntu@ubuntu:~$ sudo dmraid -r -E /dev/sda
no raid disks and with names: "/dev/sda"
```

I'll post the windows info in a minute

---

### Post by ntnkj on 2011-07-02
Here's the Win7 Disk management info

---

### Post by Rubi1200 on 2011-07-02
Well, this is an odd situation!

Two more suggestions and I hope either oldfred or YesWeCan have some other ideas.

1. check your SATA cable, maybe something came loose or there is another hardware problem that went unnoticed

2. this link describes and has solutions for the GParted issue, perhaps something there can help:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by Quackers on 2011-07-02
Your system isn't using SATA3 is it?

---

### Post by ntnkj on 2011-07-02
> **Quackers said:**
> Your system isn't using SATA3 is it?
No, it's SATA 2 (Sata-300)

---

### Post by oldfred on 2011-07-02
Well fdisk sees the drive and your two partitions.

You can use command line fdisk to create partitions. I have not used fdisk to create partitions for years and then it was the windows version. 

Instructions here:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

If you have allocated 40GB, I would create an extended partition first and all the rest as logical in the extended. Put in a 12GB  partition to use as / (root), a 24GB partition as /home and a 2GB partition to use as swap. If not enough due to rounding reduce /home. You should be able to format as part of the install. You have to use manual install or "Something Else" in 11.04 to choose existing partitions.

---

### Post by YesWeCan on 2011-07-02
This is turning in to quite a group effort. I like to see what is actually going on on the disk. Also, let's get another opinion from sfdisk. What are the outputs of:

sudo sfdisk -l -uS

sudo dd if=/dev/sda bs=512 count=1 | hexdump -C

---

### Post by ntnkj on 2011-07-03
> **YesWeCan said:**
> This is turning in to quite a group effort. I like to see what is actually going on on the disk. Also, let's get another opinion from sfdisk. What are the outputs of:

sudo sfdisk -l -uS

sudo dd if=/dev/sda bs=512 count=1 | hexdump -C

```
ubuntu@ubuntu:~$ sudo sfdisk -l -uS

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS
/dev/sda2        206848 541261823  541054976   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
```

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=512 count=1 | hexdump -C
00000000  fa 33 c0 8e d0 bc 00 7c  8b f4 50 07 50 1f fb fc  |.3.....|..P.P...|
00000010  bf 00 06 b9 00 01 f2 a5  ea 1d 06 00 00 be be 07  |................|
00000020  b3 04 80 3c 80 74 0e 80  3c 00 75 1c 83 c6 10 fe  |...<.t..<.u.....|
00000030  cb 75 ef cd 18 8b 14 8b  4c 02 8b ee 83 c6 10 fe  |.u......L.......|
00000040  cb 74 1a 80 3c 00 74 f4  be f8 06 ac 3c 00 74 0b  |.t..<.t.....<.t.|
00000050  56 bb 07 00 b4 0e cd 10  5e eb f0 eb fe bf 05 00  |V.......^.......|
00000060  60 6a 00 6a 00 ff 76 0a  ff 76 08 6a 00 68 00 7c  |`j.j..v..v.j.h.||
00000070  6a 01 6a 10 b4 42 b2 80  8b f4 cd 13 61 61 73 0c  |j.j..B......aas.|
00000080  33 c0 cd 13 4f 75 d9 be  f8 06 eb bf be f8 06 bf  |3...Ou..........|
00000090  fe 7d 81 3d 55 aa 75 b3  bf 52 7c 81 3d 46 41 75  |.}.=U.u..R|.=FAu|
000000a0  07 47 47 80 3d 54 74 11  bf 03 7c 81 3d 4e 54 75  |.GG.=Tt...|.=NTu|
000000b0  40 47 47 81 3d 46 53 75  38 60 b4 08 b2 80 cd 13  |@GG.=FSu8`......|
000000c0  bf 1a 7c fe c6 8a d6 32  f6 89 15 4f 4f 83 e1 3f  |..|....2...OO..?|
000000d0  89 0d 61 60 6a 00 6a 00  ff 76 0a ff 76 08 6a 00  |..a`j.j..v..v.j.|
000000e0  68 00 7c 6a 01 6a 10 b4  43 b2 80 8b f4 cd 13 61  |h.|j.j..C......a|
000000f0  61 8b f5 ea 00 7c 00 00  45 72 72 6f 72 21 00 44  |a....|..Error!.D|
00000100  32 31 30 41 36 31 35 2d  41 43 46 44 2d 34 31 34  |210A615-ACFD-414|
00000110  61 2d 42 44 46 31 2d 46  43 39 46 32 41 38 35 46  |a-BDF1-FC9F2A85F|
00000120  30 37 36 00 00 00 00 00  00 00 00 00 00 00 00 00  |076.............|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  47 d5 cd c1 00 00 80 20  |........G...... |
000001c0  21 00 07 df 13 0c 00 08  00 00 00 20 03 00 00 df  |!.......... ....|
000001d0  14 0c 07 fe ff ff 00 28  03 00 00 d8 3f 20 00 00  |.......(....? ..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0007216 s, 710 kB/s
00000200
```

---

### Post by ntnkj on 2011-07-03
So, I guess it is a GPT problem after all?

---

### Post by ntnkj on 2011-07-03
I see that Windows Disk manager utility has an option to convert a drive from GPT to MBR, but it has to format the drive. Should I backup my data and do that? I mean,
-is it probable that would fix my problem?
-is it necessary to format the drive?

---

### Post by Rubi1200 on 2011-07-03
I would wait until YesWeCan and oldfred comment, but if you go back a couple of posts, I linked to a site which explains the problem and offers a solution in the form of a utility called Fixparts that does not involve reformatting anything.

The only thing I am concerned about is that fdisk did not report anything like this, which it usually would.

I am also going to ask srs5694, author of the utility I mentioned, to comment on this so please be patient.

---

### Post by maclenin on 2011-07-03
[THIS...

> I am also going to ask srs5694, author of the utility I mentioned, to comment on this so please be patient.
...is why I love [this place]("http://ubuntuforums.org")...sorry for the interjection....]

---

### Post by YesWeCan on 2011-07-03
> **ntnkj said:**
> I see that Windows Disk manager utility has an option to convert a drive from GPT to MBR, but it has to format the drive. Should I backup my data and do that? I mean,
-is it probable that would fix my problem?
-is it necessary to format the drive?
Aaaah. So this is what is going on. You have a disk with a hybrid combo of GPT and MBR. Which is sort of illegal. This explains why the Windows partition starts at sector 2048 instead of 63. However, this is not really a good excuse for the bizarre behaviour of GParted and the Ubuntu installer.

[rant]I do wish apps would stop corrupting the MBR sectors of disks! That includes Grub.[/rant]

Windows (ordinary versions) does not support being installed on GPT disks. So how did you end up with this arrangement?

Since your disk has some sort of MBR boot code (which is why Windows boots at all) I think you can just delete the GPT header that follows it and the disk will then appear to be MBR only. I haven't used GPT much but I think this ought to make everything report properly.

[COLOR=Navy]sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda[/COLOR]

---

### Post by YesWeCan on 2011-07-03
> **Rubi1200 said:**
> The only thing I am concerned about is that fdisk did not report anything like this, which it usually would.
Good point. My theory is that fdisk doesn't support GPT at all so didn't even look for a GPT header in sector 1. Instead it looked for a MBR PT in sector 0 and found one and thought all was normal.
GParted must check for a GPT header and then ignore the sector 0 PT and just report the disk as blank. Which is totally unacceptable. As a minimum it ought to flag it as a GPT disk and if it was clever it would check for an MBR PT and report if it contains conflicting partition info.
Fortunately, sfdisk  checks for GPT header and reports it and also the MBR PT.
Disk Utility seems to just work off the MBR PT. So I guess it doesn't look for a GPT header at all.

This is why applications SHOULD NOT MESS WITH THE MBR sector! The GPT standard specifies a special "protective" MBR sector that is designed to show legacy MBR bios' that the disk is in fact full so that the disk is not mistaken for empty and then liable for reformatting.

IMO Grub should never have been designed to mess with the MBR sector in the old system and definitely has no excuse whatsoever to do so in the GPT system.

---

### Post by ntnkj on 2011-07-03
sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda

I'll try that when I get home, and tell you if it did the trick

THANKS, EVERYONE!!

Ubuntu community ftw!
:D

---

### Post by oldfred on 2011-07-03
I always am leery on suggesting dd as its nickname is Data Destroyer. It is very powerful and as such very dangerous. One typo and big issues.

Does not gpt also keep a backup at the end of the drive also? Which may or may not be there.

I might suggest srs5694 fixparts programs as he wrote gdisk to create gpt partitions and understands them about as well as anyone.

Backup partition table first:
sudo sfdisk -d /dev/sda > parts.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by YesWeCan on 2011-07-03
@oldfred
I'm assuming ntnkj wants to end up with an MBR PT disk rather than a GPT disk, otherwise Windows won't be bootable. The disk is only 320GB so MBR PT will span it.

I think GPT is needed if the disk is bigger than 2TiB but it doesn't support (unless hacked) conventional MBR PT booting. I believe a freshly formatted GPT has no MBR code at all and a protective MBR PT with a single entry of type "EE" which spans the whole disk starting at sector 1 and up to a maximum of 2TiB (the max size an MBR PT can describe).

---

### Post by YesWeCan on 2011-07-03
> **oldfred said:**
> Does not gpt also keep a backup at the end of the drive also? Which may or may not be there.
Good point. So if the first GPT header (sector 1) deletion is not enough then the last sector of the disk needs erasing too:
[COLOR=Navy]sudo dd if=/dev/zero bs=512 count=1 seek=625142447 of=/dev/sda[/COLOR]

(based on the last sector number from post #21, which is the total sectors 625142448 minus 1 as the sector count starts at 0).

I suppose this should be done anyhow, as a precaution, in case some intelligent tool checks for the GPT header backup and makes a decision to restore it to sector 1 - is this ever likely to happen? I don't know.

---

### Post by srs5694 on 2011-07-03
> **ntnkj said:**
> ```
ubuntu@ubuntu:~$ sudo sfdisk -l -uS

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS
/dev/sda2        206848 541261823  541054976   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
```

*Don't* use dd. Chances are YesWeCan's suggestion won't work, since it's an incomplete solution; and as oldfred states, it's easy to get it wrong and make things worse. Also as oldfred suggests, my [FixParts](http://www.rodsbooks.com/fixparts/) program should fix the problem.

Allow me to back up and explain what happened: Your disk was probably a GUID Partition Table (GPT) disk at some point in its life -- maybe it was used in a Mac or you were experimenting with GPT partitioning on your PC. GPT data structures are larger than those of the more common Master Boot Record (MBR). In particular, GPT occupies about 34 sectors at the start of the disk (rather than MBR's 1 sector) and another 33 sectors at the end of the disk (rather than MBR's no sectors). This in and of itself is fine; it's just how GPT was designed. The problem is that if you repartition the disk with certain MBR utilities, such as the Windows installer or Linux's fdisk, those utilities will replace the "protective MBR," which is part of GPT, but they will *not* erase or replace the remaining 66 sectors of GPT data. If you read the GPT spec (part of the UEFI 2.x spec), you'll see that in this situation, the disk is officially a legal MBR disk, *not* a GPT disk. Most libparted-based utilities, however, including GParted and the Ubuntu installer, get confused by this situation, and tend to report the disk as being empty when in fact it's not. This is a bug in libparted (or perhaps in the libparted-based tools but outside of the library; I haven't tried to track down where in the code the bug is), but it is triggered by a condition that is, although technically valid, a little bit ambiguous -- such a situation *could* arise from an errant disk utility, and it *could* be that the GPT data should have been used.

In any event, it's pretty clear that in your case the MBR data are valid, so you want to wipe the old GPT data. That's one of the things that FixParts does; it wipes the two sectors that confuse libparted-based tools. Note that YesWeCan's dd command wipes just one of those two sectors. The command could be adjusted, of course, but that just increases the risk of a typo causing further problems.

> **YesWeCan]You have a disk with a hybrid combo of GPT and MBR. Which is sort of  illegal. This explains why the Windows partition starts at sector 2048  instead of 63.[/quote]

The situation is technically legal, but it does cause some libparted-based tools to flake out. This has *nothing* to do with the Windows partition starting at sector 2048. Since Windows Vista, Microsoft has shifted to a policy of starting new partitions on 1 MiB (2048-sector) boundaries. Linux tools have shifted to use the same policy in the last year or so. This is true on both MBR and GPT disks, and it's because of the fact that many new technologies (Advanced Format disks, SSDs, and some types of RAID arrays) suffer performance problems if partitions are not aligned on 8-sector or larger power-of-2 multiples, up to at least 512 sectors. For more information, see [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote on the topic a year and a half ago, or try a Web search on keywords like "Advanced Format" and "alignment."

[quote=YesWeCan][rant]I do wish apps would stop corrupting the MBR sectors of disks! That includes Grub.[/rant][/quote]

This problem was not caused by a "corruption" of MBR said:**
> The only thing I am concerned about is that fdisk did not report anything like this, which it usually would.

My suspicion is that ntnkj didn't cut-and-paste the whole fdisk output in [post #21.](http://ubuntuforums.org/showpost.php?p=11002085&postcount=21) You'll note the fdisk command itself is missing from that post. I've seen people do this before. This is an illustration of why it's critical that people quote the *entire output* of a program when they're asked to post a program's output (unless they're also explicitly told to trim it in some way). FWIW, I saw this thread a day ago, and if post #21 had included the GPT warning that fdisk almost certainly did produce, I would have posted sooner.

> **YesWeCan]My theory is that fdisk doesn't support GPT at all so didn't even look for a GPT header in sector 1.[/quote]

For old enough versions of fdisk, this is true, but recent versions (certainly everything I've used in the last two years, and maybe longer) do look for GPT data. For instance:

```
$ **sudo fdisk -l /dev/sda**

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

```

[quote=YesWeCan]GParted must check for a GPT header and then ignore the sector 0 PT and  just report the disk as blank. Which is totally unacceptable. As a  minimum it ought to flag it as a GPT disk and if it was clever it would  check for an MBR PT and report if it contains conflicting partition  info.[/quote]

I'm not sure of the exact nature of the GParted bug, but you're correct that it is a bug and that it's unacceptable. Your suggestion to flag such ambiguous disks as GPT is incorrect, though, since the GPT spec (at least in UEFI 2.x said:**
> GPT fdisk[/url] do enable recovery from such situations. Arguably GParted should, too, but absent a human being's input, the proper behavior is to treat such disks as MBR disks.)

[quote=YesWeCan]Disk Utility seems to just work off the MBR PT. So I guess it doesn't look for a GPT header at all.

No, Palimpsest Disk Utility works with both partition table types. Although it's also based on libparted, its developers seem to have patched or worked around the bug (or maybe the bug is just common on libparted-based programs but isn't actually part of libparted). Palimpsest seems to adhere closely to the GPT spec and ignores the GPT data when the MBR doesn't include a protective partition. If you feed Palimpsest a valid GPT disk, though, it will recognize it as such.

FWIW, I've seen reports that some earlier versions of Palimpsest favored the GPT data over the MBR data in this situation, which can make things even more confusing. I don't know exactly when its behavior changed.

[quote=YesWeCan]This is why applications SHOULD NOT MESS WITH THE MBR sector! The GPT  standard specifies a special "protective" MBR sector that is designed to  show legacy MBR bios' that the disk is in fact full so that the disk is  not mistaken for empty and then liable for reformatting.

IMO Grub should never have been designed to mess with the MBR sector in  the old system and definitely has no excuse whatsoever to do so in the  GPT system.[/quote]

Your ire is misplaced. It was almost certainly a disk partitioning tool that "messed with" the MBR, and that's the *job* of disk partitioning tools. (My guess is it was the Windows installer that replaced the protective MBR with a conventional MBR, but I'm not certain of that.) GRUB had nothing to do with it. GRUB doesn't normally adjust partition table entries. (One exception is if you use its options to hide or unhide partitions at boot time; but whatever you think of the wisdom of using such options, AFAIK they can't produce this type of problem and I didn't notice mention of their being in use in this thread.)

---

### Post by srs5694 on 2011-07-03
> **YesWeCan said:**
> I think GPT is needed if the disk is bigger than 2TiB but it doesn't support (unless hacked) conventional MBR PT booting. I believe a freshly formatted GPT has no MBR code at all and a protective MBR PT with a single entry of type "EE" which spans the whole disk starting at sector 1 and up to a maximum of 2TiB (the max size an MBR PT can describe).

This is mostly correct, but:


[list]
[*]The MBR size limit is 2 TiB if the disk has a logical sector size of 512 bytes. On disks with larger sector sizes, the limit is higher. AFAIK, such disks are extremely rare or non-existent, at least at sizes higher than 2 TiB, although some hardware RAID controllers may enable adjusting the logical sector size.
[*]Technically, it's possible to create an MBR disk that's up to just under 4 TiB by having everything after the 2 TiB mark (and at least one sector before it) be in a single 2 TiB or smaller partition. This is because the LBA addressing for MBR consists of a partition start sector number and a length, so you can start a partition at just under the 2 TiB limit and have it be 2 TiB in size. I don't recommend doing this, though, since many OSes have problems with such disks and since the OSes that can handle it can also handle GPT, with the exception that Windows Vista and 7 can't boot from a GPT disk except on a UEFI-based computer. See [here](http://www.rodsbooks.com/gdisk/workarounds.html) for more on this topic.
[*]Thinking about "conventional MBR PT booting" on GPT disks is putting it in the wrong terms. It's the computer's *firmware* (the BIOS on most computers) that determines how the computer boots. In a BIOS system, the BIOS loads sector 0 of the hard disk (the MBR) and executes code it contains. In principle, that's basically it, although I know of cases where the BIOS does seem to interpret the partition table and does odd things in some situations -- see [here](http://www.rodsbooks.com/gdisk/bios.html) for details. The point of this is that it is possible to boot a GPT disk on a BIOS-based computer; you just need a GPT-capable boot loader (such as GRUB 2, GPT-capable versions of GRUB Legacy, the GPT loader from SYSLINUX, Chameleon, etc.). I wouldn't call this "hacking" the GPT, since GPT data structures aren't modified in any odd way. As far as I recall, the GPT spec does not specify that the protective MBR's code area must be empty, although it does specify that UEFI firmware ignores the code area.
[/list]

---

### Post by oldfred on 2011-07-03
Something has changed, I am still on Maverick 10.10 but now fdisk does not show gpt:

My current sdb is gpt and this is was the fdisk last time I ran boot script:

```
Drive: sdb _____________________________________________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   312,581,807   312,581,807  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34        16,064        16,031 BIOS Boot partition
/dev/sdb2          16,065    51,215,219    51,199,155 Data partition (Windows/Linux)
/dev/sdb3      51,215,220    57,352,049     6,136,830 Swap partition (Linux)
/dev/sdb4      57,352,050   312,576,704   255,224,655 Data partition (Windows/Linux)

```But this is what I now get. Same version of fdisk but did an unlying library change?

```
fred@fred-MavericDT:~$ sudo fdisk -l /dev/sdb
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.


Disk /dev/sdb: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1           1        8001   83  Linux 
/dev/sdb2               2        3188    25591545   83  Linux 
/dev/sdb3            3189        3570     3060382   82  Linux Swap / Solaris 
/dev/sdb4            3571       19457   127604295   83  Linux 
fred@fred-MavericDT:~$ 
```

---

### Post by srs5694 on 2011-07-03
oldfred,

You're now running GNU fdisk, rather than the more common (on Linux) fdisk from util-linux or util-linux-ng. It's not clear what command you used to produce your first output example, but if it wasn't the exact same command you used for the second one, that could explain the differences in output.

I strongly recommend you uninstall the gnu-fdisk package from your computer; it's based on libparted and so is subject to the same bugs and limitations as parted, GParted, Palimpsest, the Ubuntu installer, etc. In other words, all your partitioning eggs are now in that one libparted basket. The util-linux fdisk (in the util-linux package on Ubuntu) is an entirely different code base, which gives you a second set of options for dealing with partitions in case a bug or limitation in libparted causes problems -- and such bugs and limitations seem to crop up with distressing frequency! (Likewise, if a bug or limitation in util-linux's fdisk poses problems, you can use parted, GParted, etc. on the disk.)

The one major advantage of GNU fdisk over util-linux fdisk is that, as demonstrated by your output, GNU fdisk can handle GPT disks. It does so poorly, though. In your second example, at least, it appears that your BIOS Boot Partition was misidentified as a Linux filesystem (type-0x83) partition. If you want to deal with GPT disks with an fdisk-style user interface, I recommend my own [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program, which is *not* based on libparted and was written from scratch as a (roughly) fdisk workalike program for GPT disks. This means it doesn't go through libparted's sometimes convoluted mappings of data structures, which tend to distort one's view of the disk (as in the BIOS Boot Partition showing up as a type-0x83 partition). Also, as with libparted and util-linux fdisk, having both libparted-based tools and GPT fdisk gives you two unrelated code bases so that a bug in one need not stop you cold; the unrelated code base may be able to work around the problem.

---

### Post by YesWeCan on 2011-07-03
> **srs5694 said:**
> Don't use dd. Chances are YesWeCan's suggestion won't work, since it's an incomplete solution; and as oldfred states, it's easy to get it wrong and make things worse. Also as oldfred suggests, my FixParts program should fix the problem.
...and then you say

> That's one of the things that FixParts does; it wipes the two sectors that confuse libparted-based tools. Note that YesWeCan's dd command wipes just one of those two sectors. The command could be adjusted, of course, but that just increases the risk of a typo causing further problems.
The dd commands I stated that zero both GPT header sectors is exactly what you are recommending! Sure, dd can cause damage if the command is not typed accurately, but the OP is no idiot, IMO. So I think your blunt "this won't work" is unjustified and not very polite. And please don't be so arrogant as to tell someone to not do what I recommended when it is a perfectly valid way to do something. We are all meant to be on the same side here.

> The situation is technically legal, but it does cause some libparted-based tools to flake out. This has nothing to do with the Windows partition starting at sector 2048.ok.

> This problem was not caused by a "corruption" of MBR; it's caused by a bug in libparted in conjunction with old code that didn't know enough to wipe out GPT data structures that probably weren't invented when the code was originally written. This problem has nothing to do with GRUB.IMO these 5 pages of discussion are because of differences in how linux tools interpret a disk with an illegal combination of MBR and GPT.
[edit] I take that back. It is legal in the case that a partitioner that does not know GPT is used to create a new MBR PT on a disk that was previously GPT. The partitioner doesn't know to erase the GPT headers.

> I'm not sure of the exact nature of the GParted bug, but you're correct that it is a bug and that it's unacceptable. Your suggestion to flag such ambiguous disks as GPT is incorrect, though, since the GPT spec (at least in UEFI 2.x; I'm not sure about EFI 1.x) is quite clear that such disks are MBR disks.OK. So what exactly is the rule? Presumably, if the MBR PT has anything other than a single type EE entry then the disk should be considered an MBR disk and the GPT data ignored? That would make some sense to me. If so, GParted is defective and the Ubuntu installer is defective. But a warning about the existence of a valid GPT header would be helpful.

> No, Palimpsest Disk Utility works with both partition table types.OK. Palimpsest ignored the GPT data deliberately because it found conventional MBR PT contents.

> Your ire is misplaced. I did not actually say that Grub caused this particular problem but I agree I may have implied it, and in that sense my comment is misplaced. As we have discussed before, my concern is more to do with the Ubuntu installer than Grub, as such, although both are parts of the same problematic design approach, IMO.

---

### Post by ntnkj on 2011-07-03
SUCCESS!!!!

I used

```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda
```

worked like a charm, the installer recognized the win7 installation immediately, I didn't even reboot. :D

Once more, BIIIIIG THANKS to everyone for helping!!
And special thanks to YesWeCan for finding a way through the jungle of confusion I was in
:guitar:

---

### Post by YesWeCan on 2011-07-03
I am really pleased to hear that! :D I have learned a few new things as a result of this thread so thank you for having this problem ;)

---

### Post by Rubi1200 on 2011-07-03
Great news! I am sure we are all pleased that you managed to get this sorted out in the end.

Enjoy :)

---

### Post by oldfred on 2011-07-03
We are all glad it is solved.

But was the original issue the windows partitioner? It must have been the one not to erase the gpt data when it installed windows.

---

### Post by ntnkj on 2011-07-03
> **oldfred said:**
> We are all glad it is solved.

But was the original issue the windows partitioner? It must have been the one not to erase the gpt data when it installed windows.
Yes, that is a question.
And also, this hard drive is brand new, and Win7, an now Ubuntu are the first installations I made on it. I still don't understand the reason I had GUID partition table leftovers...

---

### Post by YesWeCan on 2011-07-03
> **ntnkj said:**
> Yes, that is a question.
And also, this hard drive is brand new, and Win7, an now Ubuntu are the first installations I made on it. I still don't understand the reason I had GUID partition table leftovers...
That would imply the disk came from the factory with a GPT table on it. What is the make and model?

---

### Post by srs5694 on 2011-07-03
> **YesWeCan said:**
> The dd commands I stated that zero both GPT header sectors is exactly what you are recommending!

Despite the fact that my original post appeared after the one in which you recommended a second dd command, when I began the post the thread to that moment only had your post in which you recommended the first dd command. Thus, to that point in the thread, the procedures weren't absolutely identical.

> Sure, dd can cause damage if the command is not typed accurately, but the OP is no idiot, IMO.

Being an idiot or not has nothing to do with typos. Although dd is a useful command, it's also a dangerous command. As a general rule, when two commands exist to solve a problem, and when one of those commands is less prone to the possibility of human error, one should favor the command that's less prone to typos or other human errors. In this case, that's FixParts rather than dd.

Of course, this is (mostly) moot in the current case, since the OP's problem has been resolved. One caveat, though: The backup GPT data may still be lurking on the disk. These backup data could conceivably cause problems in the future if some other utility were to see them and try to use them. The only tools I know of that might do this are GPT recovery programs such as GPT fdisk (gdisk), and gdisk in particular gives the user the option of what data set to use, so *if* the user is well-informed, it won't cause problem even then. That's a bit of a big caveat, though. There's also the possibility that some other program I don't know about might favor the backup GPT data over a valid MBR, or might become confused by this configuration. Thus, I recommend erasing the backup GPT data (if they exist; it's conceivable that they don't, and that only the main GPT data existed and were causing problems). YesWeCan's second dd command should do this, but for the reasons I've stated, I recommend using FixParts instead.

> So I think your blunt "this won't work" is unjustified and not very polite.

You're misrepresenting my statement, which was "*Chances are* YesWeCan's suggestion won't work" (emphasis added; and also note my earlier caveat that I was replying to your initial one-dd suggestion). It turns out I was wrong about this; it appears that libparted stops looking for GPT data if the main data are missing, at least if the MBR is valid, so a single dd command does the trick.

As to being polite, I was giving my appraisal of a technical problem and a suggested solution. If I think a solution is not likely to work or is otherwise unwise, I'll say so, and if the person I'm contradicting is offended by that, tough. My comment was not directed at you personally -- I referred to your suggestion and did not in any way disparage you personally.

> And please don't be so arrogant as to tell someone to not do what I recommended when it is a perfectly valid way to do something. We are all meant to be on the same side here.

See above. Your solution did work in this case, but at the time I posted, I had every reason to suggest an alternative -- and I *still* recommend FixParts over dd to solve this problem in general. Using FixParts is less likely to cause problems because of typos. It is not arrogant to offer alternatives or even to warn against a procedure that one believes to be risky or unlikely to work.

> OK. So what exactly is the rule? Presumably, if the MBR PT has anything other than a single type EE entry then the disk should be considered an MBR disk and the GPT data ignored? That would make some sense to me.

By a very strict reading of the specs, yes, that's correct. Unfortunately, the real world also has things called [hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) that violate the spec by containing both a shortened 0xEE protective partition and up to three other partitions. Thus, as a practical matter partitioning tools, OSes, boot loaders, etc. have to accept such disks as valid in one way or another. Most do so by using the GPT side, but Windows and Windows partitioning tools do it by using the MBR side. (That's the reason for the existence of hybrid MBRs -- they're part of what enables Windows to dual-boot on Intel-based Macs.)

[quote=ntnkj]And also, this hard drive is brand new, and Win7, an now Ubuntu are the  first installations I made on it. I still don't understand the reason I  had GUID partition table leftovers...[/quote]

Examination of the original GPT data structures (before you rewrote the MBR) could give some clues, since GPT partitioning tools create their protective MBRs and other data structures in unique ways; but most of the relevant data are gone now, so I can only speculate. Some possibilities that occur to me include:


[list]
[*]Secondhand data -- if the disk was purchased by one person, returned, and then sold again, it could have had old partitioning data that you didn't know about. I've heard of this happening once before. Once the solution was found in that case, the original poster in that thread stated the disk had been an "open box" special. If this wasn't the case for you, chances are it's not the correct explanation, but it could be your retailer misrepresented the state of the drive, so I wouldn't rule out the possibility entirely.
[*]Accidental GPT creation by you -- You might have accidentally created a GPT on the drive in early testing before you installed Windows. There are a million ways in which this might have happened if you did anything but connect the drive and boot straight into the Windows installaer.
[*]UEFI on your computer -- If your computer has UEFI firmware and you booted the Windows installer in this mode, the installer would have partitioned the disk for GPT during installation. If you had problems with this, fiddled with your CMOS settings to disable UEFI mode, and tried again, the Windows installer would have then wiped out the protective MBR but not the GPT data. (The Windows installer both knows how to partition a disk for GPT and doesn't wipe out old GPT data when doing it in MBR mode.) In a sense, this is a special case of the preceding one.
[*]Disk pre-partitioned with GPT -- This is pretty rare for internal disks, but external disks are often pre-partitioned. My impression is that the partitioning is usually for MBR, especially on disks of that size; but it's conceivable that it came from the factory with GPT. This would surprise me if true, but I can't rule it out as a possibility.
[/list]


If you're really desperate to know the solution, you could try using gdisk to recover the GPT partitions, display them (with the "p" main-menu command), and then *quit without saving changes* (with the "q" main-menu command). The nature of the GPT partitions might provide some clues -- for instance, if you saw one or more Mac OS X partitions and you're not using a Mac and never attempted a "Hackintosh" installation, that's a pretty good indication that you've got secondhand data on the disk. IMHO, though, it's not worth the (minor) risk of accidentally trashing your partition table to figure out what happened. *Maybe* if you suspected the retailer of selling secondhand merchandise as new it'd be worth checking for clues, but I'm not sure it's worth it even then. There's also no guarantee that gdisk could recover anything; it could be that the relevant sectors have all been overwritten by now.

---

### Post by ntnkj on 2011-07-03
> **YesWeCan said:**
> That would imply the disk came from the factory with a GPT table on it. What is the make and model?
Western Digital Scorpio Black WD3200BEKT - 320 GB - SATA-300

---

### Post by ntnkj on 2011-07-03
> If you're really desperate to know the solution, you could try using gdisk to recover the GPT partitions, display them (with the "p" main-menu command), and then quit without saving changes (with the "q" main-menu command). The nature of the GPT partitions might provide some clues -- for instance, if you saw one or more Mac OS X partitions and you're not using a Mac and never attempted a "Hackintosh" installation, that's a pretty good indication that you've got secondhand data on the disk. IMHO, though, it's not worth the (minor) risk of accidentally trashing your partition table to figure out what happened. Maybe if you suspected the retailer of selling secondhand merchandise as new it'd be worth checking for clues, but I'm not sure it's worth it even then. There's also no guarantee that gdisk could recover anything; it could be that the relevant sectors have all been overwritten by now.

No, I'm not that interested, actually, I've had quite enough terminal work in the past month, I think I'll just enjoy my Ubuntu, and be grateful for such a fantastic community!
But thanks for the suggestion!

---

