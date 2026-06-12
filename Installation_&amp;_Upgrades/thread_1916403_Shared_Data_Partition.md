---
title: "Shared Data Partition"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by ToshibaLaptoplinux on 2012-01-27
I am a long time Ubuntu user but have never run a dual boot box with Windows. Unfortunately I must do so on a new laptop just purchased and it has 4 partitions!!! Kind of wacky.

Anyway, my question is...

1) Can I run a dual boot machine on which Win 7 and Ubuntu can share a dedicated partition for data?

2) If so, can that partition be encrypted as well?

I may not want to do this because I hate the idea of Windows touching anything that my Linux does but may not have a choice.

Thanks.

---

### Post by LMHmedchem on 2012-01-28
I run a box that has windows XP and 4 flavors of linux on it. I have a shared data partition that I use for src code that I compile under the various OSs. The partition is formatted as NTFS and I am able to mount it from linux, create files, compile, etc.

The issues arise as to how the partition is mounted at boot time. Ubuntu seems to recognize it and mount it. It always appears under places. It can be a bit more complex with some of the other flavors, but with ubuntu it is easy. I would install win7 first, create and format the shared partition in windows, and then install ubuntu

There can be some issues with file permissions. I usually log in as root when I am going to compile something. There should be a way to assign group permissions and make both your linux and windows users members of the group. Hopefully someone can post about how to do that.

If you have never run dual boot, the best bet is to install windows first and then linux. When you install linux, install grub3 to the mbr of the drive ubuntu is on. After the install, boot into ubuntu and update the grub install, this will make sure that your windows is included in the grub options.

I'm not so sure about encryption, you would need an encryption package that is supported in both windows and linux so you could mount the partition from either side. There are some simpler encryption tools like bcrypt that you could run in linux and also with cygwin in windows. That would let you encrypt and decrypt files and archives. There very well may be some good encryption software with both linux and windows versions, you might look at truecrypt.

LMHmedchem

---

