---
title: "Ubunto 10.04 Does not detects WD HD"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by mathewprince on 2011-03-20
Hi All,


I tried to install ubuntu 10.10 Lynx through livecd  , but the partitions in my 160gb western digital hard disk is shown as unallocated free space . Through the linux terminal when I fire the command sudo fdisk -l it does not display anything. In my current HD I have installed windows XP successfully. 

PS : HD is working fine and the installation media is K ( Did a check sum check ) .

---

### Post by Quackers on 2011-03-20
What does Windows Disk Management screen show as the partition structure?

---

### Post by mathewprince on 2011-03-20
> **Quackers said:**
> What does Windows Disk Management screen show as the partition structure?

pl refer the attachment for the partition structure .

---

### Post by Quackers on 2011-03-20
Thanks. It appears that you have XP in a primary partition, then 3 logical partitions inside an extended partition. It's a prefectly good setup, but I wonder if there is a partition table problem. If the installer can't see the partition table and fdisk -l can't see it, maybe there is a problem with it. Can I ask how those partitions were set up?

---

### Post by Quackers on 2011-03-20
I see also that there is no unallocated space for Ubuntu to install into. Ubuntu will not install to a NTFS or FAT32 partition.

---

### Post by mathewprince on 2011-03-20
> **Quackers said:**
> Thanks. It appears that you have XP in a primary partition, then 3 logical partitions inside an extended partition. It's a prefectly good setup, but I wonder if there is a partition table problem. If the installer can't see the partition table and fdisk -l can't see it, maybe there is a problem with it. Can I ask how those partitions were set up?
Thanks for the reply. 

Partition were made using windows Live CD .

Let me explain the complete scenario to you . I used to have Ubuntu 10.04 ( Updated from 9.1 ) and Windows XP working absolutely fine on my laptop . Ubuntu was used mainly for my programming needs. Suddenly one day ubuntu crashed . Through my windows XP CD I fixed MBR by using fixmbr command and removed the linux partition. Then at this point I decided that I will be only using ubuntu on my laptop . While installing ubuntu my entire HD was shown as unused . I formatted my entire HD and installed XP again with the partition structure as shown above . 

PS : Gparted does not even detect my HD.

EDIT :

> **Quackers said:**
> I see also that there is no unallocated space  for Ubuntu to install into. Ubuntu will not install to a NTFS or FAT32  partition.

Problem I am facing is that ubuntu should not show my entire HD as  unallocated . Once this problem is solved I shall make proper  partitions.

/boot mount point : ext4 
/ mount point : ext4
/ home mount point 
/swap mount point

---

### Post by Quackers on 2011-03-20
It is not necessarily surprising that the installer does not see the drive. This is because the drive is completely occupied. There is no space for Ubuntu to install to. It will not install to a NTFS or FAT32 partition. fdisk -l would be expected to see it though. 
I don't know if it will see the partitions either but it may be worth trying. Please boot from the ubuntu live cd and select "try ubuntu" rather than "install ubuntu" and when the desktop loads, connect to the internet. Then go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mathewprince on 2011-03-20
> **Quackers said:**
> It is not necessarily surprising that the installer does not see the drive. This is because the drive is completely occupied. There is no space for Ubuntu to install to. It will not install to a NTFS or FAT32 partition. fdisk -l would be expected to see it though. 
I don't know if it will see the partitions either but it may be worth trying. Please boot from the ubuntu live cd and select "try ubuntu" rather than "install ubuntu" and when the desktop loads, connect to the internet. Then go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Results of the script is mentioned below.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

```

---

### Post by Quackers on 2011-03-20
Hmm this is important
```
Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

[COLOR="Red"]Invalid MBR Signature found[/COLOR]
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown
```[COLOR="Black"]As for the rest of the output, I can confidently say that I have not seen another like it! All those I/O errors! Not good I would say.[/COLOR]

Are you using a raid array?

---

### Post by mathewprince on 2011-03-20
> **Quackers said:**
> Hmm this is important
```
Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

