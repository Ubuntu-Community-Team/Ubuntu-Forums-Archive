---
title: "Best config and general questions for three drives, multibooting"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by 9littlebees on 2012-11-19
Hi all,

So I had a nice dual boot working with Win7 and Xubuntu.  Then, in response to some good partitioning advice on a different thread ([link]("http://ubuntuforums.org/showthread.php?t=2085542")), I decided to mess about with some of my partitions.  Guess what?  I wiped my D: (user)  drive in Windows!

So I have decided to do a complete wipe of my system (after backing everything up in two places!!) and do a fresh install of both Win7 and Xubuntu.

Here's my thoughts on the partitioning config.  I would love some feedback on what I am proposing, especially if there are any potential minefields I am creating!

**System:**
CPU: Intel Core i5 2500k (3.3GHz)
RAM: 16GB
Graphics: Radeon HD 6870

**sda (120GB SSD):**
sda1: 100MB NTFS Windows System Recovery
sda2: 80GB NTFS Win7

**sdb (500GB HDD):**
sdb1: 500MB ext4 /boot
sdb2: 18GB swapfile (to allow Linux hibernating)
sdb3: 100GB ext4 /root (Xubuntu 12.10)
sdb4: 350GB unallocated

**sdc (1TB HDD):**
sdc1: 1TB NTFS Win7/Linux shared data

**sdd (1TB ext HDD):**
sdd1: 1TB NTFS backup for sda, sdb, sdc

I know this looks like overkill, but I am a semi-pro photographer and have a lot of photo-related files that require storage on a separate drive and regular back-up to other sources.  

**Questions:**

[LIST=1]
[*]Anything wrong with my proposed setup?
[*]My previous dual-boot setup only had one Windows partition, though both Linux and Windows were on the same SSD, are there any dual-booting issues with allowing Windows to keep its System Recovery partition?
[*]I don't know what to do with the 350+GB unallocated on the sdb.  Could there be any Linux-related use for that?  Could I multiboot different flavours of Linux using the setup in sdb, or will having one /boot partition cause problems with different Linux kernels?  350GB still seems like overkill for this, though!
[/LIST]

---

### Post by oldfred on 2012-11-19
First if your system is an i5 then your BIOS is really UEFI (actually both). You have to install both Windows & Ubuntu in either BIOS mode or UEFI mode and if empty drive install disks should offer both choices. And how you boot install disk is how it installs.

Also then you have historical MBR(msdos) partitions and gpt partitions. Windows only boots from gpt partitions with UEFI. Ubuntu can use gpt partitions whether BIOS (with bios_grub partition) or UEFI (with efi partition).

gpt partitioning is required for drives over 2TB, so you do not have to use it. Most understand BIOS/MBR, but new systems are now UEFI and gpt.

Arch suggests gpt for SSDs. I use gpt on an old rotating drive just to learn about it. Once installed, I cannot tell any difference. But when I added my SSD I had to change to AHCI in BIOS and XP makes that extremely difficult to use, so I stopped using XP :)

       GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

            [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

Windows in BIOS boot from MBR will read data in other gpt drives. So you can stay with BIOS boot but have all but the Windows drive as gpt.

       I keep a lot of unallocated space on my then new 650GB drive. It now is almost full of 25GB / (root) partitions of my older Ubuntu and other experiments. So leave some space unallocated if not sure what to use it for.

You plan is fine. I prefer not to have a separate /boot (and you cannot share a /boot with other installs). 

With that much RAM some may suggest a virtual install. You lose a bit of performance (usually only gamers care that much)  but both systems are running at the same time and you can easily switch.

---

### Post by ibjsb4 on 2012-11-19
I run six hdd's and have tried many partitioning methods.  I think it just boils down to what works for you.  There are many good ways to do it.

Some will suggest a seperate "home" partition.  Myself I do not and run a shared data partition, rsync to another drive.

If you install Ubuntu on more than one drive its a good idea to make all drive bootable.  That way you can pull a drive and still boot.

Here's  some good reading Watch for "oldfred" in the links, he is full of good advice when it comes to partitioning.  :)

Edit:  LOL

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Partitioning+how+to&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Partitioning+how+to&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by offgridguy on 2012-11-19
> **ibjsb4 said:**
>  watch for "oldfred" in the links, he is full of good advice when it comes to partitioning.  :)

+1

---

### Post by oldfred on 2012-11-19
Just to confirm ibjsb4 on system on each drive and data not /home.

I used to just rotate my working Ubuntu install from drive to drive following this links logic. Now with my SSD, I just make sure I have a working install on every drive. 
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

    
I also prefer separate data partitions which seems to be what you are doing.

Thanks for the kind words, oldfred is just around a lot and promotes his opinions. Hopefully useful, but may not best for each user. I like to see alternatives (even corrections) and then try to improve my suggestions.

---

### Post by 9littlebees on 2012-11-19
> **oldfred said:**
> First if your system is an i5 then your BIOS is really UEFI (actually both). You have to install both Windows & Ubuntu in either BIOS mode or UEFI mode and if empty drive install disks should offer both choices. And how you boot install disk is how it installs.

