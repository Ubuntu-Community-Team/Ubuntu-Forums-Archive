---
title: "No space on the disk"
date: 2016-06-07
forum: Installation &amp; Upgrades
---

### Post by carlostefano on 2016-06-07
Hello,

I have already installed with success both xubuntu and lubuntu. Now I wanted to try finally ubuntu but during the installation I got a problem. After that I have instert the city and the language, appears an error on the screen. There is written that I have no space on the disk. On the laptop I have an hard disk with 149 GB. I have tryed to format the partitions by myself with gparted. Anyway in the end it was useless becouse ubuntu have formatted them again. Also after this it says that I don't have free space on the disk.

How can I solve this problem?

Greetings,

carlostefano

---

### Post by Bashing-om on 2016-06-07
carlostefano; Hello;

That depends on 
a) the partitioning scheme that is employed. The older legacy, msdos, scheme has a 4 "primary" partition limit .
b) The firmware to declare to an Operating System how to control its platform-specific hardware. Is this firmware EFI ?

Boot the live medium that you are attempting to install with , to the "try ubuntu mode" .
As a means to discover what we are working with please provide - between code tags - the outputs of terminal commands:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```

We see here what is .. and get an idea of what we can do.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-06-07
If we have msdos/mbr partitioning and we choose Erase disk and install Ubuntu. Then the installer will create a primary partition for Ubuntu and a special primary partition called an Extended partition and in that partition the installer will create a logical partition for the swap partition. That is the basic partition layout with msdos/mbr partitioning and only Ubuntu or one of its flavours installed.

If we then try to install another flavour of Ubuntu we will get an option to install alongside the existing operating system. Then the installer will allow us to resize the existing primary partition to create a second primary partition for the new installation and use the same swap partition.

This method should allow us install at least one more Linux distribution. Unless we have some other OS already installed such as Windows XP and that is using the two remaining allocations of primary partitions.

In this case we need to resize the extended partition and in it create a suitably sized logical partition and then install using the Something Else option. Reformatting existing partitions is not the solution but resizing and creating new partitions and using the Something Else option is the way forward.

Apart from the partition layout we also need to know the install options you are choosing. You might be installing into a partition that is too small for Ubuntu.

Regards.

---

### Post by carlostefano on 2016-06-07
Now I am using ubuntu in the trial mode, without the installation, just like you suggested me. Already apperas the wearing : this computer has only 0 byte disk space remaining. If I go on "examine" then it shows me 100% used and under a lot of folders (rofs, user, cdrom, lib, and so on). The size of the folder "/" , marked with 100%, has only 10,2 GB.
I have tryed several methods for to install it, included the one to erase the disk and then install ubuntu. The result was the same. The only one that I didn't try is to install the OS at the side of the existing one. Anyway in the last tentative with gparted I have also resized the partitions. When I have tryed to install, ubuntu told me there wasn't any other operative system installed. After it has created new partitions and told me again that there was no space in the disk :(.

---

### Post by carlostefano on 2016-06-07
[https://drive.google.com/file/d/0B7CK1BYafsmDT0dfZE9VOV8yWEk/view?usp=sharing](https://drive.google.com/file/d/0B7CK1BYafsmDT0dfZE9VOV8yWEk/view?usp=sharing)

[https://drive.google.com/file/d/0B7CK1BYafsmDb0NtMkxqZUl6T0U/view?usp=sharing](https://drive.google.com/file/d/0B7CK1BYafsmDb0NtMkxqZUl6T0U/view?usp=sharing)

[https://drive.google.com/file/d/0B7CK1BYafsmDTUp5VndnMWZ4Wmc/view?usp=sharing](https://drive.google.com/file/d/0B7CK1BYafsmDTUp5VndnMWZ4Wmc/view?usp=sharing)

---

### Post by Bashing-om on 2016-06-07
carlostefano; Hey ..


We are talking a desktop install, right ?

OK, what I see is that on the hard drive the present Operating system is using 159 Gigs of space with that 1st partition. There is no other room in this situation to install another system. 1 Gig for the "extended" partition and all the space in the extended partition taken up with the swap partition. ToTal drive space is 160 Gigs.

I see 2 options .
1) shrink that sda1 partition by the amount to allow for the install of the 2nd system ; and have a common swap partition .
2) Choose the install option " install alongside " .. I would expect the install wizard to take care of the details of disk space allocation for each system to use . If you are happy with the default . That is the simpler thing to do .

Else. well ...... if you have nothing on the present system you care to save .. and only want one operating system .. then I would expect the install option " erase disk and install ubuntu " to do just that .

Tell us what you want to do, given these options.

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by carlostefano on 2016-06-07
I can't use the option to install at the side of the other operative system becouse now there isn't anyone else installed.
I explain you, in my pc now there are:
dev/sda -> fat 32 cdrom (is the usb pen) + not allocated for 3.94 GB
dev/sdb -> 149 GB ext4

The problem of spaces are related the first one. Is like is trying to install the OS there or anyway it says that there isn't enough space on the first one.

---

### Post by Bashing-om on 2016-06-07
carlostefano; Huh ?

If it is that you are attempting to "install" , rather than make up a install medium , ubuntu onto that pen drive that is 3.7 Gigs of usable space. then the advisory is correct .
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)
> 
5 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)


The terminal command :
```

