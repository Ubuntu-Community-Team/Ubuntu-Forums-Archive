---
title: "Problem with installation on USB-HDD"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by ymilev on 2013-04-04
Hello!
Recently bougth new USB 3.0 HDD, and want to install Ubuntu on it. Already have experience with installation on "normal" HDD, and some months before installed on USB drive Mint 14, so I expected to be the same procedure with the portable HDD. As far as I read this thread
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
I saw that the procedure is the same, I used to install Mint on USB flash.
The only difference is that on flash installation I formated the whole drive and did "clear" install, and now I just shrinked the only partition on the drive, and created ext4 partitions for / and /home, so as swap partition. For installation I used LiveUSB
On installation the disk had following partitons:
sdc1 - ntfs - 690 MB
sdc2 - ext4 - 8 GB - /
sdc3 - swap - 1GB
sdc4 - ext4 - 8 GB - /home
Chose to create boot on sdc - Toshiba USB3.0 750 GB ( the new drive)
Installation was uneventfull, but when I tried to reboot, black screen with message:
grub-rescue > No file found
grub-rescue> _
Tried again instalation, with location for bootloader: dev/sdc2 with the same result
I noticed tha in GParted NTFS partition beared the flag "boot" so removed it. On new installation already boot flag was on sdc2 (dont't remember the result), then tried to move the partitions and placed ext4 partitions in the beginning of the disk.
Finally got working and booting system, but now NTFS partition is not visible in Windows 7. Strange, that the drive is visible in Device manager, but not usable by windows explorer. It is also visible and usable in Windows XP, but not on Win 7
Finally Formatted the drive and started again. Same result with installing Mint 14
Could you advise me, what I'm doing in the wrong way? Is there a way to get booting external HDD with accessible under Windows NTFS partition on it?
I had the same problem with USB flash drive - After Mint installation, the rest of the disk - FAT system was not visible by Win7, but for the small drive it was not a problem just dedicated this partition for Linux

---

### Post by oldfred on 2013-04-04
Grub does not use boot flag, but a few systems have BIOS that only let you boot if you have a boot flag on a primary partition. So make sure you have a boot flag on sdc1 thru sdc4 any one of your partitions, and only one.

To boot from sdc directly, you have to install grub to sdc not any partitions like sdc2.

Do you have grub in sda or sdb? Then you may be able to boot from there?

Some BIOS just do not boot USB3 ports. Is your BIOS up to date?

---

### Post by darkod on 2013-04-04
The problem might be that the boot files are far from the beginning of the disk. You first have a 690GB ntfs partition.

Try making / to be first partition.

Also what can happen is that grub2 didn't install correctly on /dev/sdc. You can try adding only grub2 later, no need to reinstall the whole ubuntu. And grub2 needs to be on the MBR, /dev/sdc, like you tried the first time, not on sdc2.

---

### Post by ymilev on 2013-04-04
First I install grub on sdc, but it didn't worked
It is not a BIOS problem becouse finally I succeeded to get a booting external HDD, but then NTFS partition was not visible by Windows 7
Actually the computer has only USB 2 ports, so the device is working as USB2
sda is the internal HDD, on which I run triple boot system with Ubuntu 12.10, Win 7 and Win XP, so yes, it have grub on its MBR. I install first XP, 6 months later Win 7, and an year later Ubuntu 9.04, consequently regularly upgraded to 12.04, than reformatted ext3 partition with fresh 12.10 install. During this usage I have never had problems with accessibility of windows partitions.
sdb is the LiveUSB used for installation
Which ot the linux partitions have to be primary? Till now I used primary for root and swap, and logical for /home. Can / or swap be on logical partition?

---

### Post by sudodus on 2013-04-04
You did manage to make Ubuntu boot from the USB 3 drive. Try to recall what you did, and repeat it :-)

I know that Windows XP used to have problems to see more than the first partition on USB drives. But XP sees it and Windows 7 doesn't, although it is the first one (and a primary partition, I guess). Will it behave in a different way in another USB port (probably USB 2)? Or in another computer?

---

### Post by sudodus on 2013-04-04
None of the linux partitions need to be primary. But for bootability in some computers you need one primary partition with the boot flag, and it might as well be a FAT32 or NTFS partition. I have several computers, and I think only one of them needs this boot flag.

---

### Post by ymilev on 2013-04-04
As I said all the usb ports on my mainboard are USB 2.0. It doesn't support USB 3.0, although the drive is USB 3.0 - it is working in USB 2 mode
Last attempt was with all linux partitions on logical drives, located after the primary NTFS, that carried the boot flag. With this configuration Win (All versions) see the drive, but linux didn't boot
With confidence configuration with All primary partitions , situated in a row sdc2(/)-sdc3(swap)-sdc4(/home)-sdc1(ntfs) booted, but Windows 7 doesn't see any disk drive in My computer (although it appears in Device manager). When using ext2read.exe ext4 partitions are accesible.
 Win XP sees only ntfs partition which is normal.

