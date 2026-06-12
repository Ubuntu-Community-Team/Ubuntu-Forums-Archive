---
title: "Deleting Partitions"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by anon_private on 2013-01-09
Hi,

Semeone has given me a number of Ubuntu OS's to try.

I would like to test and install each in turn to the hard-drive, then delete the partition to restore the machine to its original configuration, then install the second, and so on. After the tests, I can install the OS of choice

Should I be able to do this without a problem?

On a related point, When installing to the hard-drive sometimes I am presented with two boxes and can adjust the size of the partitions.

Assuming that Vista is on the machine, is the box to the left the vista partition, and the box to the right the partition that will be used for the new OS?

Thanks

---

### Post by The Cog on 2013-01-09
Strictly speaking, deleting the partition will not restore the drive to its original condition, because installing an OS also involves writing a boot sector to the start of the drive (in the Master Boot Record area, outside of any partitions). Just deleting the Ubuntu partition will leave the machine unable to boot at all because the bootloader that Ubuntu installs will not be able to find Ubuntu any more. This doesn't matter if you are going to install another Ubuntu straight afterwards (which will also install an updated bootloader) but it will matter if you want to run Vista again.

There are lots of tutorials on the internet about how to restore a windows bootloader. I can't vouch for any as I've never wanted to restore windows after a linux install, but I have used systemrescuecd to replace a damaged windows bootloader for someone in the past.

P.S.
Backup all your important data before you even start. If something goes wrong, like a badly burned installer CD, then you could lose all your drive contents.

---

### Post by Bucky Ball on 2013-01-09
*Thread moved to **Installation & Upgrades***

Why don't you just try them all from the LiveCD. You don't need to install them to the hard drive at all ...

---

### Post by ibjsb4 on 2013-01-09
Forget partitioning  :)

[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by darkod on 2013-01-09
On top of the other things already mentioned, if you want to test linux OSs you don't need to delete the previous partition at all. Most linux installers offer some type of manual method of installation where you can select to use an existing partition. So, no need for the partition to be deleted just so it can be created again.

In the ubuntu installer for example, this method/option is called Something Else.

---

### Post by Rebelli0us on 2013-01-09
What you're proposing **can** be done, but it seems like a lot of work and you risk damaging your Windows installation. 

Instead, you can use VirtualBox (free form Oracle) to create virtual machines of each of the Linux versions you want to try out, it's much quicker, simpler and cannot damage your Host OS.

---

### Post by offgridguy on 2013-01-09
> **The Cog said:**
> Strictly speaking, deleting the partition will not restore the drive to its original condition, because installing an OS also involves writing a boot sector to the start of the drive (in the Master Boot Record area, outside of any partitions). Just deleting the Ubuntu partition will leave the machine unable to boot at all because the bootloader that Ubuntu installs will not be able to find Ubuntu any more. This doesn't matter if you are going to install another Ubuntu straight afterwards (which will also install an updated bootloader) but it will matter if you want to run Vista again.

There are lots of tutorials on the internet about how to restore a windows bootloader. I can't vouch for any as I've never wanted to restore windows after a linux install, but I have used systemrescuecd to replace a damaged windows bootloader for someone in the past.

P.S.
Backup all your important data before you even start. If something goes wrong, like a badly burned installer CD, then you could lose all your drive contents.
Good explanation. +1

---

### Post by anon_private on 2013-01-09
> **darkod said:**
> On top of the other things already mentioned, if you want to test linux OSs you don't need to delete the previous partition at all. Most linux installers offer some type of manual method of installation where you can select to use an existing partition. So, no need for the partition to be deleted just so it can be created again.

In the ubuntu installer for example, this method/option is called Something Else.

Thanks for responding.

Have I understood you correcly.

I should create a partition using GParted. The total size could be say 30 Gib (15 Root, 10 Home, 2 Swap).

I should then install into this partition.

If I wanted to use another OS, I would simply install into this partition and the existing Linux would be overwritten - without affecting Vista.

Suppose I wanted to remove the OS (Linux) and restore my machine to its original configuration - Vista.

Would using this method protect the Vista boot loader.

I'll also have a look at the other suggestions

> **ibjsb4 said:**
> Forget partitioning  :)