### Post by Megaptera on 2012-01-28
A useful guide here for a shared data in Windows/Ubuntu: [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by ToshibaLaptoplinux on 2012-02-02
Thanks for the replies. They were very helpful and after reading them and doing much research I decided on the following.

This is a 1TB HD with Win 7 installed on a 100GB partition and a remaining 809GB or 811GB depending on what I use to look at it on a second partition.

I thought I would partition the remaining 811GB for Ubuntu as follows:

/ 20 GB ext4; encrypted
/HOME 700GB ext4;encrypted
/Shared Data 75GB NTFS
Swap 16GB

I wasn't really sure where to place the data partition to be shared by Win7 and Linux. Does it matter? I also wasn't sure if there was an advantage to placing the swap first or last. Any ideas? Keep in mind that the first 100GB's has Win7 on it and I think there is a hidden recovery partition using 20GB's.

So I start my install and gparted runs and I run into a confusing snag. Even though Windows shows only 2 partitions, gparted shows that there are 4 partitions!!!
sda1 100MiB NTFS, sda2 101GiB NTFS, sda3 (extended) 809.65GiB,sda5 809.65GiB NTFS.

I am VERY confused and I have attached a photo in the hopes someone can help me. I am not sure which partition(s) I should be dealing with when installing Ubuntu? I can not destroy either the Win part or the recovery part.

[https://www.evernote.com/shard/s54/sh/fb3da1ac-df0e-4329-b37a-c1707e48cfeb/321f562378aee26d7fb955b169e55dcb]("https://www.evernote.com/shard/s54/sh/fb3da1ac-df0e-4329-b37a-c1707e48cfeb/321f562378aee26d7fb955b169e55dcb")

---

### Post by Bartender on 2012-02-02
I've got a suggestion, but you'd have to do some homework.

It's not uncommon for laptops (and PC's I guess) to come loaded up with four partitions.  I think the manufacturers do this to discourage people from messing with the partitions.

Our Acer 5920 came with 4 partitions.  First thing I did was make recovery discs.  Then I screwed things up trying to dual-boot.  Then I ran the recovery discs.  Afterward, there was one big ntfs partition instead of four partitions.  Installing Ubuntu was easy then.

I'd suggest going to this [forum]("http://forum.notebookreview.com/samsung/") or a similar one and asking about it.  See if you can talk to a few people who've reinstalled to the same or similar Samsungs as yours with the recovery discs and what the partitions looked like afterward.

After you make recovery discs, I'm pretty sure you can wipe out the recovery part.  But don't take my word on that!

---

### Post by WthIteh on 2012-02-02
I'm changing order of your text to make it easier to answer.
> **ToshibaLaptoplinux said:**
> I wasn't really sure where to place the data partition to be shared by Win7 and Linux. Does it matter?
No, if you format it as FAT or NTFS (formats which Windows is ware of them) both OSes can detect it.
> **ToshibaLaptoplinux said:**
> I also wasn't sure if there was an  advantage to placing the swap first or last. Any ideas? Keep in mind  that the first 100GB's has Win7 on it and I think there is a hidden  recovery partition using 20GB's.
Not sure, maybe another person could post about this. BTW, Windows filled both beginning of the hard disk and the end of it. So it should not make a lot of difference wherever else to place the swap partition.
> **ToshibaLaptoplinux said:**
> So I start my install and gparted runs and I run into a confusing snag.  Even though Windows shows only 2 partitions, gparted shows that there  are 4 partitions!!!
sda1 100MiB NTFS, sda2 101GiB NTFS, sda3 (extended) 809.65GiB,sda5 809.65GiB NTFS.

I am VERY confused and I have attached a photo in the hopes someone can  help me. I am not sure which partition(s) I should be dealing with when  installing Ubuntu? I can not destroy either the Win part or the recovery  part.
The first partition /dev/sda1 is for booting Windows. It's like /boot in Linux.
Second one /dev/sda2 is what known as C: in Windows (where Windows is installed itself).
Third one /dev/sda3 is an extended partition to hold more partitions (since only 4 non-logical partitions are allowed).
Fourth partition /dev/sda5 which is a logical partition placed inside /dev/sda3 is the partition which occupies about 800G and is known as D: in Windows.
Last partition /dev/sda4 which is about 20G is the recovery partition of Windows 7.
> **ToshibaLaptoplinux said:**
> This is a 1TB HD with Win 7 installed on a 100GB partition and a remaining 809GB or 811GB depending on what I use to look at it on a second partition.

I thought I would partition the remaining 811GB for Ubuntu as follows:

/ 20 GB ext4; encrypted
/HOME 700GB ext4;encrypted
/Shared Data 75GB NTFS
Swap 16GB

If you want to encrypt the root partition, you must also create a separate partition for /boot, because /boot must be unencrypted. Otherwise it could not decrypt the rest and boot the system up.

What you should do:

[LIST=1]
[*]Boot Windows and resize D: (/dev/sda5) as small as you want (e.g. 75GB). It will be that shared data partition which you want,
[*]Then boot live CD and continue with gparted,
[*]In gparted you will see empty space at end of /dev/sda3 (when you reduce size of /dev/sda5 remaining free space will be available for more new partitions at the end of /dev/sda3),
[*]Create an ext partition for /boot (200 MB is sufficient),
[*]Then create your /, /home, and swap partitions,
[*]For /dev/sda5, just select it and set its mount point (NOTE: do not mark it for formatting, since its D: drive),
[*]You can also set a mount point for /dev/sda2 if you want to access C: drive from Linux (Again do NOT mark it for formatting),
[*]Double check everything before applying and it should go OK ;)
[*]For encrypting home partition, installer has a checkbox but for encrypting root partition it takes some more steps (after completing above partitioning steps and before installing Ubuntu). Someone may post a step-by-step guide for it.
[/LIST]

---

### Post by oldfred on 2012-02-02
Make the recovery disks and also make a Windows repairCD. Only use Windows to shrink your Windows partiton but not to create partitions as it will convert to dynamic which does not work with Linux.


Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by ToshibaLaptoplinux on 2012-03-13
Thank you everyone for your help. There are parts of this that may be specific to my system, but maybe other parts will help others that have stupidly pre-partitioned drives by the manufacturer. So, after doing some research and based on the feedback on this thread, I did the following:

sda1 100.0 MiB ntfs Samsung quick boot partition
sda2 101.0 GiB ntfs Windows 7 OS (C:)
sda3 (Extended)
	sda5 50.0GiB ntfs ([Windows D:];[Linux /Windows_D])
	sda6 190MiB ext4 /boot
	sda7 19.07GiB ext4 /
	sda9 740.37GiB ext4 /Home  encrypyted
	16MB Swap



sda4 20.77GB ntfs Samsung Recovery Partition.


Didnt have to deal with the grub bootloader. It took care of everything in the install. 

