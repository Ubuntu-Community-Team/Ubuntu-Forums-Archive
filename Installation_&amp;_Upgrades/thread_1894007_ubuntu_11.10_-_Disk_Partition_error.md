---
title: "ubuntu 11.10 - Disk Partition error"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by spulkit on 2011-12-11
i have a very weird problem i guess!!!i have the latest ubuntu installed and while installing i selected to install ubuntu side by side to windows 7 and do dual boot.

My windows that time had only one partition that is c. The ubuntu install made three new primary partitions alongside c of 3.86 gb 3.85 gb and 115.25 gb. Also there is system reserve of 100 mb and recovery of 13 gb. 
Now i wanted to split C and create a another drive so i shrank volume of c by a 100 gb but when i tried to create another drive it gae an error "cannot create a new volume in this unallocated space because disc already contains maximum number of partitions. "
when i deleted all the ubuntu drives i deleted grub bootloader also so couldnt boot windows . as a result i had to reinstall ubuntu again and install windows using recovery and i was back to where i was before. 

 Now i have no idea what to do . Please help !!

---

### Post by darkod on 2011-12-11
I always prefer to use the manual partitioning during install because it gives you more control. Especially in your case.
You already have 3 primary partitions, the system reserved, restore and the win7 partition.
You can only have one extended now with logical partitions inside it.

1. Is win7 shrinked again or not after the restore? If not, use Disk Management and shrink it again to leave enough space for ubuntu and for the 100GB partition you want.

2. After that is done, use the ubuntu cd and select Try Ubuntu to run it in live mode. Open Gparted and in the unallocated space create the 100GB partition you want. It needs to be logical, not primary. If you want win7 to also access it, create it as ntfs. Leave the rest of the space as unallocated for ubuntu.

3. Now boot with the ubuntu cd again and start the install. Either use manual partitioning and create your own root and swap partitions (plus separate /home if you want to), or use one of the auto methods and tell it to install into the unallocated space (there should be an option for that, I always use manual so I'm not sure how exactly the other options are called).

---

### Post by spulkit on 2011-12-11
ubuntu 11.10 is already installed along with windows 7 . Also i have an unallocated space of 100 gb . So all i need to do is format it to ntfs logical using ubuntu live cd as i cant do that using disc management utility in windows?

---

### Post by darkod on 2011-12-11
Depends, you can only create a logical partition from the 100GB if it's physically next to the other logical partitions on the disk.

Boot ubuntu and post the output of:
sudo fdisk -lu

---

### Post by spulkit on 2011-12-11
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9f9f7b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28311551    14154752   27  Hidden NTFS WinRE
/dev/sda2   *    28311552    28516351      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28516352   483366720   227425184+   7  HPFS/NTFS/exFAT
/dev/sda4       718888958   976771071   128941057    5  Extended
/dev/sda5       968685568   976771071     4042752   82  Linux swap / Solaris
/dev/sda6       718888960   960595967   120853504   83  Linux
/dev/sda7       960598016   968671231     4036608   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by spulkit on 2011-12-11
hey is there any way that i can convert my c drive (where windows 7 is installed ) to logical drive so that i can then extend it for creating more partitions without loosing any of the data?

---

### Post by darkod on 2011-12-11
```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    28311551    14154752   27  Hidden NTFS WinRE
/dev/sda2   *    28311552    28516351      102400    7  HPFS/NTFS/exFAT
/dev/sda3        28516352   [COLOR=Red]483366720[/COLOR]   227425184+   7  HPFS/NTFS/exFAT
/dev/sda4 [COLOR=Red]      718888958[/COLOR]   976771071   128941057    5  Extended
/dev/sda5       968685568   976771071     4042752   82  Linux swap / Solaris
/dev/sda6 [COLOR=Red]      718888960[/COLOR]   960595967   120853504   83  Linux
/dev/sda7       960598016   968671231     4036608   82  Linux swap / Solaris

```

You should be able to do it. You have the unpartitioned space between sda3 and sda4 which is the extended partition. sda6 is the first logical inside the extended.

First install Gparted in ubuntu, it's very good GUI tool for partitioning. When you open it, just select the unallocated space and create a new logical ntfs partition from it. At the end you will have to click the big green tick icon button in the Gparted toolbar, no changes are done until you click this. It should allow you this operation.

To install Gparted in terminal:
sudo apt-get install gparted

or just look for it in Software Centre.

---

### Post by darkod on 2011-12-11
> **spulkit said:**
> hey is there any way that i can convert my c drive (where windows 7 is installed ) to logical drive so that i can then extend it for creating more partitions without loosing any of the data?

There is, but every operation like that is a risk for the data. Usually the risk is not worth it. You have the 3 primary partitions at the start of the disk, so you can create as many logical as you want in the second part. Of course, how many partitions you can create and their size will depend on the unallocated space available.

---

### Post by spulkit on 2011-12-11
thank you so much (gparted being installed as i type )
also can you answer the question about the c partition that can i convert c drive into logical so that instead of shrinking space out of c drive  i can convert c drive to logical from primary and then create entended drives ?

---

### Post by spulkit on 2011-12-11
> **spulkit said:**
> thank you so much (gparted being installed as i type )
also can you answer the question about the c partition that can i convert c drive into logical so that instead of shrinking space out of c drive  i can convert c drive to logical from primary and then create entended drives ?
you already answered that too . Thank you :)

