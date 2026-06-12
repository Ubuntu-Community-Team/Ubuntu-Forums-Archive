---
title: "Partition Problem"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by PartitionTable on 2012-10-11
Hi guys,

So I'm trying to install Ubuntu on my Zenbook UX32A, and I'm having a little problem with partitioning.

I've got two devices;
**[COLOR=SeaGreen][COLOR=Black]sda[/COLOR][/COLOR]** - 320GB HDD
**sdb** - 30GB SSD

Now, I'm not trying to dual-boot (I was originally dual booting windows and Ubuntu, but now I'm migrating to solely Ubuntu), so I've completely formatted all the drives.

I've put "**/**" and the "**efi**" boot partition on **sdb** (the SSD).
On **sda **(the HDD), I put "/**home**" and another partition called "**/data**" - roughly splitting the 320GB into half amongst each.

After installing, I opened up "Home Folder" and I couldn't see "**/data**" in the Device list (I'm assuming partitions are treated as separate devices).
So I opened up the terminal and ran "**sudo fdisk -l**" and I'm getting the following error for everything on **sda**:

"*WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GTP. Use GNU Parted.*"

Is this why I can't see the "**/data**" partition?

How can I change the partition table to something else? During installation, I click "create new partition table", but I don't get the option to select anything, it just says it was done successfully.

[COLOR=Red]I found a "**/data**" in the folder _above_ "**/home**" and it looks to be the same size I made the partition, but it's owned by root, not my account. Is this the partition I made, and if so, how come I don't have control over it?[/COLOR]

Thanks so much for the help, I'm terribly new at this.
Cheers.

---

### Post by darkod on 2012-10-11
Unless I am wrong, there is nothing wrong with your system. There is only slight confusion.

1. If you used EFI and dual booted, your disks have gpt table since win7 can work only on gpt with efi. That message from fdisk is normal, since it really does NOT support gpt well. fdisk gives that message on any gpt disk.

2. The /data mount point will NOT be seen on the left side in the Nautilus file browser. The /data is part of the filesystem and as such is included in it. Nautilus shows on the left side usually partitions existing on disks in the system but which are not mounted or used by ubuntu. /data is mounted and used, hance it's not there.

One exception from this is the /media mount point and any subfolders. They DO show in Nautilus. So, if you make the mount point /media/data it should be there.

In any case, you can simply make a shortcut on your dekstop to /data and can reach it with one click.

In terminal you can always use it as /data. In Nautilus you can find it if you open Filesystem (that opens the root of the root partition) and the folder data should be there.

I think the root ownership is also normal since it's part of the system, but if you try to copy something there with your user it should let you.

---

### Post by PartitionTable on 2012-10-11
Alright, that clears some things up.

How would I go about changing the partition table anyway? 
(As I write, I'm about to boot into a live USB and try and do it somehow while I'm not accessing the system directly).

As for the /data folder, I can't seem to do anything with it. Same holds true for the /media folder. I can't right click and create anything inside, nor drag anything to them. My user account is an administrator.

Thanks again,
P.

---

### Post by darkod on 2012-10-11
You can do it in GUI with Gparted, but I prefer parted in the terminal. It will also tell you the current table type.

Open terminal and execute:
sudo parted -l (small L)

Before it lists the partition, in the general disk info you have the size, model, and the partition table type.

Writing new table is also easy with parted, of course you will lose all data on the disk, you must know that. :)

To enter the parted prompt for a specific disk:
sudo parted /dev/sdX

At the prompt, to write new msdos or gpt table:
mklabel msdos, or
mklabel gpt

You can also create partitions if you want to, or use Gparted later if you are used to GUI more. To exit the prompt:
exit

That's it.

Note that with parted most changes are done IMMEDIATELY, so be careful what you do. It's not like in Gparted where you can do anything, and until you click the green button nothing gets executed.

Depending how you made the /data folder, it might actually be owned by root and not letting other users write to it. I have created new mount points like /data1 and /data2 during installation and they are writeable without any further intervention.

---

### Post by PartitionTable on 2012-10-11
Brilliant, cheers!

I was still having problems with permissions though, thankfully I'm rather late to the party, and it's been [solved before]("http://ubuntuforums.org/ubuntuforums.org/showpost.php?p=10312284&postcount=7").
I'm now up and running pretty much exactly how I wanted.

Thanks again.

---

