---
title: "Weird issue with partitioning"
date: 2017-11-22
forum: Installation &amp; Upgrades
---

### Post by m3tax on 2017-11-22
So I kinda screwed up earlier by trying to install Ubuntu with UNetbootin, so I just decided to delete everything and install Ubuntu without dual booting Windows.

 So I grab my usb, plug it in, try to install Ubuntu and choose the option to delete everything else. I also enabled LVM. After clicking Next, the installer just crashed.
[IMG]https://i.imgur.com/4vNjy8a.png[/IMG] 

I tried a bunch more times even with LVM off, but the installer crashes anyway.
[IMG]https://i.imgur.com/a3y6zlO.png[/IMG] 
So I decide to choose "Something else"... And apparently during one of the crashes, Ubuntu did actually delete everything on my 1TB hard drive. Weird. Now I try to partition it manually.[IMG]https://i.imgur.com/H59vBW0.png[/IMG]

Nope - Failed to create swap.. Also the installer crashes after every attempt (I tried to do this like 10 times). So I just don't allocate any swap. Nope. This time it Failed to create ext4 file system for the root directory.

I also tried the UEFI option - got a weird popup considering I don't have windows installed, but otherwise it still does the same thing.
[IMG]https://i.imgur.com/bSIlxIJ.png[/IMG]

A whole day of googling later, I go into Disks and overwrite any existing data on my hard drive. After 5 hours it's finished!... And it still fails to create swap/ext4. At least the installer crashes only like 50% of the time now.

I also tried GParted, but it gives this error, so it doesn't work for partitioning either.

[IMG]https://i.imgur.com/8a10ee9.png[/IMG]


So, I kinda tried everything (aside from dban, but I already overwrote everything so I don't think it'll work anyway). Any help? I'm out of ideas.

---

### Post by oldfred on 2017-11-22
The error on 2048 is usually from the live installer's configuration.

Is this an UEFI system? Or BIOS?
Will you eventually install Windows (an in BIOS boot mode)? As then drive has to be MBR partitioned.
If UEFI or Ubuntu only better to use gpt partitioning.

       If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
sudo parted /dev/sda mklabel gpt 

If UEFI or drive may ever be installed in a newer UEFI system include both the ESP & bios_grub. I standardized on that for all new drives long before I had an UEFI system.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

---

### Post by m3tax on 2017-11-24
> **oldfred said:**
> The error on 2048 is usually from the live installer's configuration.

Is this an UEFI system? Or BIOS?
Will you eventually install Windows (an in BIOS boot mode)? As then drive has to be MBR partitioned.
If UEFI or Ubuntu only better to use gpt partitioning.

       If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
sudo parted /dev/sda mklabel gpt 

If UEFI or drive may ever be installed in a newer UEFI system include both the ESP & bios_grub. I standardized on that for all new drives long before I had an UEFI system.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found) 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

Hey there, thanks for replying.
My system is UEFI. And I don't plan on installing windows in the future.Unfortunately I cannot follow the rest of your answer because, as I mentioned, GParted gives the "Driver descriptor says the physical block size is 2048, but Linux says it's 512" error - which I can just ignore - but when trying to create a new partition table nothing happens. Ubuntu also doesn't let me partition with the installer either, so I can't really do anything.

---

### Post by oldfred on 2017-11-24
is drive gpt?
Did you trychanging drive to gpt with gparted or parted's mklabel?

Is this a standard SATA drive or newer NVMe drive?
Is UEFI set to AHCI for drives?

Does this show anything?
sudo parted -l
sudo gdisk -l /dev/sda

---

### Post by m3tax on 2017-11-25
> **oldfred said:**
> is drive gpt?
Did you trychanging drive to gpt with gparted or parted's mklabel?

Not sure if it's gpt, but I ran "sudo parted mklabel gpt" and it didn't return any errors, so I guess it worked.
However GParted still refuses to do anything.

[IMG]https://i.imgur.com/oBrzQC3.png[/IMG]

> **oldfred said:**
> Is this a standard SATA drive or newer NVMe drive?
SATA.

> **oldfred said:**
> Is UEFI set to AHCI for drives?
(copy pasted from bios)
OnChip SATA Type - AHCI
OnChip SATA Port4/5 Type - IDE

