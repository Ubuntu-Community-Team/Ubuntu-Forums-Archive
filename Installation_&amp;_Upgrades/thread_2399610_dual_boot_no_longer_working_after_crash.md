---
title: "dual boot no longer working after crash"
date: 2018-08-27
forum: Installation &amp; Upgrades
---

### Post by scags9876 on 2018-08-27
Here is my boot-repair info:  [http://paste.ubuntu.com/p/p9hPH8FvfK/](http://paste.ubuntu.com/p/p9hPH8FvfK/)

I had my system dual boot working like a charm.  One 2TB disk.  
 - 300 GB partition for windows 10
 - 175 GB partition for ubutu 18.04
 - the rest an ntfs partition for shared data between the 2 os's

I had disabled Fast Startup in Windows 10 already  (maybe some windows update turned it back on without me knowing?)

Windows and Ubuntu were installed with UEFI boot, grub would always load up and default to Ubuntu.

Today, a game froze on the Windows OS.  I did a hard restart and now the system will not boot.

It goes to a "EFI Shell Version" info screen.

Starting up my live session ubuntu via dvd drive, boot-repair fails with an error:
  - GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag).
However, I don't want bios mode booting.. I want EFI back.

I tried to repair windows with the windows installation DVD, but it just says 'Cannot repair windows'.

I notice in the boot-repair info from the pastebin above, it says:
 - Grub-efi would not be selected by default because: no-win-efi
So is this because efi booting is all messed up for my windows installation?  Is there a way to fix this other than reinstalling windows?

Thank you for any help you can give

---

### Post by westie457 on 2018-08-27
Hello scags9876
Boot your Windows install media and at the 'Install Now' screen click on 'Repair my computer'.
Go to the advanced options and select 'Command Prompt' and run these commands.```
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd
exit
```
Reboot the system hopefully to Windows only or the Grub menu.

If that does not work we get technical with it.
In the Boot report the 'EFI' partition has lost its uuid number, even though it is listed in your '/etc/fstab'.
There is probably a way of forcing that id back onto the partition, I have not looked for that solution yet.

Let us know how it goes.

---

### Post by scags9876 on 2018-08-27
Thanks for the reply @[COLOR=#000000]westie457 !

[/COLOR]Following your directions, I get an error with the rebuildbcd command.  After I answered Yes to "Add installation to boot list?" for D:\Windows (this used to be C:\Windows btw),
It replies with 

```

The requested system device cannot be found

```

In fact, in diskpart utility on the windows setup cd, it does not see the disk at all.  `list disk` only sees the dvd disk, not the hdd at all.

---

### Post by scags9876 on 2018-08-27
gparted can see the disk though... and yes, it shows the 2 special partitions that windows 10 install made without a UUID:
[ATTACH=CONFIG]280870[/ATTACH]

---

### Post by oldfred on 2018-08-27
The red exclamation error in gparted on sda3, the system reserved is normal. Gparted does not like that it is unformatted, but that is required. Windows System Reserved partitions have an unique GUID, so gparted should know unformatted is required on that partition.

But error on sda2, your ESP - efi system partition is a problem. Your forced shutdown probably corrupted it.
You may be able to run chkdsk from a Windows repair disk.
Or run dosfsck on that partition:
 [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by scags9876 on 2018-08-27
Thank you oldfred!

running dosfsck gave me the following error:

```

~$ sudo dosfsck -t -a -w /dev/sda2
fsck.fat 4.1 (2017-01-24)
Logical sector size (35701 bytes) is not a multiple of the physical sector size.

```

Also tried chkdsk from command prompt with the windows setup disk, on C:/ D:/ and E:/ it ran fine and reported no problems.

---

### Post by oldfred on 2018-08-27
You have to manually mount the ESP in Windows as it is not shown as a standard partition. Not sure of details.

New drives are now 4K physical and logical sector size is 512.
Not sure how to correct that issue?

Some in past have had totally corrupted FAT32 partition. They backup files (if possible) and delete partition, recreate new FAT32 partition with ESP and boot flags and restore data.
If you cannot restore data you have to reinstall boot loaders.
Westie457's post #2 above, should update Windows.
And you can use Boot-Repair to do a full uninstall/reinstall of grub. 
That should restore normal boot files into ESP.

---

### Post by scags9876 on 2018-08-29
Thank you oldfred and Westie457 ! My problem is now solved.

Using gparted, i removed the EFI System Partition /dev/sda2 (could not back them up first)
then created a new partition in that spot, formatted as FAT32, added the same label that was there before and the `boot, esp` flags
Then, i did the bootrec steps that Westie suggested above:
 - first i had to assign the efi partition a drive letter
 - then go to that drive to run the bootrec commands
 - and lo and behold the computer booted right into Windows.
Loaded up my ubuntu livesession, ran boot repair, it completed successfully (details here: [http://paste.ubuntu.com/p/vGS863RS9f/](http://paste.ubuntu.com/p/vGS863RS9f/) )
Then, upon boot of computer it went back right into windows... no grub :(

So, back in windows in an admin command prompt, I had to run bcdedit to point to the grub boot manager (as it says at the end of the pastebin from boot-repair, also described here: [https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/) )

So then, finally grub is back!  :yay:

However, my ubuntu kept loading up into 'emergency mode'.. i couldnt reset it.  As this is a pretty new installation, i just reinstalled ubuntu there, not formatting the partition so all my previous things were still in this new installation.

anyways, i'm back to normal, thanks so much for your help

---

### Post by scags9876 on 2018-11-16
This happened again to me :(   Luckily I detailed all the steps to fix it here.  I'm going to try to see if this works for me again.

---

