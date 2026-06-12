---
title: "Poorly set up RAID became inconsistent after upgrade"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by StarkRG on 2010-06-15
Several months ago when I set up this computer I tried to set up a hardware raid. After fiddling around with it I realized that it wasn't really a hardware RAID 5 and was in fact one of those fakeRAID things and that all the implementation was done on the software level anyway. So I removed the (what amounted to) extra SATA controller and just used the onboard controller. I then set up LVM on top of the main raid. Everything appeared fine. It was only after a week that I discovered that it was still set up as the fake raid and could not be altered by mdadm. Yet, it still worked, until now.

Here's the setup:

500GB drive
[INDENT]* /boot partition (400MB)
* Windows partition (the rest)[/INDENT]
1TB  |  1TB  |  1TB:
[INDENT]2TB RAID 5, split by LVM into...
[INDENT]* / root partition (maybe 100GB)
* /home partition (maybe another 100GB)
* video storage (whatever's left)[/INDENT][/INDENT]

I ran it for several months with no RAID or LVM issues whatsoever until I upgraded to 10.04. Grub failed.

Eventually I was able to get grub working again (removed the 500GB drive with /boot on it and plugged it into another machine and ran update-grub on it), but it would only come up in rescue mode. After issuing the magic words "linux /vmlinuz-2.6.32-22-generic root=/dev/mapper/zelbinion-root" followed by "initrd /initrd.img-2.6.32-22-generic" and "boot" the thing dropped me at a busybox prompt because it couldn't mount the root device.

After much fiddling I discovered that LVM couldn't find anything since the RAID wasn't being loaded properly. It showed up in /dev/ as /dev/mapper/sil_ajbicedebhfh (which is what it showed up as before the breakdown).

I used my magic powers to boot into Windows and downloaded a fresh install disk which is what I'm using at the moment. I installed LVM to the temporary drive, but still nothing. 

Using dmraid I was able to find out why the RAID wasn't working properly.
```
root@ubuntu:~# dmraid -s
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdc
*** *Inconsistent* Set
name   : sil_ajbicedebhfh
size   : 3907047168
stride : 128
type   : raid5_ls
status : inconsistent
subsets: 0
devs   : 3
spares : 0
root@ubuntu:~# dmraid -an
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdc
ERROR: dos: reading /dev/mapper/sil_ajbicedebhfh[No such file or directory]
root@ubuntu:~# dmraid -ay
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdc
RAID set "sil_ajbicedebhfh" was activated
ERROR: dos: reading /dev/mapper/sil_ajbicedebhfh[No such file or directory]
root@ubuntu:~# dmraid -ay
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdc
RAID set "sil_ajbicedebhfh" already active
ERROR: dos: reading /dev/mapper/sil_ajbicedebhfh[No such file or directory]
root@ubuntu:~# dmraid -s -dddvvv sil_ajbicedebhfh
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdd: sil metadata discovered
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdc: sil metadata discovered
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdb: sil metadata discovered
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
DEBUG: not isw at 1891654656
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 1890572800
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
NOTICE: added /dev/sdd to RAID set "sil_ajbicedebhfh"
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
NOTICE: added /dev/sdc to RAID set "sil_ajbicedebhfh"
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
NOTICE: added /dev/sdb to RAID set "sil_ajbicedebhfh"
DEBUG: checking sil device "/dev/sdd"
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdd
DEBUG: checking sil device "/dev/sdb"
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdb
DEBUG: checking sil device "/dev/sdc"
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdc
DEBUG: set status of set "sil_ajbicedebhfh" to 4
*** *Inconsistent* Active Set
name   : sil_ajbicedebhfh
size   : 3907047168
stride : 128
type   : raid5_ls
status : inconsistent
subsets: 0
devs   : 3
spares : 0
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "sil_ajbicedebhfh"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdd"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdb"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdc"
root@ubuntu:~# dmraid -r
/dev/sdd: sil, "sil_ajbicedebhfh", raid5_ls, ok, 1953523630 sectors, data@ 0
/dev/sdc: sil, "sil_ajbicedebhfh", raid5_ls, ok, 1953523630 sectors, data@ 0
/dev/sdb: sil, "sil_ajbicedebhfh", raid5_ls, ok, 1953523630 sectors, data@ 0

```

So... as far as I can tell, it sees the RAID headers ok, but it thinks there are zero disks in it, despite finding three...

I also tried running "dmsetup reload sil_ajbicedebhfh zelb.map" where zelb.map looks like "0 3907047168 striped 3 128 /dev/sdb 0 /dev/sdc 0 /dev/sdd 0" but no luck.

And I've pretty much exhausted my knowledge and googling capabilities.

I don't currently have a spare 1TB drive to do a dmraid -R (recovery) on, and I'm not sure that would work anyway. All the data is still there as I don't think I've changed anything. I think I should be able to get it to work if I can get it to realize that the # of devices in RAID set is 3 and not 0.

HALP!

---

### Post by ronparent on 2010-06-15
I think your problem is in the switch from fakeraid to software raid, The fakeraid writes meta data to your raid disk when it is setup. When you switch the raid off in bios that data remains in place. This didn't make much difference before 9.10 because the program dmraid which read that data and acted on it wasn't automatically installed. Now you have two alternatives 1) add the boot parameter 'nodmraid' to your grub menu boot line or 2) use dmraid in terminal to permanently erase the meta data. Either alternative should eliminate a conflict between 'dmraid' and 'dmadm'.