Also then you have historical MBR(msdos) partitions and gpt partitions. Windows only boots from gpt partitions with UEFI. Ubuntu can use gpt partitions whether BIOS (with bios_grub partition) or UEFI (with efi partition).

gpt partitioning is required for drives over 2TB, so you do not have to use it. Most understand BIOS/MBR, but new systems are now UEFI and gpt.

Arch suggests gpt for SSDs. I use gpt on an old rotating drive just to learn about it. Once installed, I cannot tell any difference. But when I added my SSD I had to change to AHCI in BIOS and XP makes that extremely difficult to use, so I stopped using XP :)

       GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

            [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

Windows in BIOS boot from MBR will read data in other gpt drives. So you can stay with BIOS boot but have all but the Windows drive as gpt.
I definitely have UEFI.  Sounds like I need to read up quite a bit on how to ensure I am using GPT.

> I keep a lot of unallocated space on my then new 650GB drive. It now is almost full of 25GB / (root) partitions of my older Ubuntu and other experiments. So leave some space unallocated if not sure what to use it for.Excellent advice, I shall do just that!

> You plan is fine. I prefer not to have a separate /boot (and you cannot share a /boot with other installs).Yeah, I'm thinking of changing the Linux HDD to be partition like this:

-------------------------------------------------
**sdb (500GB HDD) - GPT**
sdb1: swap file
sdb2: 30GB ext4 /root (Xubuntu 12.10)
sdb3: 10GB ext4 /home (Xubuntu)
420GB unallocated space
-------------------------------------------------

I've read a really good article ([link]("http://askubuntu.com/questions/45427/recommended-partitioning-scheme-considering-upgrades-dual-triple-booting-multi")) about setting up partitions on multi-OS booting machines, so that they share one data partition (my 1TB HDD), but keep the /home hidden config files unique to the distro.

If I want a new partition, I can simply add a /root and /home partition after sdb3, and configure that one to point to my shared data partition.  This makes a lot of sense and ensures the integrity of each OS is not affected by the configurations of the others.

> With that much RAM some may suggest a virtual install. You lose a bit of performance (usually only gamers care that much)  but both systems are running at the same time and you can easily switch.
I do a lot of gaming, so I'd rather keep my precious RAM fully available.  Plus, I'd rather not mess with the driver issues which appear to be quite common in virtual OS's.

So I guess the next thing to do is figure out how to ensure that my Windows 7 install (first step in the whole affair) uses the GPT type.

---

### Post by 9littlebees on 2012-11-19
Lol, in the time it took me to write my reply to oldfred, I got three new ones.  :P

Hmm, so I could get away with my sdb drive only having 2 partitions, a swap and root?  I guess that makes sense.  There's just so many different ways to go!

My 1TB data drive is already loaded with a lot of data, so I'm not sure that I'll be creating a Knoppix partition on it, but that is some good reading for maybe looking at in future!

Thanks for the Knoppix link oldfred, I found an article linked there explaining how to create a dedicated 1MB grub partition to ensure that multiple Linux OS's (and Windows!) can all be displayed in one list.  I'll be adding that little 1MB partition to the beginning of my Linux HDD.

I'll start testing this either today or tomorrow, so will leave this as Unsolved for additional comments until I've had a chance to get it all working nicely.  So to confirm, here's my planned install:

-----------------------------------------------------
**sda (120GB SSD) - GPT**
sda1: NTFS 120GB Win7 (all on one partition following [this guide]("http://ubuntuforums.org/www.shivaranjan.com/2009/05/11/how-to-prevent-windows-7-from-creating-a-hidden-recovery-system-reserved-partition-during-installation/"))
-----------------------------------------------------


-----------------------------------------------------
**sdb* (500GB HDD) - GPT**
sdb1: EXT2 1MB Grub Partition ([guide here]("http://www.troubleshooters.com/linux/grub/grubpartition.htm"))
sdb2: swap 18GB
sdb3: EXT4 40GB /root (Xubuntu 12.10)
remaining disk space unallocated
-----------------------------------------------------


-----------------------------------------------------
**sdc* (1TB HDD) - GPT** (may need to change this to GPT if it is currently MBR)
sdc1: NTFS shared data partition
-----------------------------------------------------


-----------------------------------------------------
**sdd* (1TB ext HDD) - GBR/MBR?**
sdd1: NTFS backup partition
-----------------------------------------------------

*Should sdb, sdc, sdd actually start with an "h" instead of an "s"?

---

### Post by dannyboy79 on 2012-11-19
can I ask why you're making a swap partition that's 16GB in size? That's huge. I am just trying to learn here. ALso, I always have a seperate /home partition, just my 2 cents. 1mb grub partition seems small to me. WHen I had a dedicated boot partition it was 500mb I believe.

---

### Post by Cheesemill on 2012-11-19
> **dannyboy79 said:**
> can I ask why you're making a swap partition that's 16GB in size? That's huge. I am just trying to learn here. ALso, I always have a seperate /home partition, just my 2 cents. 1mb grub partition seems small to me. WHen I had a dedicated boot partition it was 500mb I believe.
I believe that the 16GB swap partition is for hibernation. To hibernate Ubuntu you need to be able to write the entire contents of your RAM to the swap partition (although it does get compressed so I think that 16GB is probably overkill, however, HD space is so cheap and plentiful that this shouldn't be an issue).

Also the GRUB partition is not the same as a /boot partition. When you are using GPT formatting instead of MSDOS formatting there isn't enough space to fit all of the bootloader code in the MBR, you need to create a small GRUB BIOS partition for the bootloader code to live in.


@9littlebees
I would skip the /boot partition, there really is no need to have this separate nowadays.

In my setup I have partitions for / and /home on the SSD so that I get the speed advantage that this entails, my home directory only contains the hidden application configuration files, all of the other folders (Music, Pictures, Videos etc) are just symlinks to the actual data directories on the shared NTFS partition on my mechanical drive.

---

### Post by oldfred on 2012-11-19
UEFI installs have extra partitions. 

All installs have to have an efi partition first. Windows also has a unformatted space (system reserved) somewhat like the bios_grub that Ubuntu has in BIOS.

       Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
I used to have a grub only partition when using old grub legacy. You have to manually maintain all your boot stanzas, but once you learn you actually copy & paste with a bit of editing for unique UUIDs and partitions. I still in effect do this with my USB flash drives as they have grub2 installs, and manual boot entries to boot ISO with loopmount. Then I can have multiple ISO on one flash drive.

I also learned for Ranchhand but Cavsfan documented the procedures.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by 9littlebees on 2012-11-19
> **dannyboy79 said:**
> can I ask why you're making a swap partition that's 16GB in size? That's huge. I am just trying to learn here. ALso, I always have a seperate /home partition, just my 2 cents. 1mb grub partition seems small to me. WHen I had a dedicated boot partition it was 500mb I believe.
Cheesemill has answered both your questions splendidly, but I'll elaborate on them a bit as well.  

You'll find a link in post 7 (next to the sdb1 partition entry) explaining the 1MB Grub partition in detail (including step-by-step instructions on setting one up).  The real beauty of the Grub partition (and why I'll be using one) is that if you install multiple Linux distros on one drive, that little partition allows their bootloaders to all play nicely and you can have a single menu allowing you to choose which distro to boot into.  You can't do that with a separate /boot partition, since that holds your Linux kernel, and these are often very different between distros.  

I'm basically future-proofing for when I feel brave enough to give Arch Linux a shot - if it all goes pear-shaped, I can always just boot into my main distro! 

As for the /home issue, for dual booters, having a separate, large /home partition to store your personal data is actually not a good solution, as you won't be able to access it on a second non-Linux OS (Windows 7 in my case).  Therefore I store all my data on my 1TB drive and (to put it simplisticly) point all my **visible** /home folders in Linux to this separate drive.  As that drive is NTFS, I can sync all my data between both Windows and Linux.  The beauty of this is that I could actually install a (theoretically) infinite number of Linux distros on the same machine, and they could each access this same batch of data.  Hence no need for a separate /home partition.  Since a /home partition contains a lot of hidden config files, you wouldn't be able to (necessarily) share one /home partition between multiple Linux distros, either.

> **Cheesemill said:**
> I believe that the 16GB swap partition is for hibernation. To hibernate Ubuntu you need to be able to write the entire contents of your RAM to the swap partition (although it does get compressed so I think that 16GB is probably overkill, however, HD space is so cheap and plentiful that this shouldn't be an issue).
Yeah, I wasn't sure about this.  I only had 2GB of swap in my previous dual-boot conifguration and simply removed the hibernate option from my log-off menu, so I may revert to that, especially since I never use hibernate.

> @9littlebees
I would skip the /boot partition, there really is no need to have this separate nowadays.

In my setup I have partitions for / and /home on the SSD so that I get the speed advantage that this entails, my home directory only contains the hidden application configuration files, all of the other folders (Music, Pictures, Videos etc) are just symlinks to the actual data directories on the shared NTFS partition on my mechanical drive.Again, you will see in post #7 that I updated my configuration and that it no longer has a /boot partition, having replaced it with a Grub one.

> **oldfred said:**
> UEFI installs have extra partitions. 

All installs have to have an efi partition first. Windows also has a unformatted space (system reserved) somewhat like the bios_grub that Ubuntu has in BIOS.

       Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    I used to have a grub only partition when using old grub legacy. You have to manually maintain all your boot stanzas, but once you learn you actually copy & paste with a bit of editing for unique UUIDs and partitions. I still in effect do this with my USB flash drives as they have grub2 installs, and manual boot entries to boot ISO with loopmount. Then I can have multiple ISO on one flash drive.

I also learned for Ranchhand but Cavsfan documented the procedures.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Thanks once again, oldfred!  Lots of good reading there, and will save me having to search for the good threads.  Using GPT with UEFI is starting to sound like a lot of bother...

Anyway, if there was some form of rep system on these forums, you'd be getting some in bulk!! :KS

---

