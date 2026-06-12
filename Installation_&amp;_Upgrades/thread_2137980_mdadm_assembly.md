---
title: "mdadm assembly"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by FizzerUK on 2013-04-22
[SIZE=3]After a MoBo failure and upgrade I am trying to get my Arrays back in order.

Not trusting the automatic --assemble --scan... Had a raid assemble wrong before.


```

root@this:~# mdadm --examine /dev/sd[g,h,k]1

/dev/sdg1:
          Magic : a92b4efc
        Version : 0.90.00

           UUID : 04f02593:86ea8249:bfe78010:bc810f04
  Creation Time : Wed May  2 09:20:26 2012
     Raid Level : raid5
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1


    Update Time : Sat Feb 16 04:37:02 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c6a11f16 - correct
         Events : 9933

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     2       8       81        2      active sync   /dev/sdf1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       8      145        1      active sync   /dev/sdj1

   2     2       8       81        2      active sync   /dev/sdf1


```


```

/dev/sdh1:
          Magic : a92b4efc

        Version : 0.90.00

           UUID : 04f02593:86ea8249:bfe78010:bc810f04

  Creation Time : Wed May  2 09:20:26 2012

     Raid Level : raid5

  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)

     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)

   Raid Devices : 3

  Total Devices : 3

Preferred Minor : 1


    Update Time : Sat Feb 16 04:37:02 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c6a11f22 - correct
         Events : 9933

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     0       8       97        0      active sync   /dev/sdg1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       8      145        1      active sync   /dev/sdj1
   2     2       8       81        2      active sync   /dev/sdf1

```


```

/dev/sdk1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 04f02593:86ea8249:bfe78010:bc810f04
  Creation Time : Wed May  2 09:20:26 2012
     Raid Level : raid5
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Sat Feb 16 04:37:02 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c6a11f54 - correct
         Events : 9933

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     1       8      145        1      active sync   /dev/sdj1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       8      145        1      active sync   /dev/sdj1
   2     2       8       81        2      active sync   /dev/sdf1


```


Looking at this, am I correct in the assumption I can use the Number to select the correct order of assembly.

Due  to a hardware change /dev/sd[g,j,f]1 are obviously referencing the  wrong devices (I know this as they are different sized disks to the  actual array I bult)

So my Assembly would go something like:

```

mdadm --create /dev/md0 --assume-clean --level=5 --metadata=0.9 --chunk=128 --raid-devices=3 /dev/sdh1 /dev/sdk1 /dev/sdg1



```
[/SIZE]

---

### Post by darkod on 2013-04-22
No! Stay away from --create unless you have no other options. That is for creating new arrays, not assembling existing ones.

Actually the --assemble --scan is the standard option if your array doesn't have any errors. It should assemble it correctly.

But if you insist doing it by hand the first intent should be something like:
```
sudo mdadm --assemble /dev/md0 /dev/sd[hkg]1
```

See how that goes.

---

### Post by FizzerUK on 2013-04-23
> **darkod said:**
> 
But if you insist doing it by hand the first intent should be something like:
```
sudo mdadm --assemble /dev/md0 /dev/sd[hkg]1
```


I feel safer. I have identified the Disk that belong to the Arrays and the creation Time stamps match, and I have the order. Should not be a problem for 2 of the Arrays.

> **darkod said:**
> Actually the --assemble --scan is the standard option if your array doesn't have any errors. It should assemble it correctly.


That's the issue I have, I know one of the Arrays has issues. I did not want it to start reassembling it self hence **--assume-clean**

This is the problem Array:

```
[COLOR=#000000][FONT=Arial]Disk /dev/sdj: 1500.3 GB, 1500301910016 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sdj1:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]           UUID : 8fef02e6:b3e05c05:bb083459:d1daf435[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  Creation Time : Mon Sep 24 18:53:29 2012[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]this     0       8      129        0      active sync   /dev/sdi1[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Disk /dev/sdm: 1500.3 GB, 1500301910016 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sdm1:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]           UUID : 8fef02e6:b3e05c05:bb083459:d1daf435[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  Creation Time : Mon Sep 24 18:53:29 2012[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]this     1       8      177        1      active sync   /dev/sdl1[/FONT][/COLOR]
```