To erase the data you would write 'sudo dmraid -E /dev/sda', etc for whichever drives apply.

---

### Post by StarkRG on 2010-06-15
> **ronparent said:**
> I think your problem is in the switch from fakeraid to software raid, The fakeraid writes meta data to your raid disk when it is setup. When you switch the raid off in bios that data remains in place. This didn't make much difference before 9.10 because the program dmraid which read that data and acted on it wasn't automatically installed. Now you have two alternatives 1) add the boot parameter 'nodmraid' to your grub menu boot line or 2) use dmraid in terminal to permanently erase the meta data. Either alternative should eliminate a conflict between 'dmraid' and 'dmadm'.

To erase the data you would write 'sudo dmraid -E /dev/sda', etc for whichever drives apply.

Well, I didn't actually "switch" as such. I just removed the SATA controller, the meta data it put on the drives remained. mdadm won't touch the drives as it says they aren't an mdadm RAID set. dmraid may not be installed by default but I did have it installed and was working in 9.10. It was working so well I didn't even realize that it wasn't set up properly until I had data on the drives I didn't want to lose.

Running sfdisk shows some odd things in regard to the partition IDs.
```
root@ubuntu:~# sfdisk -uS -l

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1           128    786495     786368  83  Linux
/dev/sda2   *    788480    993279     204800   7  HPFS/NTFS
/dev/sda3        993280 976771071  975777792   7  HPFS/NTFS
/dev/sda4             0         -          0   0  Empty

Disk /dev/sdb: 0 cylinders, 2 heads, 4 sectors/track
read: Invalid argument

sfdisk: read error on /dev/sdb - cannot read sector 0
 /dev/sdb: unrecognized partition table type
No partitions found

Disk /dev/sdc: 121601 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/1/0 (instead of 121601/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdc1             0 2626742976 2626742977  73  Unknown
/dev/sdc2             0         -          0   0  Empty
/dev/sdc3             0         -          0   0  Empty
/dev/sdc4             0         -          0   0  Empty

Disk /dev/sdd: 121601 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1            63 3907040129 3907040067  8e  Linux LVM
/dev/sdd2             0         -          0   0  Empty
/dev/sdd3             0         -          0   0  Empty
/dev/sdd4             0         -          0   0  Empty

```

I just noticed that sdb is now reporting no partitions while just last night it was showing this:
```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023839

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect
```