There were a couple of blips and a few outstanding things I'd like to do such as encrypt root but for the moment am satisified...with the install. However there are a couple of problems one of which is MAJOR that I will outline below this post.

---

### Post by ToshibaLaptoplinux on 2012-03-13
So there is one HUGE problem I have encountered which resulted in my losing some pretty critical data. 

sda5 50.0GiB ntfs ([Windows D:];[Linux /Windows_D]) is what I am using to share data between Windows 7 and Ubuntu.

1) I can see the partition from both OS's
2) Data that I write to that directory from Windows can be seen and edited in Ubuntu.
3) If I write data to the ntfs partition from Ubuntu, it seems to move or copy successfully and I can work with the data, however...

If I reboot, either into Windows or Ubuntu, the data disappears!!! Poof! Up in smoke! Gone. Not happy.

I noticed it first with some critical data I transferred which is now lost and I have run multiple tests creating, copying, moving various kinds of documents to the partition and the behaviour is reproducible. Upon reboot into either OS the data is GONE.

What is going on and how do I troubleshoot this?

Is there any possibility of recovering data that went into that blackhole?

What information do I need to provide in submitting a bug report? It is pretty clear to me that it is a problem on the Ubuntu side.

:-x:-x:-x

---

### Post by coffeecat on 2012-03-13
> **ToshibaLaptoplinux said:**
> 
3) If I write data to the ntfs partition from Ubuntu, it seems to move or copy successfully and I can work with the data, however...

If I reboot, either into Windows or Ubuntu, the data disappears!!! Poof! Up in smoke! Gone. Not happy.

Are you writing to your NTFS partitions from Ubuntu while Windows is in hibernation? That is a sure way of losing data when you next start up Windows. Windows remembers the state of the filesystem and journal when it goes into hibernation and will restore it to that state when it is restarted.

---

### Post by ToshibaLaptoplinux on 2012-03-16
> **coffeecat said:**
> Are you writing to your NTFS partitions from Ubuntu while Windows is in hibernation? That is a sure way of losing data when you next start up Windows. Windows remembers the state of the filesystem and journal when it goes into hibernation and will restore it to that state when it is restarted.

Thanks for the information. That is good to know as I was unaware of that.

However, That is **not** the case in my sitaution. Windows is fully shutdown when I am working in Ubuntu.

Any other ideas? Clearly this problem totally defeats the purpose of having a shared partition in a dual boot box.

---

### Post by ToshibaLaptoplinux on 2012-03-16
Just noticed something else quirky.

When I look at "top" in my terminal it shows the following,


Mem:   8105132k total,  1961136k used,  6143996k free,   222352k buffer
Swap:    15356k total,        0k used,    15356k free,  1039764k cached

Because I assigned 16MB to swap, and because none of it is being used, I took a look in gparted again and saw the following":