Should be a 3 drive RAID 5

Here is the drive that was failing and I had removed from the Array before my MoBo crashed. It wasn't failing it was being removed from the ARRAY due to the below...

```
[COLOR=#000000][FONT=Arial]Disk /dev/sde: 1500.3 GB, 1500301910016 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sde1:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]           UUID : 1d93f967:43a8f37f:bfe78010:bc810f04[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  Creation Time : Sun May  6 13:46:51 2012[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]this     2       8       97        2      active sync   /dev/sdg1[/FONT][/COLOR]

```

Looks like it's from a completely different Array. Which is quite possible. Being a low paid NOC Monkey I do my home server stuff on a shoestring. 

**Some BackGround:**
A while back I had 2 RAID 1 Arrays made up with 1.5TB drives. As on broke I thought It would be a good time to Make a RAID5 enabling extra space.

I did this on the fly, creating a new ARRAY using the exsisting 2 of the RAID1 disks. BUT created it with the **--level=5 **parameter and 1 disk lablled as **missing**.

Then add the extra disk from the faild array into it and let it rebuild.
I assumned I had wiped that Disk but looking at the UUID and Time stamp, obviously not.

Trying to find the Blog post that someone made and how they expanded the RAID1 arrays into RAID5's on the fly. Must have missed a step

NOW!!  I also have a none booting system, no biggie I can re-install BUT  I would like to try and recover it, practice for my Exams.
Boot is  in a small partion and / is in a 3 Disk array in RAID 5 with encryption.  I have fixed GRUB no boot systems before but this one is beating me! That's another issue probably for a different post.

---

### Post by darkod on 2013-04-23
You can try zeroing the superblock on sde1, and then adding it to the array you mentioned with sdj1 and sdm1 already in it. That should add it as brand new disk that was never in any of your arrays. Don't forget zeroing the superblock if switching members between arrays.

I know the --assume-clean option should keep your data safe when using --create, but in any case I don't see why not starting with --assemble first. If nothing works, you can go back to create with assume-clean.

You can do all of this from live mode if the machine is not booting. You only need to add the mdadm package first since the live cd doesn't have it.

It seems that you have more than one battles going on. What do you want to do first, add sde1 to the raid5 array or make the system boot first?

---

### Post by FizzerUK on 2013-04-23
[SIZE=2][FONT=arial]Thanks for the help...

Yep I am on my multiboot Live USB Tool drive at the moment.

So far so good.

All 3 arrays assembled.

```
[COLOR=#000000]mdadm --assemble /dev/md5 /dev/sd[l,i,f]1
mdadm --assemble /dev/md10 /dev/sd[h,k,g]1
[/COLOR]mdadm --assemble /dev/md15 /dev/sd[j,m]1
/dev/md15 has been started with 2 drives (out of 3).

```

Drive superblock zeroed.
Checked no superblock exsits.
Add to broken array.
Currently rebulding.

```
[SIZE=2]mdadm --zero-superblock /dev/sde1
mdadm --examine /dev/sde1
mdadm: No md superblock detected on /dev/sde1.
mdadm --manage /dev/md15 --add /dev/sde1
[/SIZE][/FONT][/SIZE]md15 : active raid5 sde1[3] sdj1[0] sdm1[1]
      2930274816 blocks level 5, 128k chunk, algorithm 2 [3/2] [UU_]
      [=>...................]  recovery =  9.3% (136504344/1465137408) finish=210.3min speed=105240K/sec[SIZE=2][FONT=arial][SIZE=2]
[/SIZE]
```

