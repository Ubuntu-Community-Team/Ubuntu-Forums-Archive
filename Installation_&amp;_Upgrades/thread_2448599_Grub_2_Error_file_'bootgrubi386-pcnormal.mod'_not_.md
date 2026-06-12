---
title: "Grub 2 Error: file 'boot/grub/i386-pc/normal.mod' not found"
date: 2020-08-10
forum: Installation &amp; Upgrades
---

### Post by 4wimpak on 2020-08-10
Hi,
I'm new here, but I've been using Ubuntu 16.04 on my computer for a while. Since the last updates, I've been having issues accessing to Grub 2. I've tried several ways to recover it, but either comes this:

error: file 'boot/grub/i386-pc/normal.mod' not found.
Entering rescue mode...
grub rescue>

or:

error: symbol 'grub_calloc' not found.
Entering rescue mode...
grub rescue>

Instead of the normal Grub 2 environment.

When I tried to fix it with a boot-repair disk, it showed me that it's about a dpkg error. It recommended me then to type this on a terminal:

sudo chroot "/mnt/boot-sav/sda6" dpkg --configure -a

but i got the following line as an answer:

dpkg: error: unable to access dpkg status area: No such file or directory.

So. I tried to de-install grub 2 and install it back but it doesn't let me to...

Here's my boot-info: [http://paste.ubuntu.com/p/SmtDhMGVcS/](http://paste.ubuntu.com/p/SmtDhMGVcS/)

I'd be really thankful for your help!

---

### Post by oldfred on 2020-08-10
Your error probably is becuase you have a separate partition for /var. Most desktops do not have that, so Boot-Repair does not have mount it. Server users who may have separate system partitions, know how to do a full chroot to mount all required partitions to repair Ubuntu if necessary.

Not sure you can add the mount of /var in Boot-Repairs commands and then have it work or have to do the full chroot.

Not sure if any of these examples include the mount of /var or not, but you will need that also:
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

You installed grub to PBR partition boot sector in sda3 & sda6. You should never install grub to a partition's boot sector. And absolutely never to NTFS, your sda3 as that damages Windows. You may be able to restore the backup PBR or boot sector BS using testdisk.
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

You also have managed to delete the BCD from sda1 which Windows requires to boot. You need Windows repair tools to fix that. But not sure since Windows 7 is EoL - end of life if you can fix it or not.
Best not to use Windows 7 anymore, anyway.

---

