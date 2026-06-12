---
title: "Going from 8.10 to 9.10, also using raid5+lvm"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by Th3Professor on 2009-12-14
I'm running 8.10 right now. I have a RAID5 & LVM set-up also.

Would it be better to upgrade from 8.10 to 9.04 and then from 9.04 to 9.10?

Or would it be better to just do a fresh install of 9.04?

What should be done to prepare the RAID5+LVM set-up for the change?

Thanks!

---

### Post by Th3Professor on 2009-12-15
The raid5+lvm part can be disregarded in here if preferred, I can ask about that in a separate subject elsewhere if nobody knows here.

The main question can just be:

Would it be better to upgrade from 8.10 to 9.04 and then from 9.04 to 9.10; or would it be better to just do a fresh install of 9.04?


Thanks!

---

### Post by Th3Professor on 2009-12-16
> **Th3Professor said:**
> The raid5+lvm part can be disregarded in here if preferred, I can ask about that in a separate subject elsewhere if nobody knows here.

The main question can just be:

Would it be better to upgrade from 8.10 to 9.04 and then from 9.04 to 9.10; or would it be better to just do a fresh install of 9.04?


Thanks!

<bump>

---

### Post by phillw on 2009-12-16
Hi.

There are currently some 'issues' with 9.10 (Grub2) and RAID.  There are several threads on the subject on this forum. I'd recommend reading them before you commit, if you require a RAID environment.

/edit - as you'd be leaping accross more than one version to land at 9.10 - IMHO - I'd go for a reinstall - That will give you Grub2 and ext4 'out of the box'

Regards,

Phill.

---

### Post by Th3Professor on 2009-12-18
I searched for tags w/ raid and 9.10 but found nothing. Have there been any recent discussions on raid issues w/ 9.10?

---

### Post by Th3Professor on 2009-12-19
> **Th3Professor said:**
> I searched for tags w/ raid and 9.10 but found nothing. Have there been any recent discussions on raid issues w/ 9.10?
\bump/

---

### Post by Th3Professor on 2009-12-20
> **Th3Professor said:**
> \bump/

bum p

---

