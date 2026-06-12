---
title: "install ubuntu12.10 selecting &quot;do something else&quot; a complete chaos"
date: 2013-04-05
forum: Installation &amp; Upgrades
---

### Post by dvks on 2013-04-05
I install Ubuntu 12.10 on a 1 TB drive /dev/sda as the only operating system, no raid or LVM, simple partitions.

My goal is to have the /dev/sda1 mounted on "/", /dev/sda2 mounted on "/home", /dev/sda3 not used at installation time and will be formatted later & mounted as needed for backup purposes
and /dev/sda4 as swap. 

Sound simple, I started the installation, and at the prompt for the partitioning I clicked "do something else". 
I create a new partition table.
Defined /dev/sda1 as ext4 over "/". 
Defined /dev/sda2 as ext4 over "/home".
Now comes the cause for the problems- I defined /dev/sda3 as "Not Used" which is one of the available options on the partition type. 
Last defined the /dev/sda4 as swap.
When the system continues it shows a message that it can't proceed since partition 3 is busy and need to reboot, some other times it says that it can't define the partition, and some times it manages to finish the installation, I have no idea why there are few different scenarios my guess is that although I request to create a new partition table is actually didn't clean the older information and some flags remain there for the new attempt which looks like a bug by itself.
If and when I manage to complete the installation, I can't create a file system on the /dev/sda3 and get a message that the partition is busy although it does not show on /etc/fstab or /etc/mtab or /proc/mounts or when I do- sudo udisks --dump , also the mounting folder is a new one and no one is using it.

I tried to smart Ubuntu and defined the "/", "/home" and swap, leaving unused space after swap so I can partition it later using a script with "parted", but when I tried partition with parted I got an error that I am trying to create a partition outside of the device space which is completely incorrect ! 

Is there any expert that can put some order in this story, what is wrong with what I am trying to do or with how I do it?

---

### Post by darkod on 2013-04-05
I would use parted in terminal from live mode before you start, but you should also be able to do this with the installer. Instead of Not Used, see if there is an option like RAW, without filesystem. I'm not sure if Not Used actually creates the partition correctly. Honestly I have never looked into these options when installing.

If you want to try parted in terminal in live mode, note that live mode can mount existing swap partition to spped up working, so you need to turn swap off first. Also don't forget to leave 1MiB unallocated at front, the first partition should start at 1MiB.

parted creates unformatted partitions anyway, so that fits perfectly into your plan not to use sda3 right away.

It would be something like:
```
sudo swapoff -a
sudo parted /dev/sda
mklabel msdos #(new msdos table)
unit MiB #(change unit to MiB and calculate each partition size you want, where 1GiB = 1024MiB)
mkpart primary X Y #(create primary partition starting at X MiB ending at Y MiB, create all partitions you want)
quit #(quit the parted prompt after creating all partitions)
```

During the installer with existing partitions you will have to select each one by one, click the Change button below and tell it how you want to use it, filesystem, mount point, etc.

---

### Post by dvks on 2013-04-05
darkod, thanks for your feedback.
Since I don't consider myself as expert, let me first verify, you are suggesting that I first run Ubuntu from the installation usb stick, setup from there the partitions on my destination drive and then start installation and do what? select "do something else" , do not create a new partition table and go into each of the defined partitions and confirm it? I believe I will get to the same issue, what should I select to do with the partition that is actually not mounted, this is the problem to start with.
I guess I am missing something or didn't understand your feedback.
Apprecviate your further help
Thanks

---

### Post by darkod on 2013-04-05
Correct.

You select nothing for sda3. It will be created simply as a partition not holding a filesystem by parted. Like an empty container which is there, it exists, waiting for you to format it later when ever you choose to. If you create the partition like this in parted in advance, during the installation you don't even touch sda3, just leave it there. Nothing at all, no clicking on it, nothing.

Select sda1, Change button, Use As ext4, mount point /
Select sda2, Change, Use As ext4, mount point /home
Select sda4, Change, Use As swap area (swap doesn't use mount point, the field will be greyed out)

Bootloader destination: /dev/sda (wihout any number in it)

That's it.

---

### Post by dvks on 2013-04-05
Yes, I tried to do it already, I had two results, either the installation continues, finish ok.
Later when I boot the system and try to create a file system on the /dev/sda3 I get error that the device is busy.
As mentioned on my initial post I checked everywhere and the partition is not used or even mentioned on mtab, fstab and mounts.
On other attempts it just stops the installation process up-front declaring device is busy.

---

### Post by darkod on 2013-04-05
Not exactly, the way I understood it, you only tried creating partitions in the installer but not using one of them. I am wondering if only creating it still makes it busy, so it confuses the installer.

If you create partition in parted in live mode first, reboot and then start the installer, I don't see a way how the partition will be busy.

As for creating a file system later and the error you got, that shouldn't have happened. Maybe you made some mistake during creating it or formatting it.

There is another option. Start again the installer directly (without going into live mode), make new msdos table, create only three partitions, not four. When creating swap it will ask you if you want it at the beginning or end of the unallocated space. Select end and it will put it at the end of the disk.

That way instead of sda3 there will be unallocated space that you can use later. Continuing the installation in this case should go fine.

Unless all of this is because of another issue with the disk and it's not really related to the partition, but it only looks like that.

---

### Post by dvks on 2013-04-05
I found now an intermediate/alternate solution:
During installation I created only the /dev/sda1 for "/" , /dev/sda2 for "/home" and /dev/sda3 for swap I intentionally left at the end of the drive unused space without any partition on it.
the installation went on with no problems.
When the new system boot and logged in I create the partition over the empty drive space and it looks ok at this point, need more testing.

---

### Post by dvks on 2013-04-05
darkod

It seems we came to similar conclusions, thank for your support, regarding the creation of the file system, I also think I had some mistake there, maybe I gave size in bytes instead of MB, anyway I have a good solution and hope the setting during installation will be fixed in the future.
Thanks again for your time.

---

