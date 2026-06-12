---
title: "Win 7 boot hosed by Ubuntu install"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by matt h on 2011-07-17
I installed 11.04 last night and ran into some trouble with partitioning, which froze my installation. Something about that seems to have borked my \boot\bcd configuration data, because I have since been unable to boot to windows.

I did ultimately get a successful install of 11.04 running (by letting it choose auto partitioning), but still can't get the Windows 7 installation to run. 

Grub boots fine, but I get an error as above about boot\bcd still. The windows install disk also refuses to run system recovery. 

Oh, this is on a 64 bit machine, FIW

Any suggestions?

TIA!

---

### Post by garvinrick4 on 2011-07-17
In Ubuntu open a terminal and run:
```
sudo update-grub
```
reboot and see if can boot into Windows:
If not:
Install windows bootmanager as per below:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
Now install ubuntu's grub2 back into place as instructed above:
Boot into Ubuntu and open a terminal and:
```
sudo update-grub
```
Now should have grub2 installed in mbr and able to boot both windows and linux.

##If you want to have a full look at your boot files run this script and post here:

[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by matt h on 2011-07-17
Thanks very much...I will try that.

---

### Post by matt h on 2011-07-17
OK, tried step 1, which did not improve anything. 

Step 2 relies on me being able to click on "Repair your computer" after booting from the Win7 install DVD. That returns a message about having the wrong version of Windows. Of course that's not true. Looking around, the only other explanation I've found for that msg is either a RAID setup or the wrong language selected, neither of which are true, AFIK. 

So I am a bit stuck.

---

### Post by garvinrick4 on 2011-07-17
Download and burn a repair disk and make sure you get the right architecture (32 or 64 bit)

Windows 7 and Vista repair disks.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by matt h on 2011-07-17
> **garvinrick4 said:**
> Download and burn a repair disk and make sure you get the right architecture (32 or 64 bit)

Windows 7 and Vista repair disks.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Thanks, tried that (and verified that it was the 64 bit version) and got the same result as I did with the Windows install disk (ie, couldn't run system recovery--it claimed I had an incompatible version). Any other thoughts?

---

### Post by matt h on 2011-07-17
> **matt h said:**
> Thanks, tried that (and verified that it was the 64 bit version) and got the same result as I did with the Windows install disk (ie, couldn't run system recovery--it claimed I had an incompatible version). Any other thoughts?

OK. Now I am feeling really screwed. I decided to back up my data and reinstall Windows. What happens is that the Windows installer says that I can't install to the disk (the one Windows was installed on already), because it's GPT.

I'm a little perplexed, as my recent actions, AFIK, did not change the disk from MBR to GPT. And my MB supports GPT, and Windows is alleged to support it with compliant MBs. I have my BIOS set to automatically choose EFI or not; when I forced EFI, things were even worse (I think the Windows installer did not recognize the disk).

---

### Post by matt h on 2011-07-17
I did a little reading on MBR vs GPT, and that suggested a direction, but I'm not sure if it's valid.

One difference between the two file systems is that GPT allows more than 4 primary partitions. 

The only change that occurred, that Windows could see, when I installed Ubuntu the first time is that I created a number of partitions. Even now, I think I have 5 primary partitions. I wonder if reducing to four would allow life to go on?

---

### Post by garvinrick4 on 2011-07-17
I have only worked with basic maybe someone will come along that has worked
in dynamic's.

---

### Post by srs5694 on 2011-07-17
I *think* I know what happened to you, but I'm not 100% positive of this:


[LIST=1]
[*]Your motherboard has UEFI firmware. (Your claim that the "MB supports GPT" implies this under most interpretations.)
[*]Windows was installed using UEFI mode rather than BIOS compatibility mode. This means that Windows used GPT and created a ~100 MiB FAT-32 EFI System Partition (ESP).
[*]When you installed Ubuntu, it erased the valid FAT-32 ESP and created a FAT-16 ESP in its place. This is a [known bug in the Ubuntu installer.]("https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669") The result is that Windows will stop booting.
[*]When you attempted to fix and then re-install Windows, you did it two ways, which had two different negative consequences:
[LIST]
[*]On your first attempt, the computer booted the disc in BIOS mode rather than in UEFI mode, which made Windows refuse to touch the GPT disk. This happened both with your repair attempt and with your re-installation attempt.
[*]On your second attempt, you forced UEFI mode; but Windows flaked out when it saw the FAT-16 ESP that Ubuntu created. Windows really wants to see a FAT-32 ESP.
[/LIST]
 
[/LIST]


If you want further verification, please post the output of the following two commands:

```

sudo parted -l
df -h

```This will reveal how your disk is partitioned and what partitions are in use. If Windows installed in UEFI mode, there will be "fingerprints," such as a ~100 MiB ESP. If, however, something else happened, like if Ubuntu created a new GPT and trashed a Windows-created MBR partition table, then the disk will look different -- it'll have a BIOS Boot Partition or an ESP that would be some size other than ~100 MiB.

The solution, if I'm correct, is as follows:


[LIST=1]
[*]Boot Ubuntu and back up the ESP. It should be mounted at /boot/efi, and it should have a subdirectory called EFI (or efi) with at least one more subdirectory (called ubuntu). It's very small; you can just back it up on your local hard disk.
[*]Unmount the ESP ("sudo umount /boot/efi").
[*]Create a new FAT-32 filesystem on the ESP using GParted. The ESP will probably be /dev/sda1, and it will be marked as having the "boot flag" set. After you create a new FAT-32 filesystem on the partition, the "boot flag" will probably be cleared, so you should restore it. (Alternatively, you could do this job with mkdosfs, as in "sudo mkdosfs -F 32 /dev/sda1; but you must be sure that it's /dev/sda1 you want to erase!)
[*]Type "sudo blkid /dev/sda1" (or whatever the device filename is). This will return the partition's "UUID" (actually a non-UUID serial number), among other things.
[*]Edit /etc/fstab and change the "UUID" value for the /boot/efi partition to the new one you just found.
[*]Type "sudo mount -a".
[*]Type "df" and verify that the /boot/efi partition has been mounted correctly. If not, troubleshoot before proceeding -- maybe you copied the UUID value wrong, for instance.
[*]Restore the Ubuntu files to the ESP and verify that they're in the right place.
[*]Run the Windows repair or installation disc, being sure that it boots in UEFI mode, not BIOS mode.
[*]Repair or re-install Windows.
[/LIST]


It's conceivable that you could skip most of the procedure and just do the last two steps if you do a repair and not a re-install; I don't know how fussy the Windows repair tools are about the FAT size of the ESP, although I know that the installer is very fussy about this. Certainly it's worth trying this at least once, if you haven't done so already.

I realize this sounds scary, but the goal is just to convert the ESP from FAT-16 to FAT-32 and then let Windows do its repair. Unfortunately, this means you've got to back up and restore data and edit /etc/fstab.

If you have to go through the whole procedure, be sure to keep an eye on the Ubuntu bug and be sure it's fixed before re-installing or upgrading Ubuntu in the future. Also, keeping a backup of the ESP is in order; if something like this should happen in the future, you'll be able to restore the backup relatively easily.

---

### Post by srs5694 on 2011-07-17
> **matt h said:**
> One difference between the two file systems is that GPT allows more than 4 primary partitions. 

The only change that occurred, that Windows could see, when I installed Ubuntu the first time is that I created a number of partitions. Even now, I think I have 5 primary partitions. I wonder if reducing to four would allow life to go on?

No -- at least, not if it really is a GPT disk. As you say, GPT allows more than four "primary" partitions (in quotes because "primary partition" is an MBR concept that's meaningless in GPT). In fact, if it were an MBR disk and you used Windows tools to create more than four partitions, I'd expect problems with booting Linux, not with booting Windows.

---

### Post by matt h on 2011-07-18
> **srs5694 said:**
> I *think* I know what happened to you, but I'm not 100% positive of this:


[LIST=1]
[*]Your motherboard has UEFI firmware. (Your claim that the "MB supports GPT" implies this under most interpretations.)
[*]Windows was installed using UEFI mode rather than BIOS compatibility mode. This means that Windows used GPT and created a ~100 MiB FAT-32 EFI System Partition (ESP).
[*]When you installed Ubuntu, it erased the valid FAT-32 ESP and created a FAT-16 ESP in its place. This is a [known bug in the Ubuntu installer.]("https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669") The result is that Windows will stop booting.
[*]When you attempted to fix and then re-install Windows, you did it two ways, which had two different negative consequences:
[LIST]
[*]On your first attempt, the computer booted the disc in BIOS mode rather than in UEFI mode, which made Windows refuse to touch the GPT disk. This happened both with your repair attempt and with your re-installation attempt.
[*]On your second attempt, you forced UEFI mode; but Windows flaked out when it saw the FAT-16 ESP that Ubuntu created. Windows really wants to see a FAT-32 ESP.
[/LIST]
 
[/LIST]


If you want further verification, please post the output of the following two commands:

```

sudo parted -l
df -h

```This will reveal how your disk is partitioned and what partitions are in use. If Windows installed in UEFI mode, there will be "fingerprints," such as a ~100 MiB ESP. If, however, something else happened, like if Ubuntu created a new GPT and trashed a Windows-created MBR partition table, then the disk will look different -- it'll have a BIOS Boot Partition or an ESP that would be some size other than ~100 MiB.



Here's the output, which, if I understand what you said, suggests that Windows was installed in UEFI mode:

Model: ATA Hitachi HDS5C302 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      20.5kB  210MB   210MB   fat32           EFI System Partition  boot
 2      211MB   500GB   500GB   ntfs            Basic data partition
 3      500GB   500GB   1000kB                                        bios_grub
 4      500GB   1992GB  1492GB  ext4
 5      1992GB  2000GB  8572MB  linux-swap(v1)

(I'm not including sdb, which is a Mac install and data)

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4             1.4T   17G  1.3T   2% /
none                  3.9G  784K  3.9G   1% /dev
none                  3.9G  272K  3.9G   1% /dev/shm
none                  3.9G  220K  3.9G   1% /var/run
none                  3.9G     0  3.9G   0% /var/lock
/dev/sdc1             932G  931G  1.2G 100% /media/Backup 2
/dev/sdb3             233G   12G  221G   6% /media/DATA 2

---

### Post by srs5694 on 2011-07-18
There are four complications in your output:


[LIST]
[*]/dev/sda1 is ~200 MiB, rather than ~100 MiB. Windows tends to create a ~100 MiB ESP, not a ~200 MiB ESP. Mac OS X, however, tends to create a ~200 MiB ESP.
[*]/dev/sda1 is identified as having a FAT-32 filesystem, not the FAT-16 filesystem that my initial hypothesis specified.
[*]/dev/sda3 is a BIOS Boot Partition (identified in parted as having a "bios_grub" flag). This is inconsistent with the idea that Ubuntu installed in (U)EFI mode; however, it could have gotten there because you mistakenly believed it was necessary and so created it or because some automated tool created it unnecessarily.
[*]There's no hint that the ESP is currently mounted in Ubuntu, which is inconsistent with an Ubuntu UEFI-based installation.
[/LIST]


Therefore, I now believe that my initial hypothesis was incorrect. My new hypothesis is this:


[LIST=1]
[*]You're either using an Apple Macintosh or did a "Hackintosh" installation. Either way, the result was a GPT disk with a [hybrid MBR]("http://www.rodsbooks.com/gdisk/hybrid.html") on /dev/sda. Note that discussion of "Hackintosh" installations is frowned upon by this forum's moderators, but it's unclear if you've got that or a "real" Apple Mac; and the outlines of the solution are the same either way.
[*]You installed Windows to an NTFS partition on /dev/sda. Windows relied on BIOS-style booting and the hybrid MBR.
[*]You installed Ubuntu in BIOS mode, which wiped out the hybrid MBR and created a legal protective MBR in its place. This rendered Windows unbootable and unrepairable by the standard Windows tools.
[/LIST]


If this new hypothesis is correct, you have at least two, and possibly three or more, options for how to proceed:


[LIST=1]
[*]Use gptsync, [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/"), or some other tool to create a new hybrid MBR. You might then be able to boot Windows from GRUB if there's a GRUB entry, or you might need to run the Windows repair utility to render Windows bootable again. The latter might render Linux unbootable, though, at least until you re-install GRUB.
[*]Use my [GPT fdisk (gdisk)]("http://www.rodsbooks.com/gdisk/") to convert /dev/sda from GPT to MBR format. This is preferable to using a hybrid MBR, IMHO. Also, you've got five partitions on there right now, and depending on whether there are gaps between them, you might not be able to fit them all into an MBR partition table. You could probably drop the ESP without harm, though. You'll need to re-install GRUB, and you may need to run the Windows repair utility to render Windows bootable again, as in option #1.
[*]If you're using a non-Mac PC with UEFI support, you can follow the procedure described [here]("https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI") to convert Windows to boot in UEFI mode. (Fortunately, most of that's already done; you'll need to do steps 3.1, possibly 3.2, and 3.5 through 3.7.) If your firmware really is UEFI-enabled, this should work; but if you've actually got a conventional BIOS or a Mac, this procedure will not work. Depending on how your firmware handles switches between UEFI and BIOS boot modes, you might also need to convert your other OS(es) to boot in UEFI mode (for Linux, this involves installing a UEFI-capable Linux boot loader on the ESP; I recommend [ELILO,]("http://elilo.sourceforge.net/") although the Ubuntu grub-efi package will install a UEFI version of GRUB 2).
[/LIST]


Option #1 is the easiest and most likely to work in the short run, but it will leave you with a hybrid MBR, which is flaky and dangerous, as you've discovered. Option #2 is slightly harder and riskier in the short run than option #2, but it's safer and preferable to option #1 in the long run. If your computer really is a UEFI-enabled PC, option #3 has long-term advantages because UEFI and GPT support will be increasingly important in the future; but it's the most hassle to set up in the short term. It also won't work with a real Mac.

If you want more advice, please post what make and model computer or motherboard you're using. There are three basic classes here that determine capabilities: Macs, BIOS-only PCs, and UEFI-enabled PCs.

---

