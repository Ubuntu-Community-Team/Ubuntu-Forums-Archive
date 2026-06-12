---
title: "Help: need to install everything including boot loader in another drive"
date: 2015-07-10
forum: Installation &amp; Upgrades
---

### Post by Ashesh_Shrestha on 2015-07-10
I have an old laptop whose C and D drive have lots of bad sectors but  none in other drives. I have been keeping an eye on bad sectors and  they are not increasing. I installed Ubuntu in E drive but after some  times it gets corrupted. So I deleted those(C & D) drives but still  the problem is persistent. Can I know how can i fix it?  
  I thought moving boot loader to next drive would help but on installing boot loader on other drive, I get 

```
error: no such partition.
Entering rescue mode...
grub rescue>
```
how should I install boot loader to fix this problem? or is there a  problem in MBR? There are no bad sectors on first 60 mb of hard drive.
  I don't want to replace hard drive. It is my secondary pc.

---

### Post by dino99 on 2015-07-10
C, D, E, ... are the 'windows' partitions naming. Linux (ubuntu) named them as /dev/sda, /dev/sdb, ...
so if you want to install the bootloader on a drive named /dev/sda, then from a terminal, run: > sudo grub-install /dev/sda
you can get that naming with that other command:  > sudo blkid

note: maybe you can reformat the faulty drive(s) with bad sectors: simply boot with gparted live cd/usb (only if you does not care about the data stored on the faulty device (or do a backup first)

---

### Post by Ashesh_Shrestha on 2015-07-10
> **dino99 said:**
> C, D, E, ... are the 'windows' partitions naming. Linux (ubuntu) named them as /dev/sda, /dev/sdb, ... so if you want to install the bootloader on a drive named /dev/sda, then from a terminal, run:  you can get that naming with that other command:    note: maybe you can reformat the faulty drive(s) with bad sectors: simply boot with gparted live cd/usb (only if you does not care about the data stored on the faulty device (or do a backup first)  While installing ubuntu I selected sda2 partition for boot loader. Is it different from command > sudo grub-install /dev/sda2 because at that time I got error after installation was complete > error: no such partition. Entering rescue mode... grub rescue> Should I place /root anywhere or let it be as in default?  Thanks for quick reply!

---

### Post by grahammechanical on 2015-07-10
How many hard drives do you have? Windows will call a partition a hard drive. So, at the moment I am not clear if you have 4 actual hard drives or one hard drive with 4 or 5 partitions.

I ask this question because if you have bad sectors on partitions of a hard drive then you have bad sectors on the hard drive. The hard drive might not be in good condition.

Do you have another operating system on the machine?

sda2 is the second partition of the first hard disk (sda). The error message does not relate to where you installed Grub but to Grub looking at a specific partition to load a Linux kernel. Which partition is Ubuntu installed on to? Grub will look to that partition for its configuration files and a Linux kernel to load. And either that partition no longer exists or grub is looking in the wrong place.

Regards.

---

### Post by dino99 on 2015-07-10
> **Ashesh_Shrestha said:**
> While installing ubuntu I selected sda2 partition for boot loader. Is it different from command  because at that time I got error after installation was complete  Should I place /root anywhere or let it be as in default?  Thanks for quick reply!

dont change the default ubuntu installation settings , only install grub to /dev/sda, followed by 'sudo update-grub'

---

### Post by oldfred on 2015-07-10
A few bad sectors are not the end of the world, but increasing amounts of bad sectors is not a good sign. 
I would use Disks and click on icon in corner and see what drive's Smart Status is. Passed means problems are minor.

Drives only boot from MBR or first sector on a hard drive. That sector is not in any partition. But you cannot easily or normally boot from the partition's boot sector or first sector in a partition.

---

### Post by Ashesh_Shrestha on 2015-07-10
> **grahammechanical said:**
> How many hard drives do you have? Windows will call a partition a hard drive. So, at the moment I am not clear if you have 4 actual hard drives or one hard drive with 4 or 5 partitions.

I ask this question because if you have bad sectors on partitions of a hard drive then you have bad sectors on the hard drive. The hard drive might not be in good condition.

Do you have another operating system on the machine?

sda2 is the second partition of the first hard disk (sda). The error message does not relate to where you installed Grub but to Grub looking at a specific partition to load a Linux kernel. Which partition is Ubuntu installed on to? Grub will look to that partition for its configuration files and a Linux kernel to load. And either that partition no longer exists or grub is looking in the wrong place.

Regards.

I do have only one harddrive and 4 partitions in them. Yes I know they might fail but it is my secondary laptop not the primary one and there is only OS (ubuntu) installed. I created  a partition sda3 and selected bootloader path to sda3. So what did I miss there? Should I be installing manually? Can you please elaborate a bit more?

---

### Post by Ashesh_Shrestha on 2015-07-10
> **dino99 said:**
> dont change the default ubuntu installation settings , only install grub to /dev/sda, followed by 'sudo update-grub'

If I don't change the default ubuntu settings while installing,  everything works fine for some days(there is no problem with grub too)  and finally things starts to fall apart. At first, errors starts to  appear and slowly it creates more errors and finally stops booting. Once  or twice, my laptop failed to notice the harddrive(though not often) so  I guess MBR might also have been corrupted. I don't know anything about  that; just guessing. When I ran badblocks, I found there are bad  sectors starting from 55mb from the beginning of the disks and are  randomly present to first 100gb. I do have deleted those partitions. I  guess installing all files on other partition might fix that problem but  I can't seem to install bootloader to any partition that has no bad sectors  instead of installing it to sda which I guess starts from the beginning  of drive including those damaged blocks. Is there a way to create a  file in that first 55mb disk like a pointer that points to other files  to boot ubuntu?

---

### Post by Ashesh_Shrestha on 2015-07-10
> **oldfred said:**
> A few bad sectors are not the end of the world, but increasing amounts of bad sectors is not a good sign. 
I would use Disks and click on icon in corner and see what drive's Smart Status is. Passed means problems are minor.

Drives only boot from MBR or first sector on a hard drive. That sector is not in any partition. But you cannot easily or normally boot from the partition's boot sector or first sector in a partition.

Is there a way to know if MBR has been corrupted? After initial 55mb sizr, there are bad sectors upto about 100gb. Or is there a seperate small storage for MBR? Is there a way to make a pointer like thing that points where the bootloader is installed becasue I can install bootloader only on sda not on sda1 or any other partition.

---

### Post by oldfred on 2015-07-10
MBR is just the first sector of a hard drive. 

But for systems to boot MBR is too tiny to have entire boot code, so MBR just points to more boot code inside system whether Windows or Linux.

---

### Post by Vladlenin5000 on 2015-07-10
> **Ashesh_Shrestha said:**
> If I don't change the default ubuntu settings while installing,  everything works fine for some days(there is no problem with grub too)  and finally things starts to fall apart. At first, errors starts to  appear and slowly it creates more errors and finally stops booting. Once  or twice, my laptop failed to notice the harddrive(though not often) so  I guess MBR might also have been corrupted. I don't know anything about  that; just guessing. When I ran badblocks, I found there are bad  sectors starting from 55mb from the beginning of the disks and are  randomly present to first 100gb. I do have deleted those partitions. I  guess installing all files on other partition might fix that problem but  I can't seem to install bootloader to any partition that has no bad sectors  instead of installing it to sda which I guess starts from the beginning  of drive including those damaged blocks. Is there a way to create a  file in that first 55mb disk like a pointer that points to other files  to boot ubuntu?


Your disk is failing, period. Not just a partition, the whole drive. Your understandable confusion between partition and drive - understandable because we know from where it comes from, as explained by Dino - is leading you into the wrong assumption that it's OK to use 'drive E:' (just a partition actually) to install... No, it isn't. Rarely if ever the growing number of bad sectors is confined only to a portion of the drive. The corruption you've been experiencing is most likely due to new bad sectors.
As commented before, _some_  bad sectors isn't the end of the world. However, if the number of said bad sectors increases - and it clearly does - you can't use that drive reliably and the problem will only get worse.
There's nothing you can do about it with software. It's a physical problem and you'll have to replace that disk and sooner than later, I'm afraid.

---

### Post by Ashesh_Shrestha on 2015-07-10
> **Vladlenin5000 said:**
> Your disk is failing, period. Not just a partition, the whole drive. Your understandable confusion between partition and drive - understandable because we know from where it comes from, as explained by Dino - is leading you into the wrong assumption that it's OK to use 'drive E:' (just a partition actually) to install... No, it isn't. Rarely if ever the growing number of bad sectors is confined only to a portion of the drive. The corruption you've been experiencing is most likely due to new bad sectors.
As commented before, _some_  bad sectors isn't the end of the world. However, if the number of said bad sectors increases - and it clearly does - you can't use that drive reliably and the problem will only get worse.
There's nothing you can do about it with software. It's a physical problem and you'll have to replace that disk and sooner than later, I'm afraid.

Ok! i do get it and it is my secondary pc with all files backed up. Out of curiosity, I would like to ask can softwares be corrupted located in a partition which didn't and still doesn't have even a single bad sector? I agree that where there are bad sectors, files are going to get corrupted if bad sectors are not remapped properly but how can an OS be corrupted when all bad sectors containig partitions are deleted? and there are none in other partitions?

---

### Post by Vladlenin5000 on 2015-07-10
Again, *Rarely if ever the growing number of bad sectors is confined only to a portion of the drive.*
A partition is a portion of the drive.

PS - Bad sector aren't deleted but marked as unusable.

---

