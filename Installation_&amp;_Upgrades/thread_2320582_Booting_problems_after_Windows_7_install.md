---
title: "Booting problems after Windows 7 install"
date: 2016-04-15
forum: Installation &amp; Upgrades
---

### Post by tracy6 on 2016-04-15
For years now I have been dual booting Ubuntu and Windows XP using the grub menu.  I am running Ubuntu 15.10 x86 version.

Because XP has become obsolete, I decided to upgrade to Windows 7.  I did a fresh install of Win7 (x86) using the original partition used for XP.  As expected, when the installation routine was over, I booted directly into windows without a grub menu showing.  Win7 seemed to run normally.

I rebooted and ran the live 15.10 CD and installed and ran boot-repair.  The result of this action restored the grub menu with the Ubuntu 15.10 entry at the top and the Windows 7 entry at the bottom, just as it used to be when XP was in that slot of the menu.

When Ubuntu is selected, the boot sequence is normal and Ubuntu is fine.  However, when Windows 7 (loader) is selected, the computer beeps once and it's done. Just a blank screen.  I have to reset to reboot.

I have the following setup:

sda is a 300gb drive that is used for ubuntu only.  It's a PATA drive that lives in an InClose caddy.
sdb is a 1tb drive used for the windows partition (Drive C) and a Drive D and a Drive E for storage.  This is mounted inside the case.
sdc is a 2tb drive used for Drives F, G, and H to store music, video and misc.  This drive is also mounted in the case.

Here is the output of fdisk -l:

```
[I]Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 279.5 GiB, 300090728448 bytes, 586114704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00005afd

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048  39063551  39061504  18.6G 83 Linux
/dev/sda2       39065598 586113023 547047426 260.9G  5 Extended
/dev/sda5       39065600  46876671   7811072   3.7G 82 Linux swap / Solaris
/dev/sda6       46878720 586113023 539234304 257.1G 83 Linux






Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x80a96026

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1  *            63  266245244  266245182   127G  7 HPFS/NTFS/exFAT
/dev/sdb2        266245245 1953520064 1687274820 804.6G  5 Extended
/dev/sdb5        266245308 1187846099  921600792 439.5G  7 HPFS/NTFS/exFAT
/dev/sdb6       1187846163 1953520064  765673902 365.1G  7 HPFS/NTFS/exFAT


Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xed2264e9

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdc2  *    1023999165 2457591569 1433592405 683.6G  7 HPFS/NTFS/exFAT
/dev/sdc3       2457591570 3907024064 1449432495 691.1G  7 HPFS/NTFS/exFAT
/dev/sdc4            16065 1023999165 1023983101 488.3G  5 Extended
/dev/sdc5            16128 1023999164 1023983037 488.3G  7 HPFS/NTFS/exFAT

Partition table entries are not in disk order.[/I]
```

I have uploaded the output of the boot-repair info to the following pastebin:

[http://paste.ubuntu.com/15851578](http://paste.ubuntu.com/15851578)

I don't remember having this much trouble when I originally set this up with XP, nor do I remember having all of those ramdisks.  Is there something unique to Windows 7 that is causing all this grief?  Or am I just overlooking something simple?

Thanks much

---

### Post by oldfred on 2016-04-15
Please use code tags on long text or code post. And all that info is really in link to Boot-Repair's summary report.

So is Ubuntu drive really an external drive?
Do not run Boot-Repair's auto fix with multiple drives. It installs grub to the MBR of every drive. And you normally want each drive to have the boot loader for the install on that drive. You can use Boot-Repair's advanced mode, select Windows and restore a Windows type boot loader (syslinux) to Windows drive. Or use your Windows repair or install disk in repair console to restore the Windows boot loader.

It may be a mapping issue. Windows probably expects that BIOS will see it as hd0 or first drive. But drive you boot from is always hd0. But if booting from Ubuntu drive that will be hd0 and Windows hd1. Grub normally has a mapping entry in that case and I do not see it.

I might house clean kernels, be sure to boot from Ubuntu drive and run this:
sudo update-grub

And check if directly booting Windows from BIOS works. Grub only boots working Windows.

If update does not add a mapping entry we can try adding it, by copying Windows boot stanza to 40_custom and editing entry.
Added line would be something like:

 drivemap -s (hd0) ${root}

---

### Post by tracy6 on 2016-04-15
> So is Ubuntu drive really an external drive?

The Ubuntu drive lives in an InClose caddy. When the pc is off, the drive can be removed and replaced from the front of the machine with another caddy & drive if needed, but electrically, it interfaces to the pc with a PATA architecture. It just has another connector and caddy to facilitate quick removal when the pc is off. (I hope that makes sense).

>  Or use your Windows repair or install disk in repair console to restore the Windows boot loader.

I tried to repair the Windows 7 partition with the Windows installation DVD, but it said that it could not detect a problem. 
>  I might house clean kernels, be sure to boot from Ubuntu drive and run this:
sudo update-grub

This didn't help.

>  And check if directly booting Windows from BIOS works. Grub only boots working Windows.

With the BIOS set to boot from the Ubuntu drive, the same error occurs.  (I get the grub menu, but only Ubuntu works).

> If update does not add a mapping entry we can try adding it, by copying Windows boot stanza to 40_custom and editing entry.
Added line would be something like:

drivemap -s (hd0) ${root}

I'm afraid I don't understand this one at all.  But it sounds as though it may have some bearing on it.

Thanks

---

### Post by oldfred on 2016-04-15
When I suggest booting Windows directly, you use BIOS to choose Windows drive or use one time BIOS boot key often f10 or f12, check you manual if not one of those.

But you want a Windows boot loader on the Windows drive and grub on the Ubuntu drive's MBR. Then from BIOS you can directly boot either system.
Grub only boots working Windows, so sometimes you need to directly boot to repair it.
Be sure to set BIOS to default boot Windows drive before repairing. Windows only knows default drive hd0 and you must have boot flag on the primary NTFS partition with bootmgr & BCD files.
Windows normally is first drive and with some systems works better that way. 
With SATA drives better to have Windows plugged into SATA0 and Ubuntu in SATA1 and SATA ports used in order with no open ports in between working drives. That leads to many other issues.

---

### Post by tracy6 on 2016-04-15
Got it working.  Many thanks to you oldfred.  The problem turned out to be in the BIOS all right, but in an unexpected place.
I began by trying to follow your advice regarding the BIOS settings, but this is an old MB/CPU and I didn't see any settings that might correspond to what you were talking about.  But I did see one that looked interesting.  It was a security setting that was labeled ***Boot Sector Virus Protection.  ***It was enabled.  I set that to disabled and that fixed it.

I think during the process of deleting the XP files and installing the Win7 files, the BIOS glitched and reverted to the default settings.  I just ignored it because the system "appeared" to be working properly.  But that setting must have been disabled all the years I've been using grub on this drive and I just didn't remember to check it.

It took a little help to straighten it out.

Thank you.

---