sudo fdisk -lu

```
to identify the target .
The 1st device that bios passes to the operating system will be known as sda to the operating system .

Maybe, we need to clarify what is your goal here exactly .. install ubuntu where ? And also is this install to be a dual boot or single _installed_ system ?

[INDENT][INDENT]when we know better
[INDENT][INDENT][INDENT]we do better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by carlostefano on 2016-06-07
> **Bashing-om said:**
> carlostefano; Huh ?

If it is that you are attempting to "install" , rather than make up a install medium , ubuntu onto that pen drive that is 3.7 Gigs of usable space. then the advisory is correct .
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)


The terminal command :
```

sudo fdisk -lu

```
to identify the target .
The 1st device that bios passes to the operating system will be known as sda to the operating system .

Maybe, we need to clarify what is your goal here exactly .. install ubuntu where ? And also is this install to be a dual boot or single _installed_ system ?[INDENT][INDENT]when we know better[INDENT][INDENT][INDENT]we do better
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



Obviously my goal is to install the OS on the internal HD. There isn't any other operative system on the HD, so it should be the only one to run. When ubuntu adware me of the problem with the disk space, I have clicked on the option to examine the disk. I think all the folders that it showed to me, and that are the ones I have mentioned above in another of my posts, are all located on the usb pen.
In the bios I have put the usb pen like the first one that should be booted, is it right?

---

### Post by ubfan1 on 2016-06-07
Yes, putting the USB as the first boot option is good.  There has been some confusion above about sda and sdb when referring to the hard disk.  USUALLY, even when you put the USB first in the boot order, the hard disk is enumerated as "sda", and the USB as "sdb", but not in every case, like yours, where the harddisk is sdb.  The size gives you the clue here.  So, any attempt to install to sda, which is the USB in your case, will fail.  Try using sdb, and with a "use whole disk" selection, you should get pretty much the partition layout you have shown.

---

### Post by carlostefano on 2016-06-07
I have got it!!! I have installed it!! :D :D And guess what, I also love it ))). I understand now why people like ubuntu so much ). 

Ok, I explain what I did for to solve the problem.

- I have formatted the usb key and put again all the files with UNetbootin

-  I have tryed [COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -lu . I had the partition sda with 149 GB type linux and a sdb with 3,7 GB type fat32 . Maybe before I have inverted the letters, I am very sorry.

- I have chosen as way to install it, the option "other", "is possible to create new partitions..." [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] In general I have followed this guide: [/FONT][/COLOR]http://www.windoctor.it/sistemi/linux/come-formattare-e-installare-ubuntu/[COLOR=#000000][FONT=Ubuntu Mono]

-  I have chosen to install ubuntu on the sda1 ext4. I gave it "/" as point of mount. This is the partition chosen for the installation of the bootloader. I have put also the option to format this partition.

- I have created also another partition swap with 4 gb more than the big ext4 sd1 I already had

- I have also chosen another option for the language, still my language but just another one of the options listed. I wanted to be sure that it wasn't one of the cause of the problems.

Then the installation went absolutely ok and now I have my new ubuntu mate working perfectly :D

Thanks to everyone for your support! :)


[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-06-08
carlostefano: Outstanding !

Pleased you got it figured put .. and all working.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

