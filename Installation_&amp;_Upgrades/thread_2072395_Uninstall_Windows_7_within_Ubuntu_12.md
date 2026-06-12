---
title: "Uninstall Windows 7 within Ubuntu 12"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by iiVoxel on 2012-10-17
ALright, well I want to be SURE I do this right so I came here to make sure cause every post seems to have a very good solved answer!

Well, basically I'm pretty sure you need some info first! (duh) Alright, Well I have Windows Vista on the C: drive partition, and I have Windows 7 on the W: drive partition, and I installed Ubuntu 12.04 with a burned CD iso image.


My question is, I dont believe I can ever delete my C: drive since it has the MBR I believe? So how do I uninstall windows 7 from the W: partition SAFELY from Ubuntu WITHOUT messing up my Ubuntu "partition" (its on a different one)

Just want to make sure I know how in case any problems arise, so yeah! BTW, I have a system restore point for windows 7 in case anything goes wrong, and the burned ISO image for Ubuntu install on a CD, so I believe I'm good on backups??

---

### Post by zvacet on 2012-10-17
If grub is your bootloader then just uninstall Windows 7 and boot Ubuntu and in terminal type 

```
sudo update-grub
```

---

### Post by iiVoxel on 2012-10-17
Well yes, I know that bit, but how to I actually go about uninstalling windows 7? and make sure I don't uninstall Ubuntu?

And lets say I *do* uninstall Ubuntu by accident, can I just pop in my Ubuntu ISO burned CD disc and re install?

---