[COLOR=Red]Invalid MBR Signature found[/COLOR]
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown
```[COLOR=Black]As for the rest of the output, I can confidently say that I have not seen another like it! All those I/O errors! Not good I would say.[/COLOR]

Are you using a raid array?
Thanks for the information and reply. So this means I need to boot to windows and fix the MBR . Can the same be done from ubuntu linux live CD ?

---

### Post by coffeecat on 2011-03-20
> **Quackers said:**
> [/code][COLOR=Black]As for the rest of the output, I can confidently say that I have not seen another like it! [/COLOR]

Nor have I! One wonders how Windows Disk management can see anything at all.

@matthewprince, this may not reveal any more useful information, but it's worth doing. Boot up with the live Ubuntu CD to the desktop. Open a terminal and run this command:

```
sudo sfdisk -d /dev/sda > Desktop/parts.txt
```A file, parts.txt, will appear on the desktop. Please post this between [noparse]```
 and 
```[/noparse] tags. This will be a representation of your partition table. But since the boot script is trying to read that as well and coming up with errors, it will be useful to see what sfdisk makes of it.

---

### Post by coffeecat on 2011-03-20
> **mathewprince said:**
> Thanks for the information and reply. So this means I need to boot to windows and fix the MBR . Can the same be done from ubuntu linux live CD ?

No, best not to try to do anything to  the mbr just yet. The problem is more profound and needs investigating.

---

### Post by mathewprince on 2011-03-20
> **coffeecat said:**
> Nor have I! One wonders how Windows Disk management can see anything at all.

@matthewprince, this may not reveal any more useful information, but it's worth doing. Boot up with the live Ubuntu CD to the desktop. Open a terminal and run this command:

```
sudo sfdisk -d /dev/sda > Desktop/parts.txt
```A file, parts.txt, will appear on the desktop. Please post this between [noparse]```
 and 
```[/noparse] tags. This will be a representation of your partition table. But since the boot script is trying to read that as well and coming up with errors, it will be useful to see what sfdisk makes of it.
The above command gives the following output .
```

read: Input/output error
sfdisk: read error on /dev/sda - cannot read sector 0
 /dev/sda: unrecognized partition table type
No partitions found

```

---

### Post by Quackers on 2011-03-20
As a precautionary measure (and as you cannot access Windows from the live desktop) I suggest that you backup anything that you wouldn't want to lose, from within Windows.
I think we need professional help!
I'll pm somebody and see if he can make suggestions. He's the partition doctor. Sadly, I don't know if he's online at the moment.

---

### Post by mathewprince on 2011-03-20
> **Quackers said:**
> As a precautionary measure (and as you cannot access Windows from the live desktop) I suggest that you backup anything that you wouldn't want to lose, from within Windows.
I think we need professional help!
I'll pm somebody and see if he can make suggestions. He's the partition doctor. Sadly, I don't know if he's online at the moment.

Thanks a lot for your reply . So as suggested by you boot record appears to be corrupted.  In the mean time 
I shall work on it as well and fix the issue.

---

### Post by Quackers on 2011-03-20
No, it's not the boot record. It seems to be a problem with the partition table. This can happen as a result of partitioning. Actually with XP it can happen when an extended partition is created. Sometimes the system allows the extended partition (or a logical partition within it) to be slightly too large, creating an impossibility in the partition table. I don't know if that is the problem here, as we can't get any details!
I would backup anything you need and wait to see if the partition doctor arrives :-)

---

### Post by coffeecat on 2011-03-20
> **Quackers said:**
> No, it's not the boot record. It seems to be a problem with the partition table.

@matthewprince, I agree with that. If it was just the master boot record that was faulty, it would be a simple thing to repair. But since  sfdisk cannot make head nor tail of the partition table, that's a much more serious problem. 

Await the expert Quackers has pm'd. He needs to look at this.

As an aside, the partition table is actually part of the MBR, in its strict definition. The mbr is the first 512 bytes of the disc. The boot code resides in the first 440 bytes or so and this is often loosely referred to as the MBR. Which is what I was referring to when I suggested not trying to fix the mbr just yet. The 64 bytes from 446 contain the partition table.

---

### Post by mathewprince on 2011-03-20
Thanks for the info about partition table . As suggested we shall wait for the partition expert to give his view .

---

### Post by srs5694 on 2011-03-20
I don't see any evidence of a corrupt MBR (which is where both the boot loader and the partition table reside); I see evidence of an inability to read the MBR. Specifically, those I/O errors mean that the data read by fdisk, GParted, and any other partitioning tools you've used under Linux are unreliable and should be ignored. Therefore, I recommend not attempting any sort of data repair unless and until the I/O error issue is resolved. Backing up the data from within Windows, as others have suggested, is a reasonable precaution, in case the hardware is just beginning to fail (bad enough to give Linux problems, but Windows can somehow cope).

For further diagnostics, try booting a Linux live CD, typing the following commands, and posting the results here:

```

