---
title: "Ubuntu Booting up in emergency mode"
date: 2019-09-27
forum: Installation &amp; Upgrades
---

### Post by thegoodstuff24 on 2019-09-27
My Specs:
Dell XPS 8930
Ubuntu 18.04 Dual Boot
Samsung 960 Evo (M2)

So my Motherboard failed recently and I had to replace it. Upon installing it and booting my grub menu no longer worked, it went right to windows 10.
I used boot-repair to resolve that and I tried to boot Ubuntu but I get the following errors:

[   0.056310] ACPI Exception: AE_BAD_PERAMETER, Could not install Pciconfig handler for root Bridge PCIO (20170831/evrgnini-245)
[   1.938421] Couldn't get size: 0x800000000000000e
/dev/nvme0n1p4: Clean, 573615/2564096 files, 8285104/10239744 blocks
Timed out Waiting for device dev-disk-by\x2uuid-042B\x2dFE10.device.

I looked at the blkid and compared the UUID to the one in etc/fstab and I am pretty sure they match correctly.
I also tried editing the grub menu config to:
 
[COLOR=#242729][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=strict"

[/FONT][/COLOR]and updated it but still no difference. I can also boot from a live USB (With the Ubuntu installer/ISO) with no issue.


Been struggling with this for a while, any thoughts or help would be appreciated.


EDIT:
Here is the requested boot-info Link:
[http://paste.ubuntu.com/p/5nJ8xYn7zb/](http://paste.ubuntu.com/p/5nJ8xYn7zb/)

---

### Post by Rubi1200 on 2019-09-28
Hi and welcome to the forums :-)

Best to see details from the boot info summary (first link in my signature).

Thanks.

---

### Post by thegoodstuff24 on 2019-10-02
Ok, I added it to my post.

---

### Post by thegoodstuff24 on 2019-10-03
My Specs:
Dell XPS 8930
Ubuntu 18.04 Dual Boot with Windows 10
Samsung 960 Evo (M2)

Just replaced my Motherboard that failed and now Ubuntu will not boot. I can still get to my grub menu and boot from Windows though, as well as a USB device.
Ubuntu however goes into emergency mode and gives the following errors:

[ 0.056310] ACPI Exception: AE_BAD_PERAMETER, Could not install Pciconfig handler for root Bridge PCIO (20170831/evrgnini-245)
[ 1.938421] Couldn't get size: 0x800000000000000e
/dev/nvme0n1p4: Clean, 573615/2564096 files, 8285104/10239744 blocks
Timed out Waiting for device dev-disk-by\x2uuid-042B\x2dFE10.device.

I tried Boot-Repair and a couple of other solutions but have had no luck. 
Here is my boot info:
[http://paste.ubuntu.com/p/5nJ8xYn7zb/](http://paste.ubuntu.com/p/5nJ8xYn7zb/)

Any assistance would be appreciated.

---

### Post by Dennis N on 2019-10-03
Because of the "Timed out Waiting for device..." message, check if the UUIDs in your /etc/fstab are actual system UUIDs given in lines 182-198 of boot repair output. Change the UUID in /etc/fstab to match so it can mount. Possibly the EFI system partition has wrong UUID.

---

### Post by thegoodstuff24 on 2019-10-03
Here is what I have in fstab:

[IMG]C:\Users\dfaulkner\Desktop[/IMG]


If the picture does not upload here is essentially what it shows:

ext4 (or /dev/nvmeonp4) UUID = 51792f78-d42b-4900-8b50-de7178762b7b

Compare that to line 185 and I believe that it is correct, so is there anything else I can check?

---

### Post by thegoodstuff24 on 2019-10-03
Just noticed this:
/dev/sda1: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"UBUNTU 18_0"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"15E2-0D5B"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR] [COLOR=#B8860B]PARTLABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Microsoft Basic Data"[/COLOR] [COLOR=#B8860B]PARTUUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"824d2a16-b1f3-4c69-9853-aac49fb1e20b"

That does not seem right to me. Is that the system partition?[/COLOR]

---

### Post by oldfred on 2019-10-03
Even if new motherboard, you may still need UEFI update.
Did you also update SSD firmware, make sure that is most current version.

And updating UEFI or new motherboard will reset many UEFI settings. So anything you changed before, you need to redo. I have 5 to 7 settings I change (some optional), so I keep a list.

Report shows issue with nvme0pn1p1 or first partition. Was that a Dell or Windows recovery partition, since ESP is p2?

Another Dell 8930.
        Installing Ubuntu 18.04.2 on Dell 8930 with dual boot win10
[https://ubuntuforums.org/showthread.php?t=2413145](https://ubuntuforums.org/showthread.php?t=2413145)

---

### Post by oldfred on 2019-10-03
Duplicate threads merged.

---

### Post by Dennis N on 2019-10-04
> If the picture does not upload here is essentially what it shows:

ext4 (or /dev/nvmeonp4) UUID = 51792f78-d42b-4900-8b50-de7178762b7b

Compare that to line 185 and I believe that it is correct, so is there anything else I can check?

That UUID is for the root partition, and that is correct. There should also be an entry in /etc/fstab to mount the EFI system partition. Use your live media to look again for an entry line mounting some partition at /boot/efi. Since the UUID in the error message doesn't exist, It may have the wrong UUID. (You can use code tags to format more clearly what you post.)
 
"Timed out Waiting for device dev-disk-by\x2uuid-042B\x2dFE10..."  is looking for UUID=042B-FE10, causing failure. No sign of that UUID in boot repair summary. 

I see no /boot/grub/grub.cfg menu entries from the NVMe drive - only sda. Grub seems not to be installed?

---

### Post by thegoodstuff24 on 2019-10-04
Grub is definitely installed and working fine, as far as I know. I can still boot to windows fine and at least select Ubuntu to boot from.

There indeed is a line for /boot/efi and is displayed as follows:

```
/swapfile                                                         none             swap   sw        0            0
           UUID=C7C9-45DF    /boot/efi            vfat       defaults        0          1 
```

That appears to match line 183. There is only one other UUID shown in the blkid:

```
UUID = 042B-FE10    /media/SHARED-WIN-LIN-600G    vfat       auto,user,uid=1000,gid=100,dmask=027,fmask=137    0       0
```

Not sure where that one fits in as it is not in the boot info logs.

---

### Post by thegoodstuff24 on 2019-10-04
Yes I believe it was a windows recovery partition. I updated the BIOS then reset my settings, but I can check again. I will also look at updating my SSD firmware as I have not done that yet.

---

### Post by Dennis N on 2019-10-04
> **thegoodstuff24 said:**
> Grub is definitely installed and working fine, as far as I know. I can still boot to windows fine and at least select Ubuntu to boot from.
There indeed is a line for /boot/efi and is displayed as follows:
```
/swapfile                                                         none             swap   sw        0            0
           UUID=C7C9-45DF    /boot/efi            vfat       defaults        0          1 
```
That appears to match line 183...
The UUID is correct here for the ESP. But I think fstab is not getting read at all. I suspect your initramfs (needed to startup) may be looking for that missing partition UUID=042B-FE10 and it's not there so you end up in the emergency mode. If this analysis is correct, initramfs would need to be regenerated. The command (run as root) is:
```
update-initramfs -u
```
BUT, this only works if you run it from root partition of Ubuntu OS filesystem. If you can't boot Ubuntu, you have to chroot into the Ubuntu root partition from live media, execute the command above, followed by update-grub. 
 
Hopefully, that will fix things.

---

### Post by thegoodstuff24 on 2019-10-04
Ok, do you have a recommended procedure for setting up chroot?

---

### Post by oldfred on 2019-10-04
With chroot you have to mount the necessary folders in root from identical live installer.
It varies a bit if UEFI (as you have to also mount the ESP) or LVM with encryption.

       To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install 

      
 UEFI chroot - shows mount of ESP also
[URL="http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380"]http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380
      [/URL]
  chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088) 
    [URL="http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380"]
[/URL]

---

### Post by Dennis N on 2019-10-04
Get device name for Ubuntu root partition from boot info summary --> [B]/dev/nvme0n1p4
[/B]and use this as device in first mount command below (I already put it in). Words in [...] are comments. don't type in.

```
Work Notes:
STEPS TO ENTER AND EXIT CHROOT ENVIRONMENT
sudo mount /dev/nvme0n1p4 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
[enters chroot environment with root prompt]
update-initramfs -u
update-grub
exit
[leaves chroot environment]
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

---

### Post by thegoodstuff24 on 2019-10-07
So I chrooted in and followed your steps but still have the same issue.
I looked at the boot info logs again and I am wondering lines 165-171 are the actual issue.

```
[COLOR=#000000]Failed to mount [/COLOR][COLOR=#BB4444]'/dev/nvme0n1p1'[/COLOR][COLOR=#000000]: Invalid argument[/COLOR]The device [COLOR=#BB4444]'/dev/nvme0n1p1'[/COLOR] doesn[COLOR=#BB4444]'t seem to have a valid NTFS.[/COLOR]
[COLOR=#BB4444]Maybe the wrong device is used? Or the whole disk instead of a[/COLOR]
[COLOR=#BB4444]partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR]
[COLOR=#BB4444]mount /dev/nvme0n1p1 : Error code 12[/COLOR]
[COLOR=#BB4444]mount -r /dev/nvme0n1p1 /mnt/boot-sav/nvme0n1p1[/COLOR] [COLOR=#BB4444]NTFS signature is missing.[/COLOR]
```

From my liveUSB i opened Gparted and it does not recognize ncme0n1p1.
I honestly don't even know what that partition is. Maybe I could try formatting it to ntfs?

---

### Post by oldfred on 2019-10-07
Typical default installs of Windows have the first partition as some sort of recovery.
I believe it usually is NTFS.

It could be hibernated as Windows sets hibernation flag on all NTFS partitions when fast start up is on.
Or if as message says NTFS signature is missing, may be a NTFS partition boot sector is damaged. 
If that is issue then you may be able to restore the signature from a backup.

[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

### Post by thegoodstuff24 on 2019-10-07
If it truly is a Windows recovery partition why would that prevent me from booting into Ubuntu?
And why would Windows be booting properly?

---

### Post by oldfred on 2019-10-07
While maybe not the issue, did you fix it so we know for sure it is not the issue?

Did you update UEFI on new motherboard? As installed it may not have newest UEFI which is required.

---

### Post by thegoodstuff24 on 2019-10-07
Hmmm, so I rebooted a couple of times and it just started working. Maybe what Dennis suggested worked but when I did another grub-update it took it. Rebooted 3 more times and it appears to be working properly. I guess I will keep an eye on it and let you know.

---