### Post by iiVoxel on 2012-10-17
Oh, and for just a little bit more info, in GParted app for Ubuntu,
It says I have /dev/sda1.../dev/sda2.../dev/sda3 and within that there is /dev/sda 5 and /dev/sda6 with sda6 being the mount point of "/" and is ext4, while sda5 is ntfs, is blank for the mount point and the label says "windows 7" does that mean my 6th partition has Ubuntu and the 5th one has windows 7 and I could safely right click on 5th one to format to ext4 to give more space for the "Ubuntu partition", oh and below those two it says /dev/sda4 with label of PRESARIO_RP (the disc drive I'm guessing??)

---

### Post by ajgreeny on 2012-10-17
You first need to know the partition layout of your computer which you can get from command ```
sudo fdisk -l
``` in terminal.  You then need to interpret the partitions shown as sda1 sda2 etc etc into your C:\ and W:\ which is the windows way of naming partitions as disks.

Get that far and report back here the terminal output if you're not sure and someone will help you with the correct partition(s) to delete, and how most easily to do it.

For safety, I suggest you use gparted on your live Ubuntu CD/USB to carry out the deletion, but it is up to you; you can use terminal commands if you prefer.

EDIT:
OK, I see you've found gparted, so can you let us see a screenshot of that window, please, just to be sure.  Make a screenshot with the printscreen key, save it to disk and then use the paperclip in the toolbar of the reply box in the forum, navigate to the image and upload it.

---

### Post by iiVoxel on 2012-10-17
Here is the terminal code
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24837113

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      239615      118784    7  HPFS/NTFS/exFAT
/dev/sda2   *      240975   107169614    53464320    7  HPFS/NTFS/exFAT
/dev/sda3       107169790   370122751   131476481    f  W95 Ext'd (LBA)
/dev/sda4       370122752   390715391    10296320    7  HPFS/NTFS/exFAT
/dev/sda5       107169792   274937855    83884032    7  HPFS/NTFS/exFAT
/dev/sda6       274939904   370122751    47591424   83  Linux

```

Also, I attached an image of gparted, the highlighted orange one is the one I think is the linux one, and the one above I think is the Windows 7 one.

---

### Post by ajgreeny on 2012-10-18
Yes, you are correct sda6 is your ubuntu partition, a logical partition contained within the extended sda3.

You only have the one partition for ubuntu and are running without any swap, not a major problem if you have plenty of physical ram, but you will not be able to to suspend or use hibernation without swap.

I see your Windows 7 partition, sda5, is a logical one inside sda3 which I find surprising as I did not think windows would boot from a logical partition.  I presume sda4 is the Win 7 recovery partition, and sda1 the windows boot partition, but that is where my knowledge of windows ends, not having run it for about three years, and then having XP which was much easier to deal with when dual booting than the more recent versions.

However, to get back to your original question.  If you want to get rid of windows completely from your machine, boot to ubuntu live CD/USB and simply run gparted and delete sda1, sda2 and sda5.  You could keep sda4, the recovery partition, though I have no idea how you use that if you have no windows bootloader on the machine.  That will leave you with empty space at the start of the disk where sda1 and sda2 were placed, and some empty space in the extended sda3 partition which can be resized over the whole disk if you are using only Linux on the machine.  I then recommend you to add a swap partition equal in size to your ram. As grub is now your bootloader the removal of the windows partitions will not affect anything about booting the computer, as grub is not on a partition but at the root of the disk, in the first 63 (I think) sectors of the disk.

The rest of the empty space can be used as a separate /home partition if you wish, and another just for data, or you could move the ubuntu partition to the start of the disk using gparted.  It can take a long time to move partitions, and you MUST BACKUP FIRST just in case something goes wrong, but I have recently done it several times without a murmur from the moved OSs when next booted.

If you want to remove just win7 and keep vista, I'm afraid I will have to leave that to other, more windows aware users.

---

### Post by buckyaustin on 2012-10-18
To be honest I would just use Gparted or anything similar to it, and delete the C: drive. Then run "sudo update-grub". This will fix your grub. Then boot to a live iso and use Gparted to organise the hard drive partitions as you please. This seems to be the easiest solution I could come up with.

---

### Post by iiVoxel on 2012-10-18
Thank you for the replies!

To Bucky: If I deleted the C: drive wouldnt that delete the MBR?

To others: How can I completely remove Windows 7 BUT keep vista?

Since I THINK the first partition, sda1, would be the "primary" partition since its "1", and the flag on sda2 says boot, I dont guess I could delete that either, So, If I just removed the sda5 would that remove windows 7 (and not vista, I'm thinking sda2 is the vista partition since its says boot and vista was the pre installed OS on this computer)?

And To AJ: Thanks for the help man! Even though you can't completely resolve my problem, I have learned a lot about this stuff and Ubuntu from you, (I've only had it 3 days now!) I thank you!

-Voxel

---

### Post by CLCressman on 2012-10-18
I would highly recommend that you make a backup of everything, from all partitions, that you might want in the future, that you would find difficult to replace. Do not make it on any partition of the drive that you are doing partition work on. Because if you make a mistake, it can be difficult recover. If you make two mistakes in a row it can be just about impossible.

If you are not absolutely sure that the drive label of W: is indeed "Windows 7",  boot into Windows and check it. Also make sure that you have a backup of anything on the "Windows 7" disk (Windows calls it a drive, it is actually a partition) that you might want in the future. A System Restore point will do you no good after you delete everything on your "Windows 7" disk.

Now if you are sure that you are ready to delete the partition labeled "Windows 7", boot Ubuntu from your CD. Use gparted  to delete the "Windows 7" partition, it may not be called /dev/sda5 when you have booted from your CD.

Then move your ext 4 partition as far forward as it will go. Make a swap partition at the end of the free space you just made, and stretch your ext 4 partition to take the rest of the available space. Unless of course you have a scheme that you like better.

When you boot into your installed version of Ubuntu run "sudo update-grub" to update your boot menu.

I believe your "PRESARIO_RP" partition is designed to restore your computer to the factory state. If you don't want that possibility, then you can delete it as well.

---

### Post by iiVoxel on 2012-10-18
Alright, Well I get Windows 7 Unistalled! (Thank You ALL!) And NOW, if I set aside a partition like I have here (in the screenshot!) when I install programs, can I choose to install it to that partition? and If I can only install it the one labeled Ubuntu OS, Is there any simple way to merge the two without having to reinstall Ubuntu? 

Thanks for all the help people!

<3 Ubuntu! -Voxel

---

### Post by CLCressman on 2012-10-21
> And NOW, if I set aside a partition like I have here (in the screenshot!)  I don't see a screen shot in that post, but I think that I can answer your question without it. The partition that the programs get installed to is normally determined by which directory you have your partition mounted to. In Ubuntu all mounted partitions are mounted to a directory, not a drive like Windows. The Ubuntu default is, everything except 'swap' is in one partition. It is my understanding that the majority of people use that default. That means that your Ubuntu partition is mounted at "/" which is the root directory of the file system, not "C:\" as in Windows. Now if you feel like you want something different, with Ubuntu you are free to mount your partitions as you like, provided they are formatted compatibly.

> Is there any simple way to merge the two without having to reinstall Ubuntu? If your drive  looks like your first screen shot, then can you follow these instructions?> boot Ubuntu from your CD. Use gparted  to delete the "Windows 7"  partition, it may not be called /dev/sda5 when you have booted from your  CD.

Then move your ext 4 partition as far forward as it will go. Make a swap  partition at the end of the free space you just made, and stretch your  ext 4 partition to take the rest of the available space. Unless of  course you have a scheme that you like better.

When you boot into your installed version of Ubuntu run "sudo update-grub" to update your boot menu.If something is not clear, let us know.

> To Bucky: If I deleted the C: drive wouldnt that delete the MBR?If you don't care about being able to boot Windows without 'Grub', then you don't need to worry about your MBR. Between 'Gparted' and 'Grub' you will be taken care of.

> Since I THINK the first partition, sda1, would be the "primary"  partition since its "1", and the flag on sda2 says boot, I dont guess I  could delete that either,In your first screen shot, sda1,sda2, sda3, and sda4 are all "primary" partitions. Sda3 is a special type of primary (extended) in that it is a container for "logical" partitions. In the _Windows_ (and DOS before it) _scheme_ of things a physical drive can have up to 4 primary partitions of which one can be marked "bootable" (this tells the program in the MBR which partition holds Windows). When 4 partitions was too confining, they came up with the extended (container) partition subdivided into logical partitions (for most practical purposes you can have as many as you can keep track of with the letters of the alphabet) Ubuntu can use the Windows scheme among several.

---