### Post by darkod on 2009-12-20
I don't know about upgrade but if you decided to go for clean install of 9.10 and depending whether you use fakeraid (mobo onboard) or softraid, you might find something of interest here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
[http://ubuntuforums.org/showthread.php?t=1338445](http://ubuntuforums.org/showthread.php?t=1338445)

---

### Post by Th3Professor on 2009-12-20
I think it has been the better part of a year since I set up my raid5 and lvm.

I'm going to "think out loud" here, any ideas or input from anybody will be great.

I'm pretty sure I need to perform some steps to protect things before reinstalling the OS.

My current set-up... there are a few partitions I'm not using because I haven't set-up additional systems on them yet (other linux or unix systems).

Here's fdisk -l...
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095d78

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  83  Linux
/dev/sda2   *         123       24437   195310237+   7  HPFS/NTFS
/dev/sda3           24438       26261    14651280   be  Solaris boot
/dev/sda4           26262       60801   277442550    5  Extended
/dev/sda5           26262       28693    19535008+  83  Linux
/dev/sda6           28694       57263   229488493+  83  Linux
/dev/sda7           57264       57506     1951866   82  Linux swap / Solaris
/dev/sda8           57507       57749     1951866   82  Linux swap / Solaris
/dev/sda9           57750       57992     1951866   bf  Solaris
/dev/sda10          57993       60801    22563261   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c177d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000caa62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3415

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001    c  W95 FAT32 (LBA)

```It looks like I might have my operating systems installed on a separate hard drive and my extra hard drives might be used only for storing files. I'm hoping that'll make a fresh install easier.

I believe I had intended on installing Gentoo and Solaris, I forget. Never got around to it. :(

I may go ahead and redo my partitions on what appears to be my "operating systems hard drive", I've got some wasted space on there. ...may still leave just 1 small spare partition for testing various *nix systems, no need for any more than that.

Here's a glance at mount...
```
/dev/sda5 on / type ext3
/dev/sda1 on /boot type ext3
/dev/sda6 on /studio/workspace type ext3
/dev/sda2 on /windows type fuseblk
/dev/mapper/vg0-vault on /studio/vault type xfs
/dev/mapper/vg0-zone on /zone type ext3
/dev/mapper/vg0-nomad on /nomad type ext3
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdi1 on /media/My Book type vfat 

```...and df -h...
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              19G   16G  2.2G  88% /
/dev/sda1             942M   72M  823M   9% /boot
/dev/sda6             216G  200G  4.9G  98% /studio/workspace
/dev/sda2             187G  107G   80G  58% /windows
/dev/mapper/vg0-vault
                      755G  247G  509G  33% /studio/vault
/dev/mapper/vg0-zone   87G  184M   83G   1% /zone
/dev/mapper/vg0-nomad
                       87G  342M   82G   1% /nomad
/dev/sdi1             932G  766G  167G  83% /media/My Book

```I think the partitions are set up like this:
sda1 - boot
sda2 - windows
sda5 - the main OS (Ubuntu Studio)
sda6 - "workspace" is for editing files (music recordings)
sdb/sdc/sdd - raid and lvm combination set-up
"vault" - primary mass storage (raid/lvm)
"zone" - I'm not even using this. I wanted to put Solaris on it but didn't know if it's possible.
"nomad" - I'm *also* not using this. I wanted to put Gentoo (or any other *nix) on this but I didn't get a successful install.
sdi - external drive (irrelevant in this situation)

So, I'm thinking I don't have to worry about the windows partition, and that perhaps the boot partition will be automatically updated with a fresh Ubuntu install.

Before I install Ubuntu (Studio) 9.10 I'm going to move files over to the RAID/LVM disks.

After that, is there anything I need to do with the RAID and/or LVM on those 3 hard drives before I put a fresh install of Ubustu on the separate (non-raid/non-lvm) hard drive?

I can't remember if I used mdadm for the raid or if I'd have to "mdadm --stop" or any LVM -equivalent to "stop" prior to installing the new Ubuntu OS on the separate hard drive. Anybody know?[FONT=monospace]
[/FONT]

---

### Post by gilson585 on 2009-12-20
If you need a more thorough set of instructions for fakeraid and 9.10 check out my post [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

### Post by Th3Professor on 2009-12-21
Fake raid is something I may consider in the future but right now my raid+lvm hard drives are currently set up and storing data via soft raid. I'd like to be able to use raid with windows & linux but I only use windows for a couple rare applications (aka certain games). :) Anyway, thank you for that link! That'll come in handy in the future if I make a switch.

I had forgotten what I'm using, it turns out it's mdadm (along with lvm, I think lvm2).

mdadm --examine brings up some info...
raid5, 3 devices, state "clean", layout "left-symmetric", 128k chunk size.

Will I need to do anything with RAID and/or LVM prior to putting a fresh OS install on the computer?

The OS is on a hard drive *separate* from the raid/lvm set-up. Though, I still don't want to take any chances with not being able to access the raid/lvm hard drives after I get the new system installed. :-/

Are there any steps I need to take with lvm before and after a fresh OS install?

Likewise, are there any steps I need to take with raid (mdadm) before and after the fresh OS install?

---

### Post by gilson585 on 2009-12-21
Quite the configuration you've got there. Also try and see if the livecd can pick the raid up automatically. I'm not that familiar with mdadm but will try and help. If you can get it to mount on the livecd correctly then you shall not have any issues. As far as my instructions go in that link, you only need them if you are booting off the raid array which you mention you are not. I don't believe you can do much damage in the livecd environment unless you accidentally erase the mbr by rebuilding the array but even that can be fixed w/o data loss. So try it out it might just go ahead and use dmraid instead of mdadm and detect it on its own. Note dmraid doesnt cooperate with fdisk so check disk structure with gparted. But as I said I have never used mdadm so read some of this and it also has some useful external links at the bottom good luck. [http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)

---

### Post by Th3Professor on 2009-12-23
no luck with the ubuntu 9.10 live cd... i burned a disc, loaded the system to test it out... and it does *not* recognize the raid/lvm set-up. it just sees a bunch of separate hard drives. :( i'm pretty bummed out about that right now. i was hoping i'd be able to go ahead and get a fresh 9.10 ubustu install going today/tonight but i have absolutely *no idea* what i need to do with either mdadm and/or lvm *before* the fresh OS install and *after* the fresh install. :(

---

### Post by gilson585 on 2009-12-23
I'll look into it. I'm sure there is a way that you can get your current mdadm configuration and just implement it into the new install. If we can figure it out in the live environment I'd feel much safer giving you the go ahead with the install. I'll get back to you.

---

### Post by Th3Professor on 2009-12-23
I asked about the raid/lvm in the 'general' forum and someone replied with a helpful response, basically the following:

1. boot live cd
2. install mdadm & lvm (lvm2)
3. enter these commands:
```
sudo mdadm --assemble
sudo vgchange -a y
```...and a warning to back-up data, etc. - and I've copied important files over to a non-raid/lvm disk that is on a separate partition from the OS partition. (for now) for some reason every time i tried burning a data cd/dvd it screwed up :( and ruined a few very good quality dvds in the process. It burned the Ubuntu CD & Ubuntu Studio DVD fine. :confused:

Anyway, do you think those commands (the mdadm assemble and vgchange options) will do the trick? I noticed in the 'man' files that there are additional options including-
```

mdadm --assemble md-device options-and-component-devices...
vgchange --available [e|l] y (either "e" or "l" for "exclusive" or "local")
```

:confused:

...or maybe all I need to do once I install mdadm/lvm2 on the live boot is just:
```
sudo mdadm --assemble
sudo vgchange -a y
```:-/

---

### Post by Th3Professor on 2009-12-24
Should I save my old (current) fstab and mdadm.conf files and replace the new OS's version with the old ones after the new install? Or is that just a waste of effort?

(I'm guessing once I do the mdadm --assemble and vgchange -a y commands that it'll automatically adjust fstab and mdadm.conf.)

I wasn't sure where to get the "uuid" for the raid set-up, someone on another board mentioned "mdadm -E /dev/sdb1" (or sdc1, sdd1, etc.) to "examine" and that pulled it right up.

Does this look right:
```
$ sudo mdadm --assemble /dev/md0 --uuid=10056982:7e87ea13:b4ca6f73:30183c6d /dev/sdb /dev/sdc /dev/sdd
```
and still just a simple "-a y" (?) on the lvm:
```
$ sudo vgchange -a y
```

Does anyone know if entering the uuid in the mdadm --assemble command is really necessary?

On another note, I have an extra partition (for file storage) that is *not* part of the raid/lvm disks that initially showed up in an ubuntu live cd file browser but it disappeared when I clicked on it. In my current main install it shows as:
# /dev/sda6
/studio/workspace ext3

---

### Post by Th3Professor on 2009-12-26
Ubuntu Studio 9.10 installed fine, and even the raid/lvm set-up is working fine. :D I didn't even have to install mdadm/lvm2 or use any commands w/ the two applications.

---