So, despite not having altered anything the drives are going wonky. Perhaps it's because I ran this just moments ago:
```
root@ubuntu:~# dmraid -an
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdc
ERROR: dos: reading /dev/mapper/sil_ajbicedebhfh[No such file or directory]

root@ubuntu:~# mdadm --assemble /dev/sdb /dev/sdc /dev/sdd
mdadm: no recogniseable superblock on /dev/sdc
mdadm: /dev/sdc has no superblock - assembly aborted

```

I imagine putting nodmraid in the boot line will cause the raid to not be recognized at all since mdadm won't recognize it. I will try it though, and report back.

I hope, at the very least, when I can afford a fourth 1TB drive I can stick it in and do a recovery. Though it would be nice to be able to get it working now so I'd have a usable computer. (I don't consider running off a live CD to be usable, though it's more so than Windows)

---

### Post by ronparent on 2010-06-16
I hope you have nothing of value on those drives. If I read you correctly, you had abandoned the raid set you had originally set up in bios to set up a software raid5 set in lvm? After upgrading and removing your original boot drive nothing worked? You then tried to look at that setup with dmraid and, of course, found no raid definitioms in /dev/mapper/. They would not exist because the raid definitions created by mdadm would not exist at that location. As you have found in your second posting the partition tables are rational only with mdadm set up. 

To begin to sort this out, if you do not intend to use fakeraid, you have use dmraid to erase the meta data written to those disks and then uninstall dmraid. 

Putting nodmraid in the boot line should have no effect because you do not have a fakeraid now defined in /dev/mapper/. If your software raid still exist the symbolic links to the software raid array would still exist elsewhere.

---

### Post by StarkRG on 2010-06-16
> **ronparent said:**
> I hope you have nothing of value on those drives.
Depends on your definition of value. To me it's worth quite a bit, up to, and including using a hex editor to alter the metadata if I know where to look and what to change.
> **ronparent said:**
> If I read you correctly, you had abandoned the raid set you had originally set up in bios to set up a software raid5 set in lvm?
Nope. I used the "raid" SATA controller to put its metadata on the drives. Then realized that I didn't actually need the SATA controller and removed it. However dmraid still saw the metadata and set it up automatically. (keep in mind that this was my first attempt at RAID so I was very green and did some incredibly stupid things) The drives continued to be seen as if they were attached to this other controller despite the fact they were plugged into the motherboard's controller.

I never got a chance to set up anything with mdadm since it was already set up automatically by dmraid. So, to reiterate, I did NOT use mdadm and, as such, it's pointless to discuss mdadm.

> **ronparent said:**
> After upgrading and removing your original boot drive nothing worked?
the /boot partition is on a separate drive, I haven't removed it (I removed it temporarily to plug it into my laptop to get GRUB installed properly, but replaced it as it is the main boot drive, after which I was able to get to the GRUB rescue prompt, which I wasn't able to get to before)

The root partition is on LVM which is on top of the RAID.
> **ronparent said:**
> You then tried to look at that setup with dmraid and, of course, found no raid definitioms in /dev/mapper/. They would not exist because the raid definitions created by mdadm would not exist at that location. As you have found in your second posting the partition tables are rational only with mdadm set up.
No, mdadm has absolutely nothing to do with it as I never used it to set up the raid as it was already set up. /dev/mapper does indeed show the RAID device but it's inaccessible (according to dmraid it's "inconsistent" not "broken")

> **ronparent said:**
> To begin to sort this out, if you do not intend to use fakeraid, you have use dmraid to erase the meta data written to those disks and then uninstall dmraid. 

Putting nodmraid in the boot line should have no effect because you do not have a fakeraid now defined in /dev/mapper/. If your software raid still exist the symbolic links to the software raid array would still exist elsewhere.
Putting nodmraid will not work since mdadm won't touch the drives since it's never had anything to do with it.

I discovered yesterday that /dev/sdb has suddenly decided that it no longer has any partitions and is essentially blank. The other two (sdc and sdd) still report that they are part of the array, however dmraid seems to think the array has a total of zero(0) disks yet it is finding two(2) (though before it found 3).

