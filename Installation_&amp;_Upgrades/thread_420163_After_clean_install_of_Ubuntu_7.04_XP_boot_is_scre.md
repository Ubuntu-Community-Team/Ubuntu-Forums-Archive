---
title: "After clean install of Ubuntu 7.04 XP boot is screwed up"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by mijj on 2007-04-23
prior to installing Ubuntu 7.04 i had the following partitions:

first partition: XP (hidden: minimum XP config plus browser, IM, system tools - there to be made active in an emergency)
(   boot.ini:
    [boot loader]
    default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
    [operating systems]
    multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP Minimum" /noexecute=optin /fastdetect
)

second partition: XP (active: full bloated system - main used system)
(   boot.ini:
    [boot loader]
    default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
    [operating systems]
    multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="XP Bloat" /noexecute=optin /fastdetect
)
+ 20GB free space

+ Logical ntfs data partitions.

Prior to Ubuntu 7.04 install, switching between active parittions for XP worked fine and as expected. (using a boot switching tool within windows)

**After** clean install of Ubuntu 7.04 the grub boot manager allows the selection of the two XP partitions.
Selecting the first XP partition results in a failed boot because Windows cannot find a particular dll.
Selecting the second XP partition results in a boot resulting in a strange mix of the first and second XP partitions with lots of windows confusion about system files.

Deleteing the Ubuntu installed partitions and using the XP install disk to fixmbr got my system back to normal.

I've gone through the install twice .. same result.

The XP is my working system... I'd like to try out and possibly migrate to Ubuntu if it's feasible. (I have no intention of heading into Vista)   However.  I'm not willing to modify my current working XP systems to accomodate a Ubuntu trial.

Is there any way to install Ubuntu in such a way that there's no threat to my current XP arrangement?

---

### Post by mijj on 2007-04-23
:(

the silence is deafening.

It looks like i'm going to need to wait 6 months for the next release to see if that works alongside XP.

---

### Post by sque on 2007-04-23
Your probably messed up the partition table!

Post an fdisk -l /dev/(what is your disk) here. before asking help

---

### Post by mijj on 2007-04-23
partitioning is ok before installing Ubuntu and it's ok after deleting Ubuntu paritions and using an XP disk to fixmbr.

"fdisk -l /dev/(what is your disk)"  .... I have no idea what that is ... I assume that's an instruction within Ubuntu ... do i need to reinstall Ubuntu to use that instruction?

here's partition info via XP (after removing Ubuntu and fixing the mbr) ...

[IMG]http://www.mijj.info/misc/Partitions.jpg[/IMG]

the first partition is a hidden minimum XP partition.  The second partition is the working bloated XP partition.

What other info would be useful? ... i'll reinstall Ubuntu again to get it if i need to, but i'd rather know what i'm looking for before i reinstall.

---

### Post by sque on 2007-04-23
Omg! Do you really need all those partitions? :P

Ok here is the story of Windows.
Windows need the first accessible by windows partition (NTFS or FAT) to install their bootloader. And they call it "C:" even though you may not install windows in that partition. That's why sometimes you see PC with windows that is not in "C:" and the "C:" may just be an empty partition. Along with the boot-flag in partition table, this story can be very complicated.

I can't imagine how you setted up your partitions when installed linux. So either you give a full description what was the partition order (WITH THE LINUX) and the boot-up flags (if you remember). 
Or you try to install them again and after installation you run the following commands(Prefered)
sudo fdisk -l /dev/hda 
sudo fdisk -l /dev/sda

and copy paste the result of each command here. To find out what went wrong. But dont expect to get help for sure, as it is more a windows problem and a bad mixing of partitions by you :/ (no offence, just advice :) )

In my opinion your problem is fixable.

---

### Post by mijj on 2007-04-23
ok ... i'll reinstall Ubuntu and record the partitioning info ...

... I let Ubuntu decide on partitioning from the largest contiguous free space the last times i installed.

(here we go ....)

---

### Post by mijj on 2007-04-23
ok .. i resinstalled Ubuntu ..

at the point of partitioning the disk:
> How do you want to partiton the disk?
* Guided - use the largest continuous free space.


I did a system update.

And installed ntfs-3g, ntfs-config (so i could make notes to a ntfs partition for windows later)
and gparted (for a graphical look at the partitions).

here's the info:
> sudo fdisk -l /dev/hda - no result

sudo fdisk -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        5092        7538    19655527+  83  Linux
/dev/sda2               1        1566    12578863+  17  Hidden HPFS/NTFS
/dev/sda3            7539       30401   183647047+   5  Extended
/dev/sda4            1567        5091    28314562+   7  HPFS/NTFS
/dev/sda5            7651        9609    15735636    7  HPFS/NTFS
/dev/sda6            9610       15984    51207156    7  HPFS/NTFS
/dev/sda7           15985       22359    51207156    7  HPFS/NTFS
/dev/sda8           22360       28734    51207156    7  HPFS/NTFS
/dev/sda9           28735       30401    13390146    7  HPFS/NTFS
/dev/sda10           7539        7650      899577   82  Linux swap / Solaris