> **oldfred said:**
> Does this show anything?
sudo parted -l
sudo gdisk -l /dev/sda
I included both the results for IGNORE and CANCEL after "sudo parted -l" since they're different for some reason.

[IMG]https://i.imgur.com/0IjAGc2.png[/IMG]

---

### Post by oldfred on 2017-11-25
Make sure you are not using SATA ports 4/5 or change them to AHCI.  The old IDE is for old drives compatiblity.
You should start using SATA0 and plug drives in SATA port order, to avoid future issues.

Gparted does not like the disk label which is either gpt or msdos (and others).
So mklabel may not have worked.

Was drive ever RAID? Then it may have meta-data still on it. And Intel SRT is seen as RAID.
This will remove the meta-data.
 sudo dmraid -E -r /dev/sda

If gdisk is not complaining, then you can try gdisk to create partitions.
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by m3tax on 2017-11-25
> **oldfred said:**
> Make sure you are not using SATA ports 4/5 or change them to AHCI.  The old IDE is for old drives compatiblity.
You should start using SATA0 and plug drives in SATA port order, to avoid future issues.
Don't know which port I'm using so I just changed ports 4/5 to AHCI.

> **oldfred said:**
> Was drive ever RAID? Then it may have meta-data still on it. And Intel SRT is seen as RAID.
This will remove the meta-data.
 sudo dmraid -E -r /dev/sda

[IMG]https://i.imgur.com/PN23s7Y.png[/IMG]
Nope, no RAID and no meta-data. 

> **oldfred said:**
> If gdisk is not complaining, then you can try gdisk to create partitions.
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

A little bit of weirdness with gdisk. So the first time I tried it, I created a new partition and used all the defaults, and it worked! I made a 1tb partition with all-defaults. I took this screenshot while writing the reply.

[IMG]https://i.imgur.com/s6kPVsh.png[/IMG]

At this point I have read about cgdisk on the site you linked, so I try it out too. I use that to delete it, then make a few other ones, write them to the disk, and launch  gdisk. But this time gdisk doesn't see anything. So I try to make a few partitions, write them, then quit and relaunch gdisk... but they don't show up. Cgdisk can't make any partitions either, and it gives this warning when running the command:

[IMG]https://i.imgur.com/DmRcD6E.png[/IMG]

---

### Post by oldfred on 2017-11-25
If gdisk worked, I would have stopped there.
I think the cgdisk is intended more for scripts.

---

### Post by m3tax on 2017-11-25
Never mind, a quick restart seemed to fix everything. So, you mentioned creating a bios_grub file and an ESP file alongside the swap, /, and /home partitions earlier. How would I do this with gdisk?

---

### Post by oldfred on 2017-11-25
I have not used gdisk, but gparted.
But the code in gdisk is ef00 for the ESP and ef02 for the bios_grub partition.

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   EF00  efi
   2         1026048         1030143   2.0 MiB     EF02  
   3         1030144        52229362   24.4 GiB    8300  trusty
   4       246163456       250068991   1.9 GiB     8200  
   5       223791104       246163455   10.7 GiB    8300  iso_ssd
   6        52230144       103429362   24.4 GiB    8300  xenial
   7       103430144       163641081   28.7 GiB    8300  bionic

