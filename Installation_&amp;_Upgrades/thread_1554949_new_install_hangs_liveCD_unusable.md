---
title: "new install hangs/ liveCD unusable"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by cholericfun on 2010-08-17
Hi all

i finally decided to updgrade from Hardy Heron to Lucid Lynx.
for this i made a backup of my old install, then i couldnt find my Lucid CD so i used a Karmic one to partition my old ext3 to ext4. There were some errors but after trying a few times it worked. Installed Karmic, rebooted (worked fine), downloaded all updates - (did NOT reboot to let updates take effect) and upgraded to Lucid.

Everything went fine so far. Now when i try to boot into Lucid the system hangs, i've also got a windowsXP partition on there so i tried booting that,
first grub tells me 
Error 29: Disk write error
then trying again windows seems to boot but it takes much longer than it should and seems to hang.

Then i tried Karmic and Lucid LiveCD (which i found in the meantime) 
none of the LiveCDs make it to boot after about 20 minutes. (previously they worked fine)
looking at the errors it seems to be something about the harddrive.
Why the harddrive would stop the LiveCD booting is a mystery to me but the same messages appear when i select Recovery from the Grub menu so i guess the problem is related.

some boot-up errors
```

Sense: SCSI parity error ..
end_request I/O error, dev,sda, sector 17377...
lost page write due ti I/O error on dm-4
```

this sort of thing goes on for ever, every now and then it detects my USB mouse again and again so it seems to be a loop going around and around.

At the moment i'm on a Hardy LiveCD, earlyer i tried removing the ext4 partition but it had errors there as well and i can't touch the partition at all. (i can access the ntfs partitions)

```
sudo fdisk -ul
```
gives
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63103319    31551628+   7  HPFS/NTFS
/dev/sda2        63103320   165501629    51199155    7  HPFS/NTFS
/dev/sda3       165501630   169550009     2024190   82  Linux swap / Solaris
/dev/sda4       169550010   312576704    71513347+  83  Linux

```

after i try to format with Hardy gparted i am not able to find my hard drive at all anymore so i cant see how i could try to install Lucid again.

i haven't searched through all the threads that look similar to this but was hoping that while i'm searching someone else may have a good idea.
Its a bit annoying that i cant use the LiveCDs and after formating to ext4 i cant access that partition with Hardy either...
thanks

---

### Post by cholericfun on 2010-08-17
ok,

managed to boot into Jaunty,
trying to fix ext4 partition from there and hopefully get some results

---

### Post by cholericfun on 2010-08-17
so far managed to delete the linux partitions

also managed to boot into lucid

trying to instal gives me an error related to creating the partitions
so i started gparted and gparted tells me it cant create the partitions on empty space because the empty space "is apparently in use by the system"
???

---

### Post by cholericfun on 2010-08-18
ok

solved,
smart as i am i cant remember what exactly the program was and i couldnt find the thread again where i found it...

just had to install a program that enabled me to create the partitions and then the install just went smoothly

---