---

### Post by spulkit on 2011-12-11
**It is not possible to create more than 4 primary partitions.**
If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.

when i right click and select new on unallocated space i get this message. no other options except "new" and "information" and clickable.

---

### Post by darkod on 2011-12-11
Hmm, strange. I wonder if the problem is that you are running it from within ubuntu.

Try booting with the cd in live mode, open Gparted (it's included). The swap partitions will have a keys symbol, that means they are mounted. Right click on them and select swapoff.

The keys symbol should go away from sda5, sda7 and sda4.

Try again right clicking the unallocated space and see if it allows you to create logical partition.

If not, the only other option would be to resize sda4 so it includes the unallocated space. There is small risk involved but usually it works out fine. In Gparted above the partition list where the layout is shown like a bar, drag the left border of sda4 to the left until it includes the unallocated space. After that it should allow you to create logical partition inside sda4. Try this resize only if the option above doesn't work.

---

### Post by spulkit on 2011-12-11
another thing happened as i was not able to create another partition i deleted the 100mb system reserve and then formatted unallocated space to primary partition now ..when i try to boot to windows it says  no such device. then it says bootmgr is missing . :'( is windows gone?

---

### Post by darkod on 2011-12-11
No, windows is not gone but its boot files are. The system reserved partition hold two boot files for win7. It can't boot without them.

If you have a win7 rescue cd you might be able to repair the boot, it will put the files back but this time to the win7 partition.

---

### Post by spulkit on 2011-12-11
i dont have a rescue cd but the recovery feature of the vaio which i have tested before and is not able to repair boot problem in grub. 
so this is what the best i can think off to do . 
1st)reinstall ubuntu as it will reinstall grub and thus repair the windows damage . 
2nd) use easybcd software in windows to uninstall ubuntu. 
3rd) uninstall ubuntu manually or inside windows.

correct me if i am doing anything wrong?

---

### Post by darkod on 2011-12-11
Ubuntu can't repair the missing win7 files. We are not talking about the bootloader on the MBR. Win7 has 2 boot files that are present on that small 100MB partition (when it exists, it can function without it but depends on the way it is installed). Without these 2 files ubuntu can't help, they are part of the win7 boot process.

You could do the factory restore again but that will delete the ubuntu and all your data on the disk. Note that you can still access the data from ubuntu so you can copy anything you need on external HDD first.

---

### Post by spulkit on 2011-12-11
So actually my windows is gone . sad . so now this is what i sould do. copy everything, Hard reset everything and install everything again. cool . Its going to be a long long night . 
btw thank you very much :))

---

### Post by darkod on 2011-12-11
Don't forget to plan the partitions in advance. Right after you do the restore and the shrinking, sit down and calculate what and where you would like to install.

---

### Post by spulkit on 2011-12-11
> **darkod said:**
> Don't forget to plan the partitions in advance. Right after you do the restore and the shrinking, sit down and calculate what and where you would like to install.
i surely will

---

