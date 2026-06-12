---
title: "Lubuntu 20.04 installation warns ESP flag missing despite an existing ESP"
date: 2020-05-01
forum: Installation &amp; Upgrades
---

### Post by &amp;wP*!) on 2020-05-01
**Problem**
Lubuntu 20.04 installation warns that the ESP flag is missing even though 19.04 can boot with ESP /boot/efi without its ESP flag is set. Following message is shown by the installation:
```
A partition was configured with mount point /boot/efi but its esp flag is not set.
To set the flag, go back and edit the partition.

You can continue without setting the flag but your system may fail to start.

```
However, the partition editor in the installation does not show esp flag, but the flags **boot** and **bios-grub**. Clicking former (boot flag) did not solve the problem. The latter (bios-grub) cannot be used, because the computer has an existing UEFI/GPT partitioning scheme with ESP on /dev/sda1.

**Setup**
The Computer has Lubuntu 19.04 with the following partition layout. As it can be seen below, the esp flag is not set. But the system could boot.
```
$ sudo parted /dev/sda -l
Model: ATA SAMSUNG SSD PM85 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name  Flags
 1      17,4kB  1075MB  1075MB  fat32                 msftdata
 2      1075MB  9665MB  8590MB  linux-swap(v1)
 3      26,8GB  44,0GB  17,2GB  ext4
 5      68,7GB  137GB   68,7GB  btrfs
```
1st partition is ESP:
```
$ df -h /dev/sda1
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1      1023M  7,7M 1016M   1% /boot/efi
```
Questions
[LIST=1]
[*]The reason why Lubuntu 19.04 can be booted by an ESP without its ESP flag ist set is described in [https://www.rodsbooks.com/efi-bootloaders/principles.html](https://www.rodsbooks.com/efi-bootloaders/principles.html) : &#8220;and a redundant "esp flag".. Why does Lubuntu 20.04 installation not ignore a redundant flag, but 19.04 does?
[*]Is it a good practice to manipulate the ESP flag with parted, before I install 20.04? Is there anything I have to pay attention to?
[/LIST]

---

### Post by &amp;wP*!) on 2020-05-01
Solution: completely wipe out the harddisk and install Ubuntu 20.04. 
esp flag could not be set. The warning was ignored by the user (myself). 
After the installation, rebooted the system. Package upgrade done. Rebooted the system.
The computer can boot without esp flag set to ESP. Below the partition layout after the Ubuntu 20.04 installation:
```
$ sudo parted /dev/sda -l
Model: ATA SAMSUNG SSD PM85 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      17,4kB  1075MB  1075MB  fat32                 msftdata
 2      1075MB  26,8GB  25,8GB  linux-swap(v1)        swap
 3      26,8GB  95,6GB  68,7GB  ext4
 4      95,6GB  256GB   160GB   ext4
```
Since the system is able to boot, warning does not seem to be an issue.

Proof that 20.04 was installed:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04 LTS
Release:        20.04
Codename:       focal]/CODE]

```
Kernel:
```
$ uname  -a
Linux e7440 5.4.0-28-generic #32-Ubuntu SMP Wed Apr 22 17:40:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```


Thus setting this thread to SOLVED.

---

### Post by oldfred on 2020-05-01
Parted uses the esp flag to set a very long GUID which tells UEFI to use that partition to find boot files.
The bios_grub flag is only used for BIOS boot on gpt partitioned flags and is totally different. 
Gdisk uses code ef00 to assign the same GUID for the ESP - efi system partition.
You may have an unusual case?

List of GUID.
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)
fred@Z170N-focal:~$ lsblk -o +parttype

```
nvme0n1
&#9474;      259:0    0 465.8G  0 disk            
&#9500;&#9472;nvme0n1p1
&#9474;      259:1    0   512M  0 part /boot/efi  c12a7328-f81f-11d2-ba4b-00a0c93ec93b

```

---

### Post by &amp;wP*!) on 2020-05-01
> **oldfred said:**
> Parted uses the esp flag to set a very long GUID which tells UEFI to use that partition to find boot files.
The bios_grub flag is only used for BIOS boot on gpt partitioned flags and is totally different. 
Gdisk uses code ef00 to assign the same GUID for the ESP - efi system partition.
You may have an unusual case?

List of GUID.
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)
fred@Z170N-focal:~$ lsblk -o +parttype

```
nvme0n1
&#9474;      259:0    0 465.8G  0 disk            
&#9500;&#9472;nvme0n1p1
&#9474;      259:1    0   512M  0 part /boot/efi  c12a7328-f81f-11d2-ba4b-00a0c93ec93b

```
Hi oldfred, I am fully aware that bios_grub flag is out of question here. Maybe my text above is not clear that I am aware of it. I am aware that I have a UEFI/GPT system. 

Due to the partition, its underlying hardware or maybe Ubuntu installation software bug, I don't know what the reason is, during the 20.04 installation the flags were never shown properly in the user interface.