sda1 100.0 MiB ntfs Samsung quick boot partition
sda2 101.0 GiB ntfs Windows 7 OS (C
sda3 (Extended)
---sda5 50.0GiB ntfs ([Windows D:];[Linux /Windows_D])
---sda6 190MiB ext4 /boot
---sda7 19.07GiB ext4 /
---sda9 740.37GiB ext4 /Home encrypyted

Unallocated 2MiB
sda8 15MiB Unknown
sda4 20.77GiB ntfs Samsung Recovery Partition

What is going on? Is swap allocated and recognized or not? How could this have happened and if it isn't recognized do I have to repartition from scratch because the unallocated sda8 precedes my encrypted HOME partition sda9? And why will it only let me expand the swap by 1MiB even though 2MiB are free preceeding it?

---

### Post by darkod on 2012-03-16
Are we talking about 16MB or 16GB for swap?

For 16MB you shouldn't have bothered.

Don't expect it to use every single MB space, especially when resizing and if Gparted is rounding to cylinders. There will be gaps of 1-2MB here and there. If we are talking about partitions of GBs, those few MBs don't matter.

On the other hand, if you really made swap 16MB, just forget about it, I would say it's useless.

---

### Post by dave2001 on 2012-03-16
I would not make a swap partition of less than a one GB on a new lappy. If you want to confirm how much swap you do, or do not have, type in terminal ```
free -m
``` and look under the total column for swap.

As far as your NTFS file sharing problem, I think something unusual is going on for you. I have been using Ubuntu with Windows 7 for years now, and an NTFS partition is where I store almost all my data. I've never had a problem with anything disappearing. 

When using multiple OS's I'm a fan of keeping things simple. Your partitions look unnecessarily complicated to me. I'd do ONE partition for Windows 7 OS. Neither OS actually needs a separate partition for the boot files. Also, I think "recovery" partitions are a waste of space, how often do you need a backup on the same drive? I'm not saying don't back up your OS, I just prefer to do it on an external drive.

I would make sure your NTFS partition is a primary partition. 

This is the setup I've been using all these years with no trouble.

sda1 (primary): Windows7 OS
sda2 (primary): NTFS shared personal data storage partition
sda3 (primary): Ubuntu OS and data files
Sda4 (primary): Swap

---

### Post by dave2001 on 2012-03-16
After looking again, the only other thing I can think of is that having an encrypted partition for /home is somehow influencing things in an unexpected way. I don't use encryption, so I know very little about how an OS goes about getting data in and out. Is it possible your Ubuntu OS is confused and thinks it also needs to write "encrypted" data to the NTFS partition, which of course Windows will not see correctly? Just a thought, I'm really guessing here. Since I've never had problems with NTFS file-sharing, I'm not sure where to look except at the differences between our systems, and the two major differences are encryption and partitions. 

Also, one other question, are ALL Ubuntu-saved files missing upon entering Windows, or is it only some formats? Perhaps the application handling the files could be at fault instead of the OS?

---

### Post by coffeecat on 2012-03-16
> **ToshibaLaptoplinux said:**
> 
Because I assigned 16MB to swap, and because none of it is being used, I took a look in gparted again and saw the following":

sda1 100.0 MiB ntfs Samsung quick boot partition
sda2 101.0 GiB ntfs Windows 7 OS (C
sda3 (Extended)
---sda5 50.0GiB ntfs ([Windows D:];[Linux /Windows_D])
---sda6 190MiB ext4 /boot
---sda7 19.07GiB ext4 /
---sda9 740.37GiB ext4 /Home encrypyted

Unallocated 2MiB
sda8 15MiB Unknown
sda4 20.77GiB ntfs Samsung Recovery Partition

What is going on? Is swap allocated and recognized or not?

When you install Ubuntu with an encrypted home partition, your swap partition is automatically encrypted as well. This appears as "unknown" in Gparted but is a usable, albeit encrypted, swap space for your system.

By the way, I agree with darkod. 15-16MB for swap is inadequate.

---

### Post by oldfred on 2012-03-16
Please do not start discussion of an issue and then start a new thread. We are all volunteers and need to see what others have contributed to correctly add to the discussion.

This thread should just be on the issues of creating a Shared Data Partition as per title. 
Then if OP is having issues using the Shared they should be in his new thread:

Losing data when writing to NTFS partition.
[http://ubuntuforums.org/showthread.php?t=1940122](http://ubuntuforums.org/showthread.php?t=1940122)

---

### Post by ToshibaLaptoplinux on 2012-03-23
> **oldfred said:**
> Please do not start discussion of an issue and then start a new thread. We are all volunteers and need to see what others have contributed to correctly add to the discussion.

This thread should just be on the issues of creating a Shared Data Partition as per title. 
Then if OP is having issues using the Shared they should be in his new thread:

Losing data when writing to NTFS partition.
[http://ubuntuforums.org/showthread.php?t=1940122](http://ubuntuforums.org/showthread.php?t=1940122)

Sorry about that. I thought it was just a natural progression of the thread and the subsequent problem was a direct result of the first problem thus related.

How do you suggest one start a new thread and keep the previous contributors in the loop?

---

### Post by Megaptera on 2012-03-23
> **ToshibaLaptoplinux said:**
>  How do you suggest one start a new thread and keep the previous contributors in the loop?

You could start a new thread and link back to this one & also link this one to the new one?

---

### Post by coffeecat on 2012-03-23
> **ToshibaLaptoplinux said:**
> Sorry about that. I thought it was just a natural progression of the thread and the subsequent problem was a direct result of the first problem thus related.

How do you suggest one start a new thread and keep the previous contributors in the loop?

@ToshibaLaptoplinux, you started two new threads a little over a week ago. This one about NTFS:

[http://ubuntuforums.org/showthread.php?t=1940122](http://ubuntuforums.org/showthread.php?t=1940122)

And this one about swap:

[http://ubuntuforums.org/showthread.php?t=1941673](http://ubuntuforums.org/showthread.php?t=1941673)

Both of these threads concern issues that you were also asking about in this thread at the same time. This is bad netiquette. Therefore I have closed this thread.

---