[SIZE=2]What's with the spare...
I am gu[SIZE=2]essing I should have removed the faulty first??  :(

[/SIZE][/SIZE][/FONT][/SIZE]```
[SIZE=2]root@this:~# mdadm --examine /dev/sd[e,j,m]1 | grep -e dev -e UUID -e Creation -e this
/dev/sde1:
           UUID : 8fef02e6:b3e05c05:bb083459:d1daf435
  Creation Time : Mon Sep 24 18:53:29 2012
this     3       8       65        3      spare   /dev/sde1
   0     0       8      145        0      active sync   /dev/sdj1
   1     1       8      193        1      active sync   /dev/sdm1
   3     3       8       65        3      spare   /dev/sde1

/dev/sdj1:
           UUID : 8fef02e6:b3e05c05:bb083459:d1daf435
  Creation Time : Mon Sep 24 18:53:29 2012
this     0       8      145        0      active sync   /dev/sdj1
   0     0       8      145        0      active sync   /dev/sdj1
   1     1       8      193        1      active sync   /dev/sdm1
   3     3       8       65        3      spare   /dev/sde1

/dev/sdm1:
           UUID : 8fef02e6:b3e05c05:bb083459:d1daf435
  Creation Time : Mon Sep 24 18:53:29 2012
this     1       8      193        1      active sync   /dev/sdm1
   0     0       8      145        0      active sync   /dev/sdj1
   1     1       8      193        1      active sync   /dev/sdm1
   3     3       8       65        3      spare   /dev/sde1

[/SIZE]
```[SIZE=2][FONT=arial][SIZE=2][SIZE=2]
[/SIZE][/SIZE]
As for the encrypted / drive.

I am at a loss. Assembled the array, it used to have a password at boot to decrypt.
Unsure what Ubuntu uses, dmcrypt or cryptsetup.

BUT I can not find an encypted header using either query tools.

Thought maybe it was mdadm > LVM > Encryption.

BUT pvscan reveals no LVM.

As far as I can tell, it's a blank array  :(


[/FONT][/SIZE]

---

### Post by darkod on 2013-04-23
I'm not 100% sure but I think it calls it spare until it finishes the rebuild. Only at that point it calls the member active. Which makes a little sense to me.

As for the encryption, I have no idea. Yes, a working encrypted system should ask you for the passphrase at boot, and it won't boot until you enter it. Did you maybe change the /boot partition needed for encrypted setup? Or it got messed up if the array was somehow messed up.

---

### Post by FizzerUK on 2013-04-23
Thanks..

Well I would like to work out how to fix an encrypted / (root) system.

But alas I need my server up and running.

There is nothing in there that I need so will probably have to re-install.

Just for competion, and if anyone knows how to fix such a system here is some info.

3 disk with 2 partions on each.
1 for ext2 /boot other RAID5 array

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e36da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1050623      524288   83  Linux
/dev/sda2         1050624  1953523711   976236544   fd  Linux raid autodetect
```

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa954

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     1050623      524288   83  Linux
/dev/sdb2         1050624  1953523711   976236544   fd  Linux raid autodetect
```

```
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ebc73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048     1050623      524288   83  Linux
/dev/sdd2         1050624  1953523711   976236544   fd  Linux raid autodetect

```

As the hardware changed I had no Boot, found the Boot drive but was gettting a Blank screen.
Fixed this via grub command prompt.
Then was getting Error 25, or changing the Boot partion it would say 'Loading OS...' then go to a Black screen.

Original menu.lst

```
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/TAFFY-root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Taffy 2.6.32-220.el6.x86_64
    root (hd0,0)
    kernel /vmlinuz-2.6.32-220.el6.x86_64 ro root=/dev/mapper/TAFFY-root rd_LUKS_UUID=luks-319304a8-59ce-4dea-be00-057fabb0b901  KEYBOARDTYPE=pc KEYTABLE=uk LANG=en_GB.UTF-8 quiet rd_LVM_LV=TAFFY/swap rhgb crashkernel=auto rd_LVM_LV=TAFFY/root rd_MD_UUID=645687c8:709714aa:cec5993b:da5d5323 rd_NO_DM
    initrd /initramfs-2.6.32-220.el6.x86_64.img
```

---