My intention was to install Ubuntu 20.04 onto the existing partitions of a Lubuntu 19.04 installation, by wiping them out but keeping the partitions. ESP flag was never shown by the installation. I returned to 19.04, set the ESP flag, rebooted and started the installation 20.04 ISO from an existing partition (not USB!). Through this trick I was able not to see the warning any more.

The installation on existing partitions failed for some reason which was not reported (installation report shows only the commands) and I had to wipe out the complete harddisk to get the 20.04. During this new fresh installation ESP flag warning was shown again, but as I have written above, I have ignored it. This is also maybe the proof that ESP flag is redundant. Rod Smith, the developer of rEFInd has also same comments here: [https://www.rodsbooks.com/efi-bootloaders/principles.html](https://www.rodsbooks.com/efi-bootloaders/principles.html)

There are many threads on internet that the installation program of Ubuntu used in other distros have the same problem. Example:
[https://github.com/calamares/calamares/issues/891](https://github.com/calamares/calamares/issues/891)

---

### Post by &amp;wP*!) on 2020-05-01
BTW, after the fresh install (by completely wiping out the hardissk) I don't see the GUID you mention:
```
$ lsblk -o +parttype
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT PARTTYPE
sda      8:0    0 238,5G  0 disk            
&#9500;&#9472;sda1   8:1    0     1G  0 part /boot/efi  ebd0a0a2-b9e5-4433-87c0-68b6b72699c7
&#9500;&#9472;sda2   8:2    0    24G  0 part [SWAP]     0657fd6d-a4ab-43c4-84e5-0933c84b4f4f
&#9500;&#9472;sda3   8:3    0    64G  0 part /          0fc63daf-8483-4772-8e79-3d69d8477de4
&#9492;&#9472;sda4   8:4    0 149,5G  0 part /home      0fc63daf-8483-4772-8e79-3d69d8477de4
```
Ubuntu 20.04 installation does not set the flag after the successful installation:
```
$ sudo parted -l
Model: ATA SAMSUNG SSD PM85 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      17,4kB  1075MB  1075MB  fat32                 msftdata
 2      1075MB  26,8GB  25,8GB  linux-swap(v1)        swap
 3      26,8GB  95,6GB  68,7GB  ext4
 4      95,6GB  256GB   160GB   ext4
```

---

### Post by markf2 on 2020-07-13
> **pencuse said:**
> **Problem**
Lubuntu 20.04 installation warns that the ESP flag is missing.... However, the partition editor in the installation does not show esp flag, but the flags **boot** and **bios-grub**. Clicking former (boot flag) did not solve the problem. The latter (bios-grub) cannot be used, because the computer has an existing UEFI/GPT partitioning scheme with ESP on /dev/sda1.


This is funny to me. I participated in 20.04 testing. I reported that problem (among a few other Calamares problems, such as ambiguous GPT-creation failures -- which didn't seem like errors you went back and looked at the finished result). I was told the "ESP" flag problem (you described) was "just semantics."

I miss the old Lubuntu *so* much. When it was LXDE, and maybe Mario had it then. Now it's like nobody cares. I was beating my brains out with that random GPT failure (which didn't seem to be a failure when you went back and looked at the disk.). *Then* I learned it had been known for _*months*_, and nobody had even proposed that Calamares add more error capturing (context reporting). Everyone seemed *fine* with just living with it as "*someday* we'll see a pattern." Worse than that, they wouldn't even enable Calamares extended error/debug reporting to make it easier to find a *known* problem (a *random *problem benefiting from always-on *opportunities* like that.). I wasted 2-3 weeks before someone told me I should enable that for myself.  A week or two later I learned this was an existing issue for _*months*_. It's like they *enjoy* working harder, ignoring usability issues, etc. (After that I was depicted as merely complaining, not "helping.").

None of that's really funny. What's funny is that I was just now, for the first time, trying to install Lubuntu 20.04 and ran into this very *familiar* problem. I googled to see if anyone else had found it. *And there you were!* Reporting the *same* thing. Linking to a bug where the Calamares people downplay the matter, as if usability doesn't matter, just as they did *last February*.

I told the Lubuntu people to just go back to Ubiquity until Calamares is usable. (But, then, of course, I was complaining, not speaking like a rational person.). 

IMO, Lubuntu isn't ready for primetime. (It's conceptual.). They complain that they can't get enough people to help. But then, have _***zero***_ care for the time they cost people who help. I mean, at some point, "helping" becomes *enabling*. This Calamares matter is a _***perfect***_ example. I would have gone back to Ubiquity (and had a working installer) *months* before some volunteer suggested it (after wasting countless hours of his time). They were just shooting in the dark, expecting everyone else to. (They didn't even enable extended debug/reporting as a default -- to make the most of any opportunity to see a pattern. It's **_*still*_** there. I just got the gpt error/non-error again!).

I guess what twisted my nose out of joint about all this is the narrative like above would be met with tedious, red-herring, distracting "it's not 'extended debug/reporting,' and that's why nobody should pay attention to you." I swear to God! Some semantic mistake in the details, and the entire larger point means nothing. Whatever it was, I was *supposed to have been using it* -- and all those random encounters were less valuable. At a time when they knew the problem existed for _***MONTHS***_. When asked why that wasn't the default in the daily image... now I'm complaining. They need people to help, not complain.

That's the attitude which led to you having to report what you just reported (to people who wasted a ton of time -- while wishing they had more of.). IMO this is a perfect example of why Linux can't acquire a credible portion of Microsoft's market. How would a new user navigate the ESP error message (when there's no ESP flag, and it's dismissed as "just semantics.")? Or, the seemingly pointless GPT-creation error? How badly does the Linux community *want* to compete against Microsoft -- when a blind eye is turned to garbage like that (instead of going back to the normal, default installer until Calamares gets their act together)?

---

### Post by &amp;wP*!) on 2020-07-15
> **markf2 said:**
> This is funny to me. I participated in 20.04 testing. I reported that problem (among a few other Calamares problems, such as ambiguous GPT-creation failures -- which didn't seem like errors you went back and looked at the finished result). I was told the "ESP" flag problem (you described) was "just semantics."

I miss the old Lubuntu *so* much. When it was LXDE, and maybe Mario had it then. Now it's like nobody cares. I was beating my brains out with that random GPT failure (which didn't seem to be a failure when you went back and looked at the disk.). *Then* I learned it had been known for _*months*_, and nobody had even proposed that Calamares add more error capturing (context reporting). Everyone seemed *fine* with just living with it as "*someday* we'll see a pattern." Worse than that, they wouldn't even enable Calamares extended error/debug reporting to make it easier to find a *known* problem (a *random *problem benefiting from always-on *opportunities* like that.). I wasted 2-3 weeks before someone told me I should enable that for myself.  A week or two later I learned this was an existing issue for _*months*_. It's like they *enjoy* working harder, ignoring usability issues, etc. (After that I was depicted as merely complaining, not "helping.").

None of that's really funny. What's funny is that I was just now, for the first time, trying to install Lubuntu 20.04 and ran into this very *familiar* problem. I googled to see if anyone else had found it. *And there you were!* Reporting the *same* thing. Linking to a bug where the Calamares people downplay the matter, as if usability doesn't matter, just as they did *last February*.

I told the Lubuntu people to just go back to Ubiquity until Calamares is usable. (But, then, of course, I was complaining, not speaking like a rational person.). 

IMO, Lubuntu isn't ready for primetime. (It's conceptual.). They complain that they can't get enough people to help. But then, have _***zero***_ care for the time they cost people who help. I mean, at some point, "helping" becomes *enabling*. This Calamares matter is a _***perfect***_ example. I would have gone back to Ubiquity (and had a working installer) *months* before some volunteer suggested it (after wasting countless hours of his time). They were just shooting in the dark, expecting everyone else to. (They didn't even enable extended debug/reporting as a default -- to make the most of any opportunity to see a pattern. It's **_*still*_** there. I just got the gpt error/non-error again!).