Since sdb is reporting no partitions I decided to try to do a recovery from the other two discs using sdb as the spare but it gave me this:
```
root@ubuntu:~# dmraid -R sil_ajbicedebhfh /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [2/0] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [2/0] on /dev/sdc
Segmentation fault (core dumped)

```

and, with more verbosity and debug messages:
```
root@ubuntu:~# dmraid -vvvddd -R sil_ajbicedebhfh /dev/sdb
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdd: sil metadata discovered
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdc: sil metadata discovered
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
DEBUG: not isw at 1891654656
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 1890572800
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching /dev/sdb
DEBUG: _find_set: not found /dev/sdb
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
NOTICE: added /dev/sdd to RAID set "sil_ajbicedebhfh"
NOTICE: dropping unwanted RAID set "sil_ajbicedebhfh"
DEBUG: checking sil device "/dev/sdd"
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [1/0] on /dev/sdd
DEBUG: set status of set "sil_ajbicedebhfh" to 4
DEBUG: freeing devices of RAID set "sil_ajbicedebhfh"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdd"
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
NOTICE: added /dev/sdc to RAID set "sil_ajbicedebhfh"
NOTICE: dropping unwanted RAID set "sil_ajbicedebhfh"
DEBUG: checking sil device "/dev/sdc"
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [1/0] on /dev/sdc
DEBUG: set status of set "sil_ajbicedebhfh" to 4
DEBUG: freeing devices of RAID set "sil_ajbicedebhfh"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdc"
ERROR: either the required RAID set not found or more options required
no raid sets and with names: "/dev/sdb"
WARN: unlocking /var/lock/dmraid/.lock

```

To me this indicates that at least part of the metadata is damaged (it's showing that the discs are part of an array, but is ignoring it because it thinks the array somehow consists of zero disks (ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [2/0] on /dev/sdc)

However dmraid -s does show "devs   : 2", not sure what that means.
```
root@ubuntu:~# dmraid -s
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [2/0] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [2/0] on /dev/sdc
*** *Inconsistent* Active Set
name   : sil_ajbicedebhfh
size   : 1953523584
stride : 128
type   : raid5_ls
status : inconsistent
subsets: 0
devs   : 2
spares : 0

```

To me the "wrong # of devices" bit is saying 2 out of 0 where normally those errors show something like [2/3] (which I take to means "two out of three drives found").

Stupidly I left the "raid" controller in my other computer which I left in storage before I moved so I don't have access to it. However, since it's fake raid I shouldn't really need it (though would probably have made recovery easier).

The problem now seems to be twofold. sdb has lost its partition table, not a big deal since I should be able to use it as the spare and recover the array. The main problem is that the array is listed as inconsistent which I take to mean that the metadata from the two remaining drives do not agree (an array that is missing a drive is labeled as "broken" and can then be recovered), if I can get the array to be listed as "broken" I should be able to recover it.

---

### Post by ronparent on 2010-06-17
OK, I think you have finally gotten through to me. You had turned off the raid bios and eventually tossed aside the original raid chipset and plugged the raid set into another MB with the raid bios turned off. Everything worked fine, because dmraid was operating it as a pure software raid, Everything was fine until you upgradded to 10.04!

I have no idea what to advise you because dmraid wasn't designed to function totally independently of a bios raid chipset. I'm totally flabbergasted that it worked at all. I wouldn't suggest turning on the raid bios, except with the original chipset since I've done that and it effectively erased the partition tables. The data on the disks is still there except where it may have been overwritten. Please don't take it as an affront, but, I am really sorry for your loss.

---

### Post by StarkRG on 2010-06-25
Well, I was able to get a replacement "RAID" card AND got another hard drive to install Windows XP on so I could run the card's software. Thing promptly notified me that there was a new "task." I checked it out and it said it was "restoring redundancy." After a few false starts (turns out the process restarts if you reboot, I thought that wasn't supposed to happen) I left the computer going for about 30 hours. Eventually it completed and I quickly booted back into linux to see if the problem was resolved.

