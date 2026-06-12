---
title: "Seeking advice &amp; confirmation for manual partitioning: UEFI, 14.04, no other OS"
date: 2016-08-02
forum: Installation &amp; Upgrades
---

### Post by giga+bytes on 2016-08-02
From other threads I have posted (thanks for the help, Mods!), and researching everywhere I can find pertinent information, this is what I currently have planned for my partitions for my new Ubuntu-only PC build (8GB RAM, Intel SSD):

/ = Root [primary, 25GB]
/home = Home1 [logical, #GB]
/home2 = Home2 (encrypted) [logical, #GB]
/? = whatever else is needed for UEFI install [logical, #GB]

I am not creating a swap partition because I will not be using any memory-heavy programs, and if I *do* need more memory I can easily add more. Plus, swap would need to be encrypted to keep anything done in the encrypted profile.. encrypted. So, no swap= no worries and less hassles.

I have 3 questions:
>Is there anything wrong with this partitioning list?
>What other partition(s) do I need for the UEFI requirement(s)?
>How do I encrypt the home2 partition? (I have little experience with partitioning, and have never tried to encrypt a partition. I am assuming it simply gives the option when creating the partition.)

---

### Post by Bucky Ball on 2016-08-02
> **giga+bytes said:**
> 
>What other partition(s) do I need for the UEFI requirement(s)?

An [EFI boot partition]("https://help.ubuntu.com/community/UEFI#Creating_an_EFI_System_Partition").

---

### Post by giga+bytes on 2016-08-02
Okay, I was not sure if that was needed. The Ubuntu auto-install on my other computer (you have been helping me with that thread, much appreciated!) made the boot partition like this: sda1 vfat 512m /boot/efi
Should I type the exact same thing, or should the partition type and/or size be changed? Oh, also, I am assuming that would be a logical partition, not a primary?

---

### Post by ubfan1 on 2016-08-02
Size and type is OK, but I think the EFI partition must be a primary on an MSDOS partitioned disk.

---

### Post by oldfred on 2016-08-03
With UEFI you use gpt partitioning not the 35 year old MBR(msdos) partitioning. There are no extended nor logical partitions with gpt.

If new drive, or else this will totally erase drive if already MBR. There are ways to convert MBR to gpt, also.
       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

I do not use encryption. There are two standard ones. 
Full drive LVM (LUKS)which encrypts everything but the ESP - efi system partition and the /boot partition. That is about the only time a separate /boot partition is normally used. 
And encryption of /home. That is not necessarily a separate partition. 
With either choice swap is also encrypted.

 Full disk encryption for two disk (ssd and hdd) setup ? 
[http://ubuntuforums.org/showthread.php?t=2312651](http://ubuntuforums.org/showthread.php?t=2312651)
[http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i](http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i)

This is my partitioning on a SSD & HDD, but no encryption.
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by giga+bytes on 2016-08-03
Okay, I have been following the "how to use manual partitioning during installation?", specifically the first section titled "if you have a blank disc" which shows options to select primary or logical partition types, so it must be for a Legacy/MBR install.

This is a new drive, so no risk of erasing anything. I will be encrypting one of the two /home partitions, not the whole drive.

From what Bucky Ball said (and linked, I went there and read it), and looking at Oldfred's "info on UEFI intall & repair" - "Partitioning", and the "DiscSpace" link below it, and what you just said in your post, I have revised my partitioning to this:

/boot/efi (300MB, FAT32)
/ (25GB, ext4)
/home1 (whatever size I want, ext4)
/home2 (encrypted, whatever size I want, ext4)

I am guessing this looks better, but is it precisely how it should look in the partitioning setup screen?

Also: I am seeing it mentioned more than once among the linked guides that the /boot/efi partition _does not_ need to be setup because the installer will do this automatically. *Does* the installer create this partition itself? And if so how do I choose the size of this partition, considering there are multiple recommendations for what size to make it (as you can see I followed Olfred's recommendation for a 300MB size)?

---

### Post by Bucky Ball on 2016-08-03
Just one thing, and apologies if you are aware of this. The two /home partitions you have are not the same variety of beast. When you create a /home partition during the Ubuntu install, it is more than just a data partition. 

Ubuntu identifies it as a /home partition and creates your user settings and default user folders like /Documents, /Videos, /Music, etc. in the /home partition instead of inside a default /home directory in /. This has advantages and disadvantages. 

Your /home2, on the other hand, is just how you are intending it (I think). A data partition which could be named anything. You could call it /frankfurt or /Data2. Doesn't matter. But if you change the name of the /home partition or don't have one, all settings and default user folders will be created in the /home directory inside /. ;)

---

### Post by oldfred on 2016-08-03
There are several install alternatives.
But only the auto install options create partitions.

With Something Else manual install option you can create partitions yourself or use partitions you create in advance with gparted. It is only the install of boot files to ESP that is automatic with UEFI installs  as is install to MBR with BIOS based installs.

Your second home is really just an encrypted data partition. 
With standard encrypted /home you have the encrypted files in an encrypted folder. And when system is running it shows files & folders, all as a standard unencrypted system.

Also with any encryption, you need to have a very good backup plan. Any corruption or issue is more difficult to recovery from or may not be repairable and backup is all you then have.

More than just flash drive:
[https://www.linux.com/learn/easily-encrypt-your-flash-drives-linux](https://www.linux.com/learn/easily-encrypt-your-flash-drives-linux)

---

### Post by giga+bytes on 2016-08-03
Hmm.. perhaps I should consider removing the encrypted home2 partition, and just keeping all information I was going to have there on external drives instead. I am having enough of a challenge installing and adjusting to Ubuntu and everything else Linux-based, so if encrypting a partition could cause additional problems (which I seem to be good at finding) it is best to avoid it for now. The main reason I was planning it that way is because an article I read made creating an encrypted second /home partition appear to be easy and ideal.

If I understand correctly, you are saying that I create the /boot/efi partition, then Ubuntu puts the boot files in that partition afterwards during the actual installation?

So with /home2 removed from the list, the rest is fine?

---

### Post by oldfred on 2016-08-03
Should be fine.

I do not partition entire drive when manually partitioning in advance. Then with the unused space and can potentially allocated to another install or more data or whatever.

This is my current use with SSD, HDD & one of my flash drives mounted. But I only have standard install with a fair number of additional apps. But not any games which can be large.

```
fred@Asusz97:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           793M  9.6M  784M   2% /run
/dev/sda6        24G  8.6G   15G  38% /
tmpfs           3.9G  384K  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1       500M   25M  475M   5% /boot/efi
/dev/sdb4       385G  101G  265G  28% /mnt/data
tmpfs           793M   56K  793M   1% /run/user/1000
/dev/sdc2        21G  4.5G   15G  24% /media/fred/yakkety
/dev/sdc3        36G   16G   19G  47% /media/fred/data64
/dev/sdb5        28G  4.3G   22G  17% /media/fred/backup
/dev/sdb6       6.7G  3.3G  3.1G  52% /media/fred/iso_hdd

```

---

### Post by giga+bytes on 2016-08-03
Okay, thanks!

I will be assembling my new PC shortly, then will see how setting everything up and installing Ubuntu goes, though I will "try Ubuntu" for a short while first, to see if there are any problems.

---

### Post by giga+bytes on 2016-08-03
One thing I have not seen much information about is how does "try Ubuntu" work? Is it try for a while and if no problems are found, restart the computer and install Ubuntu?

---

### Post by oldfred on 2016-08-03
You do not have to even restart. Once using the live installer, one of the icons is to install.
Best to use live version for a bit to make sure there are no major issues.

And you want to keep live installer as an emergency repair disk and if you update system to newer version later, update live installer also. ( I prefer new clean installs).

---

### Post by Bucky Ball on 2016-08-03
> **oldfred said:**
> ...keep live installer as an emergency repair disk ...

+1. Very handy as you need to have the / partition unmounted if you need to fix/resize it. You can't do that while Ubuntu is running off it so you boot the live session and unmount all partitions. Then you can do what you like. ;)

Good luck. Looks like you're set to go.

---

### Post by giga+bytes on 2016-08-04
Okay, thanks! Now I know what I am doing!

Just finished assembling the new PC, will start it up after supper. Here is hoping I have no problems with this one!

---

### Post by giga+bytes on 2016-08-13
I'm happy to report that everything went well and I've had no problems whatsoever with this new Ubuntu PC. I partitioned it exactly as recommended in this thread, leaving some space empty for future expansion. The only thing to mention is once I created the partitions, I got a message saying "the partition tables of the following devices are changed: SCSl1 (0,0,0) (sda)". Anyone know what that means?

---

### Post by Bucky Ball on 2016-08-13
Accurate report as the partition table has changed if you've repartitioned the drive so no worries there. In other words, don't worry about that message. :)

Good news, great job and could you please mark thread as solved to help others. See second link in my signature below. :)

If you have any issues don't hesitate to post a new thread. Enjoy!

---

