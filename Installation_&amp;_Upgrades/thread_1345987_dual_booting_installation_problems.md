---
title: "dual booting installation problems"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by krnbob246 on 2009-12-04
Hey!
I just recently installed ubuntu and I wanted to set up a dual booting system. I wanted to downgrade my windows OS from vista to xp sp3 so I had ubuntu take over my entire hard drive.
afterwards I had i used Gparted to create a new unallocated partition. I put my windows xp sp3 CD and rebooted.
everytime it starts loading all the xp files from the cd and after its done I get the blue screen of death. anyone know why this might be happening. I've burned 3 different CDs using Imgburn at 16x, 8x and 4x. All of them dont work =(

---

### Post by darkod on 2009-12-04
If you already planned to install XP it's very bad practice to let one OS take the whole drive and then shrink right after that. Very easily some corruption in the files can happen and make the system unusable.
Also, if Ubuntu is first on the drive now, on primary partitions, and you put XP on extended (logical) partition, it can't boot from logical partition.
If you post the results of:
sudo fdisk -l (small L)

we might find out more.

---

### Post by krnbob246 on 2009-12-04
Here's the info thanks for helping me out

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e6d666c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11065    88879581   83  Linux
/dev/sda2           29285       30401     8972302+   5  Extended
/dev/sda5           29285       30401     8972271   82  Linux swap / Solaris

And when you say that it makes the system unusable do you mean the OS or the Harddrive?

---

### Post by krnbob246 on 2009-12-04
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e6d666c

---Device Boot-----Start-------End-------Blocks-----Id--System
/dev/sda1 --*--------1--------11065-----8879581---83--Linux
/dev/sda2 ---------29285------30401----8972302+--5--Extended
/dev/sda5 ---------29285------30401----8972271---82--Linux swap / Solaris

reposting the stats since it was all jubled

---

### Post by darkod on 2009-12-04
I meant the OS might be unusable with corrupt files. Don't worry about the HDD.
Where is your XP? You have no ntfs partition here, just the gap between 11065 and 29285.

---

### Post by krnbob246 on 2009-12-04
everything in between is unallocated.

i had Linux take over my harddrive and then i used gpart to create another partition everything from 11065 to 29285

---

### Post by krnbob246 on 2009-12-04
think it might help if i reinstalled ubuntu

---

### Post by misterbk on 2009-12-04
When you say it "starts loading up the XP files from the CD", what exactly is it doing?  Is it loading from the CD to start the installation process, or have you finished telling it what partition to go to and all that, and it's putting XP on the hard drive?

One of the unfortunate things about the XP installer is it didn't come with support for nice things like SATA controllers.  So you have to use a floppy disk (Remember those??!!??) with your SATA drivers on it or you can't install to a SATA disk.  They may have fixed that if your XP disk is SP3, but I think it was still that way with SP2.

It could also be getting in a fight with Grub.  Could also be getting in a fight with a bios-based virus inhibitor...  Check bios to make sure it isn't write protecting the boot sector.  (Though if you installed Ubuntu OK, that option seems unlikely.)

If you don't mind reinstalling at this point, try installing XP first and taking over half the drive.  Then use the Ubuntu installer second, since it is much better designed for installing cooperatively alongside another OS.

---

### Post by krnbob246 on 2009-12-04
"starts loading up the xp files from the CD"
is like before the you choose what partition to install it in
i think right before it gets to that screen, it blue screens my face

and is there a way to wipe the hard drive of any OS it has installed on it? i think that might be the only way i can get my laptop to install xp

and ill get onto checking those things right now

---

### Post by darkod on 2009-12-04
You can wipe it with ubuntu cd selecting Try Ubuntu option. That will run it from the cd. Open Gparted. If swap is mounted right-click and select swapoff. Other partitions shouldn't be mounted. If they are right-click and do unmount.
Gparted will allow you to delete all partitions, in effect wiping the hdd. Make SURE this is what YOU WANT!!!!!!!

---

### Post by krnbob246 on 2009-12-04
Alright. Thanks guys. Problem solved.

Misterbk was right. its because my HDD is a SATA. I wiped everything using the way darkod told me and it still blue screen of deathed me. So i tried installing vista and it works fine. Ill reinstall ubuntu after finals are over for me. Thanks guys

---

