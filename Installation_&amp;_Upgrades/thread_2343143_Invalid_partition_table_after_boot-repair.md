---
title: "Invalid partition table after boot-repair"
date: 2016-11-13
forum: Installation &amp; Upgrades
---

### Post by ahtur on 2016-11-13
Hello everyone. I had to reinstall windows 7 on a computer that already had a dual boot. Then I ran boot-repair ("recommended" button) from a ubuntu live CD in order to make grub show up again at startup. However, now I first get a "Invalid partition table!" message and have to press Enter to skip it and make grub show up. This happens even when I explicitely choose in bios to boot from the ssd drive where windows and linux are installed (sdb). Bios is in legacy mode btw. Could you please help me get rid of this message ? My boot-repair report is here : [http://paste.ubuntu.com/23473151/](http://paste.ubuntu.com/23473151/).

---

### Post by oldfred on 2016-11-14
How did you partition and install to sdb?

Your first partition starts at sector 63. But all new partitioning tools start first sector at 2048. I think Windows started with Windows 7 installer and Ubuntu/Linux installers & gparted changed soon after Windows 7 did change. Only XP installer still used sector 63.

       Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
sudo parted /dev/sda unit s print
sudo parted /dev/sda align-check opt

---

### Post by ahtur on 2016-11-14
Hi oldfred and thanks for trying to help me. Please note that I have very weak knowledge in this area.

When I bought the computer 4 years ago, windows was installed on the sdb drive while sda has always been a single partition data drive. Using either the windows disk manager or EaseUs (can't remember well), I shrunk the windows partition down to 100GB, created a small (100GB) "production" data partition for work and installed ubuntu in the remaining space with a ubuntu DVD. Please note that things went absolutely fine for these 4 years and I didn't do any other manual reparitioning ever after. The problem appeared recently, after I reinstalled windows in its own partition (no error messages just after that, but no grub anymore either) and ran boot-repair with recommended settings. I'm not aware of any repartioning during this operation. Is it possible that boot-repair does not support my old partitioning scheme ? 

Here are the results of the suggested commands :

sudo parted /dev/sda unit s print

```
Modèle: ATA ST9750420AS (scsi)
Disque /dev/sda : 1465149168s
Taille des secteurs (logiques/physiques): 512B/4096B
Table de partitions : msdos

Numéro  Début  Fin          Taille       Type     Système de fichiers  Fanions
 1      8192s  1465139199s  1465131008s  primary  ntfs
```

sudo parted /dev/sda align-check opt

```
Numéro de partition ? 1                                                   
1 aligned

```

But please note that the "invalid partition table" message arises event when sda is not among the boot drives so may be we should focus on sdb. Do you see any workaround ? Would formatting and reinstalling the ubuntu part of sdb even fix the problem ?

---

### Post by oldfred on 2016-11-14
Issue is more with sdb as that is the unaligned drive.
Run the align command on all your sdb partitions.

When you have two drives, typically better to keep Windows on first drive or sda. And then install Ubuntu on second drive.
Then each system can have its boot loader in the MBR of that drive (for BIOS systems).

But difficult to redo now, so should be ok other than partition issues.
Do you know if somehow partitions got moved, or have back up showing old info?
Windows 7 would never be in a drive starting at sector 63, unless in upgrade from XP.

---

### Post by ahtur on 2016-11-15
> **oldfred said:**
> 
Run the align command on all your sdb partitions.

It says sdb 1, 4 and 5 are not aligned. The others are.

> **oldfred said:**
> 
When you have two drives, typically better to keep Windows on first drive or sda. And then install Ubuntu on second drive. Then each system can have its boot loader in the MBR of that drive (for BIOS systems).

I'm the kind of guy who puts the OSs on the SSD and keeps the large drive for storage. I thought that was good practice.

> **oldfred said:**
> 
Do you know if somehow partitions got moved, or have back up showing old info?
I'm not aware of any repartitioning after the initial one I did 4 years ago. Turns out I have a boot info that I've manually generated just before running the boot-repair : [http://paste.ubuntu.com/23473141/](http://paste.ubuntu.com/23473141/). No invalid partition table message back then.

Would it have something to do with boot-repair moving the boot flag to a logical partition ?

---

### Post by oldfred on 2016-11-15
If sdb is SSD then better to have systems installed to it.
But normally you install SSD to sda, which when building system means it is plugged into SATA0.

Probably older report did not show error as 4 years ago or even until recently it was not a major issue. Only a few SSD or newer larger HDD with 4K sectors.

You cannot easily move Windows. It has vital boot info in partition boot sector PBR, that must match partition table. Moving Windows typically breaks it, but usually but not always chkdsk can fix it. Good backups required.

So your choice is to leave it, but it has to in many cases read two sectors when optimum configuration would only require reading one. Or system will be slower & trim has to clear two blocks when released. And therefore increased wear or shorter life. But your SSD will still be faster than HDD.
Other choice is full backup & reinstall of Windows which is a lot of work. 

If SSD is 4 years old, I might start thinking about a new drive anyway. I normally keep drives, but once they are over 3 years old of full use as main working drive, change to a new main working drive and reallocate older drive to backup or part time use. Even if warrantee is 5 years. Many older drives only had 3 year and some only one year warrantee.

---

### Post by ahtur on 2016-11-15
> **oldfred said:**
> 
Probably older report did not show error as 4 years ago or even until recently it was not a major issue.
If you're referring to [http://paste.ubuntu.com/23473141/](http://paste.ubuntu.com/23473141/), this was was done like 2mn before the "after boot-repair" report [http://paste.ubuntu.com/23473151/](http://paste.ubuntu.com/23473151/). boot-repair made the "invalid partition table" message appear. [COLOR=#000000]Would it, for example, have something to do with boot-repair moving the boot flag to a logical partition ?[/COLOR]

Could you please clarify the cause of the error according to you ? I don't mind reinstalling windows, I have a fresh install anyway. It will probably be fine until I try to restore grub and make the story repeat itself.

---

### Post by oldfred on 2016-11-15
As far as boot flag goes, Boot-Repair often moves it incorrectly. We probably should provide a bug report to Boot-Repair.
Boot flag is not used by grub. It is used by Windows and syslinux.
And Windows will not install into, boot from, nor repair a NTFS partition if boot flag is not on NTFS partition with Windows boot files, if BIOS.

I think, but do not know for sure that it is the alignment that you confirmed is not correct.

---

### Post by ahtur on 2016-11-15
> **oldfred said:**
> As far as boot flag goes, Boot-Repair often moves it incorrectly. We probably should provide a bug report to Boot-Repair.
Boot flag is not used by grub. It is used by Windows and syslinux.
To be clear, what part of the system issues an "Invalid partition table!" message ? Grub, BIOS, ... ?

> **oldfred said:**
> 
And Windows will not install into, boot from, nor repair a NTFS partition if boot flag is not on NTFS partition with Windows boot files, if BIOS.
So I definitely should put this flag back on the windows partition in case I need to reinstall windows someday, right ? Grub would still show up if installed in the MBR as states line 9, right ?

> **oldfred said:**
> I think, but do not know for sure that it is the alignment that you confirmed is not correct.
In that case, what would be the solution, please ? Formatting the whole sdb ? Or some partitions of it ? (which ?)

---

### Post by oldfred on 2016-11-15
Probably best to totally repartition. Not easy to move start of partitions by a few sectors.
But I thing gparted may have an align command, but if you run that you may break things particularly Windows.
So good backups, a Windows repair disk as Boot-Repair can only fix minor issues with Windows and be prepared.

And first move boot flag back to sdb2. You can use gparted or the same command Boot-Repair posted.
This is line 920 in report where it moved to to sdb6. You would need sudo and use 2 in place of 6. Then confirm with new partition listing.
parted /dev/sdb set 6 boot on

sudo parted -l

---

### Post by ahtur on 2016-11-16
The "Invalid partition table!" warning has gone after moving the boot flag back to the physical sdb2 partition. So it was not an alignment issue after all.

Thank you so much for your time and advice, oldfred. And yes, you definitely should report a bug to boot-repair's developer.

Last question (hopefully) : Please, what are the steps to remove the extra entry for "Windows 7 Loader" that boot-repair has added to the grub menu ?

---

### Post by oldfred on 2016-11-16
So many users do not know in BIOS the 100MB Windows boot partition has essential boot files. So Boot-Repair started to copy boot files from Windows Boot partition into the main Windows partition. And Windows only uses Boot-Flag to know which partition to boot from which must have those boot files. 
But grub2's os-prober does not use boot flag and searches for those boot files and then adds those partitions to grub menu. It does allow direct booting of multiple Windows installs.

You can turn off os-prober and copy the Windows boot stanza you want into 40_custom.
       Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
or
sudo nano /etc/grub.d/40_custom

# then turn off os-prober by adding a line to grub configuration file
sudo nano /etc/default/grub
GRUB_DISABLE_OS_PROBER=true 
Then do:
sudo update-grub

---