```

       GPT fdisk Tutorial - user srs5694 in forums
[http://www.rodsbooks.com/gdisk/walkthrough.html]("http://ubuntuforums.org/showthread.php?t=1439794")
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by photonxp on 2017-11-26
Sometimes when I don't know the cause of an OS-related problem, I'd like to start again from the very beginning, which is to **erase the whole disk (including the partition tables)** after re-plugging it to another well-working computer with an external hard drive case. You could also use dd command if you're familiar with it.

This way I guess it helps removing the potential remaining data on the first few blocks or bytes of the disk when trying to install the OS. Some partitioning tools may have their limits in this kind of job, though I'm not quite sure about this. Then do a disk check if that's possible. I'd also tend to use the partitioning tool provided by ubuntu's built-in  insallation tool, to avoid possible compatibility issues with other  partitioning tools.

It's probably not a golden rule, but it did save me out of some weird troubles with OS-installing problems.

As for the "force uefi installation" option, I also encountered it once when I tried to install ubuntu 16 from a 12-based drive. I chose to ignore it, hit continue and the ubuntu works well after installation. But this choice may not work in other situations. Check the bios settings first.

---

### Post by m3tax on 2017-11-26
This should be good, right? 

[IMG]https://i.imgur.com/q8RZ0Co.png[/IMG]

Also, how do I actually install Ubuntu on it after this? Just with the normal installation?

---

### Post by photonxp on 2017-11-26
Type code **8300** should be OK for partition number 4 and 5.

But type code **8302** and **8304** are probably seldom seen in most installations perhaps because they're more of a concept/protocol under development. According to the specific [answer here]("https://askubuntu.com/questions/703443/gdisk-hex-codes"):
> they're part of the [Discoverable Partitions Specification]("http://www.freedesktop.org/wiki/Specifications/DiscoverablePartitionsSpec/"), which is a Freedesktop/systemd initiative ... Currently, Ubuntu is just using the main Linux filesystem type code (**8300** in GPT fdisk) for filesystems

---

### Post by oldfred on 2017-11-26
You need to use Something Else (change button) to manually choose / partition, format as ext4 & format box. Same with /home except of course use as /home. But if reinstalling when you have data in /home you must be careful NOT to check the format box.
It finds swap automatically.
With 17.04 and later, they have changed from swap partition to swap file, but if swap partition found then it will be used.

Shows partitioning screen, and if partitioned in advance you choose a partition and click on change button.
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by m3tax on 2017-11-27
So I tried to install it by doing what oldfred said, but I got this error after the partitioning step:
[IMG]https://i.imgur.com/11PIMCk.png[/IMG]

I chose to continue, then it started installing but it got stuck at creating the ext4 partition for /home. After stopping the install and restarting the live session, the ext4 partitions for / and /home weren't associated with / and /home, which is pretty weird. They also have something on them from the previous installation.
[IMG]https://i.imgur.com/Qusv2ri.png[/IMG]

I changed them to / and /home and hit Next, got the same EFI error, continued anyway, and this time the installation doesn't even have a progress bar so I'm not sure if it's making any progress, but I'll let it run for a while.

[IMG]https://i.imgur.com/EaJsuHE.png[/IMG]

---

### Post by oldfred on 2017-11-27
I think you should have progress bar.

Did you format ESP as FAT32 and add boot flag? It looked correct in post #12.

If you formatted with gparted, you do not have to check the format box, sometimes called a "dirty" install but it would keep any files you added, but overwrite with an all new install. Used more when /home is inside / and you cannot specify format separately.

I install from HDD using grub2's loopmount and toram boot parameter so installer is all in RAM. And an install to SSD then takes less than 10 min. Progress bar moves very fast. My install to a USB3 flash drive takes close to an hour, so drive performance makes a huge difference in the install speed.

---

### Post by m3tax on 2017-11-27
I just cancelled the installation again. Fortunately, gparted seems to work now.
Looks like the EFI partition didn't work  because it wasn't formatted to fat32 - fixed that. Do I need to format the bios_grub file to anything? It still shows that red "!" sign next to it.

[IMG]https://i.imgur.com/oOnXWuE.png[/IMG]

---

### Post by oldfred on 2017-11-27
Gparted always shows bios_grub as error as it is unformatted. Same with Windows required system recovery partition as it is unformatted.
But both types of partitions are defined with GUIDs, so gparted should not be showing error on those types of unformatted partitions.

---

### Post by m3tax on 2017-11-27
Done! Installed with no errors. Thanks so much for the help, oldfred. :D

---

### Post by photonxp on 2017-11-28
I would just use [Something Else] without using [Ubuntu Live's GParted] when the disk is in good condition.
Here is what the partitions of efi and biosgrub  may look like in [Ubuntu Live's GParted] and [Something Else] when these special partitions are both used:

> efi partition:
____ Gparted:
________ partition type: fat32 
________ flag: esp, boot
________ size: 512 M or more
____ Something Else:
________ partition type: EFI (EFI System 32)

biosgrub partition:
____ Gparted:
________ partition type: unknown (not to set any format), with exclamation mark (!)
________ flag: bios_grub
________ size: 1~2 M
____ Something Else:
________ partition type: biosgrub (Reserved BIOS boot area)

And in gdisk:
>     efi partition:
____ type code: EF00

    biosgrub partition:
____ type code: EF02

---