Partition table entries are not in disk order


[IMG]http://www.mijj.info/misc/GParted.png[/IMG]

---

### Post by sque on 2007-04-24
1st of all your partitions are scrambled. The order is not right... So lets fix it...

Try this, open a console
sudo fdisk /dev/sda
(enter your password...)
press x + enter
press f + enter
press w + enter

After that reboot your system.
If your grub is well informed about the partitions of windows, the problem may be fixed.
If not run: cat /boot/grub/menu.lst
and copy-paste results (it should be quite big)

---

### Post by mijj on 2007-04-24
I made a copy of menu.lst when i was in Ubuntu getting the partition info ... this is the relevant part of menu.lst associated with teh partition info listed above ...

```
default		0
timeout		10

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=85172218-8142-4536-97ce-5457b1aa3d6d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		XP minimum
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		XP bloat
root		(hd0,3)
savedefault
makeactive
chainloader	+1
```

Next: I'll install Ubuntu again and make the partition order descrambling changes you suggested above. Presumably, i'll need to change menu.1st to reflect any changes in teh way partitions are identified to linux.

---

### Post by mijj on 2007-04-24
ok .. i finally have success.  Not a complete solution tho.

so thanks, ***[SIZE="3"]sque[/SIZE]*** ... it looks like getting the order linux sees the bootable partitions to be the same as the order that windows sees the bootable partitions is the solution.

Because i have two bootable XP partitions, i need an extra step to switch active xp partitions where I hide the none active xp partition and unhide the active partition ... grub doesnt take care of that.

For that reason, it gets a bit fiddly swiching between XP boot partions using Grub.

I think i may need to use a boot manager on a floppy or something.   And have the hard drive boot as a windows system.  ... maybe ... somehting like that.

anyway .. these are the steps i took to get the boot selection via grub working ...

1. (failed attempt)
  use the install disk to order the partitions via the instruciton:
sudo fdisk /dev/sda
x
f
a
- this resulted in the partitions starting with the first as sda2 then sda3 - dunno why

2. Install Ubuntu and *then* use the instruciton
sudo fdisk /dev/sda
x
f
a
- this time the bootable partitions are in the expected sequence .. starting with the first as sda1
- then edited menu.lst to account for the different identification of the partitions.  ( I checked a copy of this with the final version - they were the same)
- this failed to reboot into Ubuntu .. message: Error 17 - could this be something to do with the swap partition having an unaccounted for different sda?

3  Install Ubuntu again deleteing the partions on which Ubuntu was previiously installed.
- ***[COLOR="Red"][SIZE="2"]success[/SIZE][/COLOR]***.
- booting into the unhidden Windows succeeded ... however .. it took an excrutiatingly long time to boot up.  I thought it was a fail but it got through .. i rebooted three times .. after the third time it got down to a normal boot time.
- using grub to boot into the alternate xp partition required unhiding the new active partition and hiding the old activbe partition.

:)

So .. the next step is to find an alternative boot manager that will fit onto a floppy.

---

### Post by mijj on 2007-04-25
well well ... it seems Grub has instructions to hide and unhide partitions.



The Ubuntu installation doesnt automatically create an appropriate menu.lst to allow for multiple Window boot partitions to boot correctly.  So menu.lst needs to be adjusted by hand.

so .. [COLOR="RoyalBlue"]*in case anyone is reading this .. a summary*[/COLOR] (from the keyboard of a novice) ...

On startup - if selecting XP results in the XP boot screwing up ...

1   
     check that Windows and Ubuntu see the boot partitions as being in the same order. (thanks, ***sque***)
     (Windows sees them in the order they're placed physically on the disk.)
     (as far as i can tell, linux sees them in the order they were created in time (edit: no ... that's not right ... i dont have a clue what the logic is for how linux decides on the order of the partitions) - my experience is that if you change the linux-seen order to correct for this problem, then Ubuntu needs to be reinstalled.  (even with menu.lst adjusted for teh new order for sake of Grub ... error 17 results on boot... maybe an expert will give instruction on how to change the order *and* have the same installation of Ubuntu work.)

2   
     if there's more than one Windows boot partition - ensure that the appropriate windows partitions are hidden and unhidden in the selected menu.lst Windows option.
( ref: hide, unhide [_[COLOR="SeaGreen"]http://www.gnu.org/software/grub/manual/grub.html[/COLOR]_]("http://www.gnu.org/software/grub/manual/grub.html") )

--------------------------------------------------------------------

So ... <wipes away tears of joy> ....

On startup, I can finally select between my two XP partitions and Ubuntu in the way i expected it to happen when i made my first naive attempt at installing Ubuntu.

And now, after about 8 installs and hours and hours of blood, toil, sweat and tears, I can finally start messing with Ubuntu itself.  

I expect that i will have no more problems whatsoever.

:)

---