ls -l /dev/sd*
dmesg | grep sda
cat /proc/scsi/scsi

```

With any luck, the output from those commands will provide some clue about what's going on.

Just to clarify: If I understand correctly, you once had Linux (Ubuntu 10.04) installed on *this exact hardware*, but it stopped booting, so you removed it, and now you want to install it again. If I misunderstand that Linux was once installed and working on this system, please clarify. Also, if you've made any changes to the hardware, please say what they were. I ask all this because it strikes me as odd that Linux could once work with this computer and this disk but now can't. The three most likely causes I can think of for this are a failing piece of hardware, a loose cable, or a new bug in a recent kernel that's causing problems.

---

### Post by mathewprince on 2011-03-21
> **srs5694 said:**
> I don't see any evidence of a corrupt MBR (which is where both the boot loader and the partition table reside); I see evidence of an inability to read the MBR. Specifically, those I/O errors mean that the data read by fdisk, GParted, and any other partitioning tools you've used under Linux are unreliable and should be ignored. Therefore, I recommend not attempting any sort of data repair unless and until the I/O error issue is resolved. Backing up the data from within Windows, as others have suggested, is a reasonable precaution, in case the hardware is just beginning to fail (bad enough to give Linux problems, but Windows can somehow cope).

For further diagnostics, try booting a Linux live CD, typing the following commands, and posting the results here:

```

ls -l /dev/sd*
dmesg | grep sda
cat /proc/scsi/scsi

```With any luck, the output from those commands will provide some clue about what's going on.

Just to clarify: If I understand correctly, you once had Linux (Ubuntu 10.04) installed on *this exact hardware*, but it stopped booting, so you removed it, and now you want to install it again. If I misunderstand that Linux was once installed and working on this system, please clarify. Also, if you've made any changes to the hardware, please say what they were. I ask all this because it strikes me as odd that Linux could once work with this computer and this disk but now can't. The three most likely causes I can think of for this are a failing piece of hardware, a loose cable, or a new bug in a recent kernel that's causing problems.

Guys One major update , If I set the HD mode to ACHI from BIOS ubuntu is able to detect the HD . Also Gparted also detects the HD , but the problem is when I boot to windows XP BSOD ( Blue screen of death )is displayed. 

Linux used to work perfectly well on my Laptop before and no hardware changes were made . 
Now atleast with HD mode set as AHCI ubuntu detects my HD.

---

### Post by mathewprince on 2011-03-21
Thanks a lot mates for helping me . Atleast now ubuntu recognizes my HD .Now as the problem needs to be fixed in XP I am marking this thread as fixed. Thanks once again :)

---

### Post by srs5694 on 2011-03-21
As I understand it, many modern chipsets support both a newer Advanced Host Controller Interface (AHCI) mode and a "legacy" mode that uses older transfer methods. Most Linux drivers support both modes transparently, so in theory it should be working for you. My suspicion is that you've encountered a bug or configuration issue in the specific kernel or Ubuntu version you're trying to use.

In theory, AHCI mode can produce better speed, but I don't know how much of an effect it has in the real world. Typically, mucking with the AHCI setting will cause problems for Windows, and fixing those problems can be very difficult. I'm not a Windows expert, but the few sources of information I've stumbled across seem to suggest re-installing Windows as being the solution if you must switch AHCI mode.

Between all this, you might want to look more closely at the Linux side and try to get it working with AHCI mode. As I'm not an expert on this topic, I can't offer any specific solutions, but I can offer a few possible approaches:


[list]
[*]**Google it** -- Try a Web search on relevant keywords. It may turn up something. Include your computer's, motherboard's, or chipset's model number in your search, if possible, since the proper solution is likely to involve the disk controller chipset.
[*]**Investigate boot loader options** -- One possible class of solutions is to add a kernel option to the boot loader to enable AHCI support or to set driver-specific AHCI options.
[*]**Try another distribution** -- It's possible that another distribution (or another version of Ubuntu) uses different options that will work better with your hardware.
[/list]

---

### Post by mathewprince on 2011-03-25
> **srs5694 said:**
> [B]My suspicion is that you've encountered a bug or configuration issue in the specific kernel or Ubuntu version you're trying to use.
[/B]

Sorry for the delayed response. This seems to be true . I fixed the problem by re installing Windows and switching the HD mode to AHCI. What I have done is just one of the fixes as I had recently taken a HD back up , I did not mind doing a clean install.

---