[https://www.virtualbox.org/](https://www.virtualbox.org/)


Hi,

I might have some difficulty in using Virtualbox

Although I have Vista installed it will not run due to insufficient memory, hence I need to install an OS that will run before I could consider using Virtualbox.

Having no experience with Virtualbox, my previous comments are guesswork.

---

### Post by darkod on 2013-01-10
> **anon_private said:**
> Thanks for responding.

Have I understood you correcly.

I should create a partition using GParted. The total size could be say 30 Gib (15 Root, 10 Home, 2 Swap).

I should then install into this partition.

If I wanted to use another OS, I would simply install into this partition and the existing Linux would be overwritten - without affecting Vista.

Suppose I wanted to remove the OS (Linux) and restore my machine to its original configuration - Vista.

Would using this method protect the Vista boot loader.

I'll also have a look at the other suggestions

Not exactly. The root, /home and swap are all different partitions, so you can't call it ONE partition. It's three.
But yes, if you later install another linux version using these same partitions, it will not affect Vista in any way, or any other partition on the disk.
You can create the partitions in advance with Gparted, but it's not needed since you can do it with the installer. In any case, you should have the 30GB unallocated space (not belonging to any partition) before you start. And not have reached the limit of 4 primary partitions.

From ubuntu live mode, can you open terminal and post the output of this command:
```
sudo parted -l (that's small L)
```

That will show us the existing disk layout.

If you install the grub2 bootloader to the MBR (which I recommend) it will overwrite the windows bootloader, but it's easy to restore it back even if you don't have a vista dvd. Making ubuntu boot with the windows bootloader is more complicated especially if your vista is not working good right now because of low resources.

---

### Post by anon_private on 2013-01-10
> **darkod said:**
> Not exactly. The root, /home and swap are all different partitions, so you can't call it ONE partition. It's three.
But yes, if you later install another linux version using these same partitions, it will not affect Vista in any way, or any other partition on the disk.
You can create the partitions in advance with Gparted, but it's not needed since you can do it with the installer. In any case, you should have the 30GB unallocated space (not belonging to any partition) before you start. And not have reached the limit of 4 primary partitions.

From ubuntu live mode, can you open terminal and post the output of this command:
```
sudo parted -l (that's small L)
```

That will show us the existing disk layout.

If you install the grub2 bootloader to the MBR (which I recommend) it will overwrite the windows bootloader, but it's easy to restore it back even if you don't have a vista dvd. Making ubuntu boot with the windows bootloader is more complicated especially if your vista is not working good right now because of low resources.



Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  57.6MB  57.5MB  primary  fat16        diag
 2      57.7MB  10.8GB  10.7GB  primary  ntfs
 3      10.8GB  250GB   239GB   primary  ntfs         boot


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  4010MB  4006MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label



Vista is not working at all at the moment, but I still want to keep it. Sometime in the future I may be able use it.

I am a little worried about overwriting to Vista bootloader.

I will let the 'something else' create the partitions.

If I wanted to delete Lubuntu for some reason, would this be straightforward and not affect Vista.

I am trying to keep all my options open.

Best wishes.

A

Ps. Thanks for advising

PPS. If I wanted to post the GParted information. Is this the correct command.
sudo gparted.

I thought that I should check this before typing in case it wipes

---

### Post by darkod on 2013-01-10
Well, you can't worry about every little thing in this world, right? :)

In reality, the windows bootloader on the MBR is not even a bootloader. It's only a small piece of code that continues the boot process where the boot flag is. That's why it's easy to reproduce it even with linux tools.

The thing is that grub2 is not designed to work on a partition, and that's where you have to install it if you don't install it on the MBR. If vista doesn't even work, I think you are giving too much thought to the windows bootloader. Simply use grub2 and you can restore the windows bootloader when you want to.

If you do install ubuntu/lubuntu, note that you can't simply delete the ubuntu partition in future. It's better to restore the windows bootloader first, test that vista is booting, and only then delete the linux partitions on your disk.

But all of that is not very important or urgent, we are talking about IF and WHEN you want to remove ubuntu.

More important is the fact that your hdd doesn't have unallocated space on it. Almost all hdd belongs to the vista partition. You need to shrink it so that unallocated space is created.
But shrinking vista is best to be done by windows Disk Management. If you can't boot vista, you can't do that.
How did you plan to create the unallocated space for ubuntu?

If vista is not working, personally I would back up all personal data from it, and reinstall it on a smaller partition, so that it leaves space for ubuntu on the end of the disk. That will have two benefits:
1. Ubuntu will have space to install without shrinking any partition.
2. You will also get a working vista installation.

In this situation it's pointless to keep vista and on top of that you are getting so worried about it and its bootloader.

---

### Post by anon_private on 2013-01-10
> **darkod said:**
> Well, you can't worry about every little thing in this world, right? :)

In reality, the windows bootloader on the MBR is not even a bootloader. It's only a small piece of code that continues the boot process where the boot flag is. That's why it's easy to reproduce it even with linux tools.

The thing is that grub2 is not designed to work on a partition, and that's where you have to install it if you don't install it on the MBR. If vista doesn't even work, I think you are giving too much thought to the windows bootloader. Simply use grub2 and you can restore the windows bootloader when you want to.

If you do install ubuntu/lubuntu, note that you can't simply delete the ubuntu partition in future. It's better to restore the windows bootloader first, test that vista is booting, and only then delete the linux partitions on your disk.

But all of that is not very important or urgent, we are talking about IF and WHEN you want to remove ubuntu.

More important is the fact that your hdd doesn't have unallocated space on it. Almost all hdd belongs to the vista partition. You need to shrink it so that unallocated space is created.
But shrinking vista is best to be done by windows Disk Management. If you can't boot vista, you can't do that.
How did you plan to create the unallocated space for ubuntu?

If vista is not working, personally I would back up all personal data from it, and reinstall it on a smaller partition, so that it leaves space for ubuntu on the end of the disk. That will have two benefits:
1. Ubuntu will have space to install without shrinking any partition.
2. You will also get a working vista installation.

In this situation it's pointless to keep vista and on top of that you are getting so worried about it and its bootloader.

Gparted says that there is unallocated space (1.58 MiB).

If you confirm the command, I will post the information.

sudo gparted - yes/no.

If I can't use the install facility as it is in Lubuntu, I'll leave things as they are, or re-consider installing Lubuntu alongside Vista

Thanks

---

### Post by oldfred on 2013-01-10
If a graphical app you should use graphical sudo from command line or gksu or gksudo.

gksudo gparted

       Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

    
       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by darkod on 2013-01-10
Yeah, sudo gparted is safe. That's how you can start it from the terminal but it doesn't do anything until you tell it to, it only starts the program.
In fact, since Gparted is graphical program, if you want to start it from terminal it's better with:
gksu gparted

For graphical programs you use gksu in place of sudo.

It might show unallocated space of 1.5MiB between partitions but have you thought what can you do with 1.5MiB?

A larger word document is larger than that. You need many more GBs for the OS, not MBs.

---

### Post by anon_private on 2013-01-10
> **darkod said:**
> Yeah, sudo gparted is safe. That's how you can start it from the terminal but it doesn't do anything until you tell it to, it only starts the program.
In fact, since Gparted is graphical program, if you want to start it from terminal it's better with:
gksu gparted

For graphical programs you use gksu in place of sudo.

It might show unallocated space of 1.5MiB between partitions but have you thought what can you do with 1.5MiB?

A larger word document is larger than that. You need many more GBs for the OS, not MBs.


Hi,

Yes, you are right. It is not much space.

I am looking for an easy and safe way of forming the partitions.

There may not be one. If that is the case, I'll consider either using the live Lubuntu pendrive (as I am at present), or installing alongside Vista.

Best wishes.

A

---

### Post by darkod on 2013-01-11
But installing along vista means that ubuntu will be installed on linux partitions next to the existing vista partition. That still means there will need to be unallocated (unpartitioned) space on the hdd where the linux partitions will be placed.

If there is no such space, the installer can shrink the vista partition, but as i mentioned windows doesn't like linux tools to shrink its system partition. It's best to do it from within vista. But you say you can't boot it, so you can't do that either.

The choice is yours. I still say better to get your data out, reinstall a working vista, then shrink it or not depending how you installed it (whether on the whole hdd or leaving unallocated space for ubuntu), and then install ubuntu.

---

### Post by Bucky Ball on 2013-01-11
Make free space, create an extended partition, stick whatever you want on logical partitions in that. Just remember, four primary partitions is the limit. So, three primarys with an extended and as many logical partitions as you like inside that is the way to go (Win usually wants two or three primary partitions anyhow). 

You don't need much more than 10 - 15Gb partitions to install Ubuntu and if you are just trying it out and not stacking data in there, probably less.

---

### Post by anon_private on 2013-01-11
> **Bucky Ball said:**
> Make free space, create an extended partition, stick whatever you want on logical partitions in that. Just remember, four primary partitions is the limit. So, three primarys with an extended and as many logical partitions as you like inside that is the way to go (Win usually wants two or three primary partitions anyhow). 

You don't need much more than 10 - 15Gb partitions to install Ubuntu and if you are just trying it out and not stacking data in there, probably less.


Thank you for responding.

I do not understand the concept of extended partitions.

Best wishes.

A

> **darkod said:**
> But installing along vista means that ubuntu will be installed on linux partitions next to the existing vista partition. That still means there will need to be unallocated (unpartitioned) space on the hdd where the linux partitions will be placed.

If there is no such space, the installer can shrink the vista partition, but as i mentioned windows doesn't like linux tools to shrink its system partition. It's best to do it from within vista. But you say you can't boot it, so you can't do that either.

The choice is yours. I still say better to get your data out, reinstall a working vista, then shrink it or not depending how you installed it (whether on the whole hdd or leaving unallocated space for ubuntu), and then install ubuntu.

Thank you for replying.

As a matter of interest, If I decided to make a persistent Lubuntu LiveCD would it be better to use Unetbootin to simply create the USB, or make a partition for Lubuntu and then use Unetbootin?. In the case of the latter, how could I ensure that Unetbootin installs the files into the correct partition.

The USB will also contain a personal folder containg files.

---

### Post by darkod on 2013-01-12
For persistant usb you simply create it with unetbootin and specify the size allocated to the persistant file. You don't create partitions on the hdd.

---

### Post by anon_private on 2013-01-12
> **darkod said:**
> For persistant usb you simply create it with unetbootin and specify the size allocated to the persistant file. You don't create partitions on the hdd.

I have never made a persistent USB, is there an advised size for the persistent file?

Can I view the USB using GParted?

I considered partitions because I thought that working with the USB would give me some experience of working with partitions without risk.

Am I right in assuming that if I decided to replace Vista with Lubuntu and the system crashed at some stage, then I could lose all my data?

Thanks

---

### Post by darkod on 2013-01-12
I have never used persistant usb either. I guess you need at least 2GB usb stick, the ubuntu image is about 750MB so you will have more than 1GB for the persistant file. That should be more than plenty. Even on bigger usb sticks you can decide to make the file 1GB or similar.

Yes, you can view any usb stick and all partitions on it using Gparted.

As for replacing vista and losing data if lubuntu crashes, first of all if you literary replace vista with lubuntu, you need to copy the data first because the vista partition will be overwritten with linux ext4 partition. All data is erased in the process. So you need to use the lubuntu live mode for example and copy any data BEFORE you do anything else.
Concerning losing data if lubuntu crashes, depends what type of crash we are talking about. If the OS gets corrupted and you can't fix it you can still use live mode, copy the data you need, and do a new clean install. You never lose all the data at once unless the hdd dies or something, and in that case you lose all data regardless which OS you had installed. Linux actually works much better than windows, and it less likely to crash in any way. Your current vista is crashed, right?

---