---

### Post by darkod on 2013-04-04
I think only grub2 didn't install correctly on the MBR of /dev/sdc. Did you check that possibility? Did you run the boot info to check there is grub2 on sdc for example?

I have seen few threads here where 12.10 didn't install grub2 for unknown reasons.

---

### Post by oldfred on 2013-04-04
Back to Darko's comment on / (root) far into drive. I believe it has been only certain BIOS, but more often with USB drives. I might just create a small /boot partition at the beginning of sdc in sdc1. That may just be the entire issue.

---

### Post by Bashing-om on 2013-04-04
ymilev; Hi !

In addition to the excellent advise thus far, may I add to look and see where grub is installed: -> Be aware that if you can not boot into the present install, a change root procedure will have to be employed. These commands are only effective from the installed environment.

```
sudo grub-probe -t device /boot/grub
```
and confirmation in respect to "blkid":
```
sudo grub-probe -t fs_uuid /boot/grub
```
and to see what grub has done as far as installation configs:
```
sudo debconf-show grub-pc
```
And finally To find out the names of the menu items:
```
sudo grep menuentry /boot/grub/grub.cfg
```

These commands will tell a bunch about what is going on and what needs to be re-done. But maybe a bit extreme ??
[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by ymilev on 2013-04-04
OK, I would like to post you the output of this commands, but I cannot at all boot in this environment. The last attempt to install was with Mint 14 on logical partition, situated after the ntfs partition.
I think I can load now Mint, by updating grub, that is on my internal HDD, and booting from there, but I'm not sure that you mean this option. 
About /boot partition - I have no experience with this issue. What is the purpose of creating separate partition for this mountpoint, and what type it should be?

---

### Post by ymilev on 2013-04-04
So here provide booting configuration: Done now with Mint, but similar was working with Ubuntu
Moved ntfs partition, and created small primary partition at the very beginning of the disk sdc2 . Formatted it with ext4 and set mountpoint /boot.
It was followed by sdc1 - the big ntfs partition and then three logical partitions for the /, swap and /home.
I think the previous working installation was with all the linux partitions located at the beginning of the disk (with no separate /boot partition)
After moving the ntfs partition away from the beginning of the disk it is not longer seen by Windows 7, but seen by XP
Can someone help me with this issue or I should look for Windows forum ? ;)

PS What is the recomended size for /boot partition? I set 256 MB. Is it much ot less?

---

### Post by oldfred on 2013-04-04
256MB should be fine for /boot. Just as kernels get updated it will fill up, but you have room for many. Just plan on housecleaning occasionally. I like to houseclean kernels just so my grub menu does not get long. I normally keep the current and one old one just in case.

I do not know why XP would see a partition and Windows 7 would not see it. Did you run chkdsk from Windows 7 on the partition after you moved it?

---

### Post by ymilev on 2013-04-05
Will do this now.
I thing about possibility to move now the /boot partition again after the ntfs one. Then to reinstall GRUB. Do you thing this will make the system unbootable?

---

### Post by darkod on 2013-04-05
Yes, moving /boot at the end might break it, but you can try anyway. It looks like earlier the problem was exactly that, the ubuntu partition was at the back too far from the start of the disk.

Windows can be idiotic when it sees linux partitions, but on a usb hdd it should still see the ntfs partition regardless where it is. On usb sticks it can see only the first partition, that's a limitation of windows done on purpose by Microsoft. So, if you move ntfs partition to the back on a stick, it won't see it.

But the usb hdds use different driver that should let you read more partitions on it, not just the first, so the position of the ntfs partition shouldn't matter. I say shouldn't, but you know how it is with windows. :)

---

### Post by ymilev on 2013-04-05
Finally decided not to move anything but to try chkdsk under Windows. The problem appeared with the issue that if the drive is not seen in My computer, it has no letter assigned. So I went to Disk Management - the whole drive with all its partitions was seen, but none of them had letter. Option to assign letter was active only for the ntfs partition, and in 2 seconds, after assigning letter, the device appeared and got accessible.
So obviously the sloution has to be:
1) Not placing big partition before the root partition/or dedicate a small /boot partition in the very beginning of the volume, otherwise the system will fail to boot (message error: no such partition, followed by grub-rescue> waiting for command)
2) Visibility of the ntfs partition is restored by simply assigning a letter to the drive through Windows embedded tools (Disk management)
Thanks everybody for the help. Highly appreciate all the advice.
Now continuing with attempt to make visible the residual FAT partition of a USB-Flash installation :)

PS> How to change the status of the thread to SOLVED?

---

### Post by darkod on 2013-04-05
Since few weeks back the SOLVED option seemed to be broken. Not sure if it works, it should be in Thread Tools at the top of the page, above the first post on every page.

---

### Post by oldfred on 2013-04-05
See my signature below for the current work around on [SOLVED] until an add in is created for the new version of the forum.

---