I guess what twisted my nose out of joint about all this is the narrative like above would be met with tedious, red-herring, distracting "it's not 'extended debug/reporting,' and that's why nobody should pay attention to you." I swear to God! Some semantic mistake in the details, and the entire larger point means nothing. Whatever it was, I was *supposed to have been using it* -- and all those random encounters were less valuable. At a time when they knew the problem existed for _***MONTHS***_. When asked why that wasn't the default in the daily image... now I'm complaining. They need people to help, not complain.

That's the attitude which led to you having to report what you just reported (to people who wasted a ton of time -- while wishing they had more of.). IMO this is a perfect example of why Linux can't acquire a credible portion of Microsoft's market. How would a new user navigate the ESP error message (when there's no ESP flag, and it's dismissed as "just semantics.")? Or, the seemingly pointless GPT-creation error? How badly does the Linux community *want* to compete against Microsoft -- when a blind eye is turned to garbage like that (instead of going back to the normal, default installer until Calamares gets their act together)?

TL;DR

Solution to get ESP flag after installation was to set the ESP flag manually, using **parted**. Having set this flag, now I get the GUID of ESP:
```
$ lsblk -o +parttype
sda        8:0    0 238,5G  0 disk                               
&#9500;&#9472;sda1     8:1    0     1G  0 part  /boot/efi                    **c12a7328-f81f-11d2-ba4b-00a0c93ec93b**
&#9500;&#9472;sda2     8:2    0    24G  0 part  [SWAP]                       0657fd6d-a4ab-43c4-84e5-0933c84b4f4f
&#9500;&#9472;sda3     8:3    0    64G  0 part  /                            0fc63daf-8483-4772-8e79-3d69d8477de4
&#9492;&#9472;sda4     8:4    0 149,5G  0 part  /home                        0fc63daf-8483-4772-8e79-3d69d8477de4
 
```

---