It isn't. (that part earlier where /dev/sdb wasn't reporting things properly had already resolved itself when I rebooted a while back) The whole "wrong # of devices" thing remains, still saying [3/0]

Anyone got any more ideas?

---

### Post by StarkRG on 2010-06-25
Aha, so new discovery: "dmraid -l" shows that it doesn't support sil raid 5 arrays: "sil     : Silicon Image(tm) Medley(tm) (0,1,10)"

Remember though, it WAS working under Karmic. Might try downloading Karmic disc and see if that makes any difference.

---

### Post by StarkRG on 2010-06-25
Hurray, so new development: upon booting into Karmic dmraid no longer reports "wrong # of devices"
```
root@ubuntu:~# dmraid -s
*** Active Set
name   : sil_ajbicedebhfh
size   : 3907047168
stride : 128
type   : raid5_ls
status : ok
subsets: 0
devs   : 3
spares : 0
```

However after I installed LVM2 I discovered that it wasn't detecting any physical volumes:

```
root@ubuntu:~# pvscan
  No matching physical volumes found
```

The corresponding part of "pvscan -vvvddd"

```
        Opened /dev/mapper/sil_ajbicedebhfh RO
      /dev/mapper/sil_ajbicedebhfh: size is 3907047168 sectors
        Closed /dev/mapper/sil_ajbicedebhfh
      /dev/mapper/sil_ajbicedebhfh: size is 3907047168 sectors
        Opened /dev/mapper/sil_ajbicedebhfh RO O_DIRECT
        /dev/mapper/sil_ajbicedebhfh: block size is 4096 bytes
        Closed /dev/mapper/sil_ajbicedebhfh
        Using /dev/mapper/sil_ajbicedebhfh
        Opened /dev/mapper/sil_ajbicedebhfh RO O_DIRECT
        /dev/mapper/sil_ajbicedebhfh: block size is 4096 bytes
      /dev/mapper/sil_ajbicedebhfh: No label detected
        Closed /dev/mapper/sil_ajbicedebhfh
```

Seems the metadata is missing... according to the [official howto]("http://tldp.org/HOWTO/LVM-HOWTO/recovermetadata.html") I just need to use the metadata backup from /etc/lvm/archive

Unfortunately I was stupid and put my root partition inside the LVM so that backup is inaccessible.

I wonder if I could just run pvcreate with no options as that's what I would have done when I first set it up, or is that just going to totally screw things up even more?

---

### Post by psusi on 2010-06-25
dmraid is saying there are errors with the metadata because there probably are, but who cares since you aren't using the fake raid anyhow?  As ron said, you need to erase the fakeraid metadata if you aren't using it so dmraid doesn't interfere with mdadm.

---

### Post by StarkRG on 2010-06-25
I just remembered I'm fairly certain I had partitioned the raid's block device...


googled "lost partition table"


rediscovered *testdisk*


ran *testdisk*
recovered partition table

reran pvscan

behold:
```
root@ubuntu:~# pvscan
  PV /dev/mapper/sil_ajbicedebhfh1   VG zelbinion   lvm2 [1.82 TB / 0    free]
  Total: 1 [1.82 TB] / in use: 1 [1.82 TB] / in no VG: 0 [0   ]
root@ubuntu:~# ls /dev/mapper/
control  sil_ajbicedebhfh  sil_ajbicedebhfh1  zelbinion-gilina  zelbinion-home  zelbinion-root  zelbinion-swap

```
w00t!

*does happy dance*

*kisses everybody in thread*


er... sorry, got a little carried away there... Thanks everyone, I think I'm on the home stretch now!

---

### Post by StarkRG on 2010-06-25
Just to test it out I booted into Lucid and the error returned, booted into Karmic, error disappeared again.

I'm not sure if it was a bug that it worked at all which was patched or if it's a new bug, but there's been some change in dmraid that's not liking my crappy setup.

---

### Post by StarkRG on 2011-01-31
To quickly summarize the issue:
I set up my computer using an SIL SATA raid card. I told it to set up the raid metadata on the drives. Then, as I read up on linux RAID I decided that I wasn't going to use the fake raid card at all and so I removed it thinking that formatting the drives individually would get rid of the metadata. After installing the system I went in to begin setting up the RAID. At the point of creating the RAID I got an error. Turns out the system had recognized the SIL metadata and set up the raid all on its own. (keep in mind there's no RAID card at this point)
I used it for several months, loading 2TB worth of data on these drives. Then I was informed that there was an upgrade, Lucid was ready to install. I went ahead and upgraded, but when it was done I no longer had access to my RAID drive. It was being reported as "inconsistent". Freaked out I did much research and found very little to explain what was going on (some pages said to remove the faulty drive and replace it with a new one, well fine, but which one is faulty? Seems like it's saying there are three drives when there should only be zero which is how I interpret [3/0]) I posted this thread. I reinstalled the RAID controller again, thinking that perhaps the lack of one was the problem. It wasn't. Eventually I found a slightly older version of my original Karmic install (I'd changed boot drives at one point, apparently) and voila, RAID access. Since nobody seemed to have any ideas about what kind of troubleshooting I should be doing, or even where I might look for the problem I decided to stick to Karmic for a while.


So here we are several months later. I've been using Karmic this whole time and it's getting to be quite restrictive (there are apps I want to install but can't for various reasons).

I decided to download and freshly install Maverick on a second drive, guessing that perhaps whatever caused this to occur might have been accidentally fixed. No luck.

Karmic installs seem to see my raid setup, anything more recent than that seem to think it's inconsistent.

Here's what it says on my new Maverick install.
```
# dmraid -s -dddvvv

ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sdc
ERROR: sil: wrong # of devices in RAID set "sil_ajbicedebhfh" [3/0] on /dev/sda
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
DEBUG: not isw at -2049614848
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -2050696704
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdc: sil metadata discovered
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdb: sil metadata discovered
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sda: sil metadata discovered
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
NOTICE: added /dev/sdc to RAID set "sil_ajbicedebhfh"
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
NOTICE: added /dev/sdb to RAID set "sil_ajbicedebhfh"
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
NOTICE: added /dev/sda to RAID set "sil_ajbicedebhfh"
DEBUG: checking sil device "/dev/sdb"
DEBUG: checking sil device "/dev/sdc"
DEBUG: checking sil device "/dev/sda"
DEBUG: set status of set "sil_ajbicedebhfh" to 4
*** *Inconsistent* Active Set
name   : sil_ajbicedebhfh
size   : 3907047168
stride : 128
type   : raid5_ls
status : inconsistent
subsets: 0
devs   : 3
spares : 0
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "sil_ajbicedebhfh"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdb"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdc"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sda"


**********************************************

# dmraid -r -dddvvv

WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
DEBUG: not isw at -2049614848
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -2050696704
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdc: sil metadata discovered
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdb: sil metadata discovered
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
DEBUG: not isw at -522494976
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at -523576832
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sda: sil metadata discovered
NOTICE: /dev/sda: via     discovering
INFO: RAID devices discovered:

/dev/sdc: sil, "sil_ajbicedebhfh", raid5_ls, ok, 1953523630 sectors, data@ 0
/dev/sdb: sil, "sil_ajbicedebhfh", raid5_ls, ok, 1953523630 sectors, data@ 0
/dev/sda: sil, "sil_ajbicedebhfh", raid5_ls, ok, 1953523630 sectors, data@ 0
WARN: unlocking /var/lock/dmraid/.lock

```

Even though it's listed as active I don't actually have access to it. The device shows up under /dev/mapper but the system can't read it. I've pulled it down and tried to bring it back up but it says it can't because it's inconsistent (but then goes ahead and activates it anyway, though still no access)

And the same tests done on my Karmic install:
```
# dmraid -s -dddvvv

WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sde: asr     discovering
NOTICE: /dev/sde: ddf1    discovering
NOTICE: /dev/sde: hpt37x  discovering
NOTICE: /dev/sde: hpt45x  discovering
NOTICE: /dev/sde: isw     discovering
DEBUG: not isw at 320072932352
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 320071850496
NOTICE: /dev/sde: jmicron discovering
NOTICE: /dev/sde: lsi     discovering
NOTICE: /dev/sde: nvidia  discovering
NOTICE: /dev/sde: pdc     discovering
NOTICE: /dev/sde: sil     discovering
NOTICE: /dev/sde: via     discovering
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
DEBUG: not isw at 1000204884992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 1000203803136
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdd: sil metadata discovered
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
DEBUG: not isw at 1000204884992
DEBUG: isw trying hard coded -2115 offset.      
DEBUG: not isw at 1000203803136
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering    
NOTICE: /dev/sdc: pdc     discovering    
NOTICE: /dev/sdc: sil     discovering   
NOTICE: sil: areas 1,2,3,4[4] are valid      
NOTICE: /dev/sdc: sil metadata discovered   
NOTICE: /dev/sdc: via     discovering      
NOTICE: /dev/sdb: asr     discovering         
NOTICE: /dev/sdb: ddf1    discovering             
NOTICE: /dev/sdb: hpt37x  discovering         
NOTICE: /dev/sdb: hpt45x  discovering    
NOTICE: /dev/sdb: isw     discovering
DEBUG: not isw at 1000204884992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 1000203803136
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdb: sil metadata discovered
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: not found sil_ajbicedebhfh
NOTICE: added /dev/sdd to RAID set "sil_ajbicedebhfh"
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
NOTICE: added /dev/sdc to RAID set "sil_ajbicedebhfh"
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
DEBUG: _find_set: searching sil_ajbicedebhfh
DEBUG: _find_set: found sil_ajbicedebhfh
NOTICE: added /dev/sdb to RAID set "sil_ajbicedebhfh"
DEBUG: checking sil device "/dev/sdc"
DEBUG: checking sil device "/dev/sdd"
DEBUG: checking sil device "/dev/sdb"
DEBUG: set status of set "sil_ajbicedebhfh" to 16
*** Active Set
name   : sil_ajbicedebhfh
size   : 3907047168
stride : 128
type   : raid5_ls
status : ok
subsets: 0
devs   : 3
spares : 0
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "sil_ajbicedebhfh"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdc"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdd"
DEBUG: freeing device "sil_ajbicedebhfh", path "/dev/sdb"


**********************************************

# dmraid -r -dddvvv

WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sde: asr     discovering
NOTICE: /dev/sde: ddf1    discovering
NOTICE: /dev/sde: hpt37x  discovering
NOTICE: /dev/sde: hpt45x  discovering
NOTICE: /dev/sde: isw     discovering
DEBUG: not isw at 320072932352
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 320071850496
NOTICE: /dev/sde: jmicron discovering
NOTICE: /dev/sde: lsi     discovering
NOTICE: /dev/sde: nvidia  discovering
NOTICE: /dev/sde: pdc     discovering
NOTICE: /dev/sde: sil     discovering
NOTICE: /dev/sde: via     discovering
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
DEBUG: not isw at 1000204884992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 1000203803136
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdd: sil metadata discovered
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
DEBUG: not isw at 1000204884992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 1000203803136
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdc: sil metadata discovered
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
DEBUG: not isw at 1000204884992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 1000203803136
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdb: sil metadata discovered
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
INFO: RAID devices discovered:

/dev/sdd: sil, "sil_ajbicedebhfh", raid5_ls, ok, 1953523630 sectors, data@ 0
/dev/sdc: sil, "sil_ajbicedebhfh", raid5_ls, ok, 1953523630 sectors, data@ 0
/dev/sdb: sil, "sil_ajbicedebhfh", raid5_ls, ok, 1953523630 sectors, data@ 0
WARN: unlocking /var/lock/dmraid/.lock
```

As far as I can tell the only major difference are the numbers following "DEBUG: not isw at"

This is the EXACT SAME RAID SET on each system (I swaped out the boot drive again). I'm at a complete loss as to why the new install refuses to read the set. I believe isw is a brand of RAID controllers, but since I've got an sil it shouldn't matter. Though it does bring into question what else could have possibly changed in the dmraid code (or the kernel code, perhaps) that could cause these symptoms.

I'd be happy to file a bug somewhere, but I'm not entirely sure that it's not something I've done wrong. (I'm also not sure what else to include in such a bug report besides the output of these two commands. (really just one command run with separate switches) Any advice would be most helpful.

---

### Post by psusi on 2011-01-31
If you are not using the fake raid then you need to erase the fake raid metadata either using the bios utility, or sudo dmraid -E /dev/sda.  If you are using one flavor of fake raid, but there is also another on the disk, you can specify which format to erase with the -f switch.

---

### Post by ronparent on 2011-01-31
psusi is absolutely right. 

The meta data once written to a disk is persistent. Even if placed on another port it will retain its original identifying data (but not the partition table). To rid yourself of it, it has to be erased.

I, for instance, personally use raid disks id'd as nvidia although now connected to a pdc chip set with a newly created partition table. It is not material to me. But if I wanted to be rid of the raid, I would have to erase the meta data!

---

### Post by StarkRG on 2011-01-31
So, am I using FakeRAID or not? It sounds like I am since it calls itself "sil_ajbicedebhfh" (sounds like it's sil metadata). Though you guys make it sound like I'm not. As far as I understand it FakeRAID is simply software RAID with proprietary metadata.

If I delete the metadata will dmraid still be able to access it from the Karmic install? Is there any guarantee that doing so won't render all my data inaccessible? Can I back up the metadata so that if it does make it inaccessible I can always restore the old metadata and continue as I have been?

I still don't understand why there's a difference between karmic and after-karmic. Why should karmic have no trouble reading it at all while after-karmic has so much?

Obviously I simply don't know enough about what I'm doing to do it properly and, unfortunately, there doesn't seem to be anyone, prior to me, that has had this particular issue (with the [3/0] weirdness). So there's no HOWTOs or mentions of what the difference between FakeRAID and SoftRAID are. I notice anomalies but I have no way of figuring out what they mean.

Oh, and I currently don't have mdadm installed, not that I think it would be any use whatsoever since in the past it's refused to touch my RAID.

Just to prove it, I installed it and tried it out:
```
# mdadm /dev/mapper/sil_ajbicedebhfh
/dev/mapper/sil_ajbicedebhfh: is not an md array
# mdadm -E /dev/mapper/sil_ajbicedebhfh
mdadm: No md superblock detected on /dev/mapper/sil_ajbicedebhfh.
```

---

### Post by ronparent on 2011-01-31
You have a fakeraid based on your MB chipset. Dmraid is the software used to discover it and initially set it up. Mdadm is the software used to setup and access a software raid and in no way applies in your case. You do have and active and valid raid5 set at least in Karmick. I am puzzled also - there should be no difference in how dmraid behaves with Karmic and with Maverick. In any case since you do use a fakeraid DO NOT erase the meta data. All we have to do now is try to find out what is happening to your raid5 set in Maverick.

If there is a verifiable difference in behavior then you should document it and submit a bug report. 

Prior to that we need determine that dmraid is installed on your maverick and working right. Also, in maverick, what is the output of 'sudo blkid'.
Are you aware of 'man dmraid'? Are the /dev/dm-# devices set up along with the /dev/mapper/* devices. What is the output of 'dmraid -l'? What I find confusing is that the sil meta data doesn't apparently support a level 5 raid. 

I will research the situation some a try to get back to you. I will be handicapped because I no longer have Karmic installed and have not used a raid5.

---

### Post by psusi on 2011-01-31
I thought you were saying that you did away with the fake raid and set up an mdadm software raid.  You appear to have a sil fakeraid raid-5, which is not supported.

Unless you need to dual boot with windows, you should get rid of all of the fakeraid stuff and just use mdadm.

---

