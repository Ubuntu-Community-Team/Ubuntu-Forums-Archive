---
title: "Installs GRUB on wrong partition"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by siggi.f on 2011-09-10
Hello everybody,

i'm new on ubunto, not completely new on linux.
I'm trying to install kubuntu on a hp elitebook 8730w wit a raid 0 system, but can't succeed.
I have an bootmanager installed: bootit from terrabyte.
So my harddisc ist partitioned as following:

8MB    Bootit
20GB  drive C for Windows
20GB   / for ubuntu
5GB     swap
rest     drive D for Windows


When i start "Ubuntu" in the Bootmanager the following table is written in the mbr:

20GB / for ubuntu
5GB swap

The rest of the drive is seen by ubuntu as free unpartitioned.

So i start the installing process and when it asks for partitioning i choose "manualy"
I select first partition choose mountpoint / and format it as ext4 and the second partition as swap.
AT THE BOTTOM I ALWAYS CHOOSE TO INSTALL GRUB ON THE SAME PARTITION AS MOUNTPOINT / IS.
and it always writes it in the MBR of the drive, so all my partitions are gone, and i have to recover all.
I tried it 3 times and always the same trouble.

Maybe someone can help me out.
I dont want to be diapointed by first time use of ubuntu.

Big thanks

---

### Post by YesWeCan on 2011-09-10
Hi there and welcome to the Ubuntu Forums. You want to install Ubuntu 11.04 on a Windows RAID0 and partition boot it using your Bootit program?

---

### Post by siggi.f on 2011-09-10
At the bottom there is Bootit from terrabyte unlimited, a bootmanager with many features.
At every boot it writes the choosen partition table to the mbr.
In the case of ubuntu it writes the 2 partitions to the mbr, so i can choose these partitions for installation at the ubuntu manual menu.
I also can choose to install the grub bootloader not in seen whole Disk . Here i have to choose the partition / to Not mess up the mbr of the Disk.
It does always mess it up.

---

### Post by YesWeCan on 2011-09-10
Interesting. So Bootit actually alters the partition table so that logical partitions become bootable? Eek.
Well you have a few challenges here. Installing Ubuntu to a Windows RAID is one.
Even without RAID, Grub2 does not work reliably when installed to a partition. Grub1 can be made to boot from a partition reliably.
Grub1 and Grub2 need some help to make them boot on a Windows RAID.  I don't have the solutions to hand so some Googling will be required.
You need to look for info about fake RAID and Grub legacy.

---

### Post by siggi.f on 2011-09-10
**[SIZE=2]Bootit Menu for partitioning a harddisk:[/SIZE]**

[IMG]http://www.downloadatoz.com/bootit-next-generation/images/work-with-partition.jpg[/IMG]



**[SIZE=2]and thereafter you can choose up to 4 visible partitions on every drive[/SIZE]**

[IMG]http://www.terabyteunlimited.com/images/bibm/bibm_editbootmenu.jpg[/IMG]

so eg i choosed only "Linux native" (not the one in the extended part) and "Linux Swap/Solaris" to be seen when i start the menu item Linux. Only these two partitions will be inserted in the MBR of the disc so that Ubuntu will only see these partitions and the rest will be seen as free.
At Windows Menu i chosse only the windows partitions to be seen be Windows so all other will be seen by Windows as free space.

I don't think that it has something to do with the raid 0 system beacouse after intalling it starts and works. The only thing is, it messes up the bootit-software installed and all the other generated partitions as free beacuse it installs grub on the MBR.

Why is there a menu to choose where to install the bootloader, if it does't do what you choose to do?

From the Bootit knowledge base:
*The most important point for BootIt BM users to observe when installing Ubuntu, is to ensure that the boot loader (Grub2 in this case) gets installed to the Linux partition, which is typically the root partition. The default action is to install Grub2 to the MBR, which will completely overwrite BootIt BM, and require that it be reinstalled from scratch. It can also **lead to data loss**, particularly if BootIt BM is configured to NOT limit primary partitions.*
[I].
.
.
The important thing is that you **don't** install Grub2 to the MBR, and that you **do** install Grub2 to the same partition that you selected as the partition to boot from in the BootIt BM boot item.[/I]


btw. thats not a windows raid, at this stage windows bootmanager hasn't been loaded.
Bootit acts as a bootmanager.
Is it possible to install kubuntu as i have done it befor, repair the bootit bootmanager, recover the other partitions, and thereafter install grub1 to the / partition?
How can i do that?

---

### Post by YesWeCan on 2011-09-10
I've given this some thought and I still don't understand what is going on. :)

1) Is it the case that when you boot Windows it runs RAID0 with hd0 & hd1 but when you boot Ubuntu it will run non-RAID on hd0?

2)> So i start the installing process and when it asks for partitioning i choose "manualy"
I select first partition choose mountpoint / and format it as ext4 and the second partition as swap.
AT THE BOTTOM I ALWAYS CHOOSE TO INSTALL GRUB ON THE SAME PARTITION AS MOUNTPOINT / IS.
and it always writes it in the MBR of the drive, so all my partitions are gone, and i have to recover all.
I tried it 3 times and always the same trouble.
This worries me. Why does the MBR area get corrupted when you choose to install Grub to the / partition? I do not understand this. I believe the alternate install CD allows you not to install Grub at all; which is what you want.

3) If you boot an OS with Bootit's "fake" MBR partition table then I presume you must not do any subsequent partitioning or you'll corrupt the "hidden" partitions. Seems a risk of using this Bootit system.

4) > Why is there a menu to choose where to install the bootloader, if it does't do what you choose to do?
That is an excellent question. IMO it shouldn't allow installing to a partition anyhow. Lots of people get into all sorts of trouble because of this, not just because booting is unreliable but because they accidentally install to their Windows partition and trash its boot sector.

I don't think the Bootit knowledge base should recommend installing Grub2 to a partition. Grub2 is not designed to boot this way - it has to have 50 sectors of space outside a fs to embed its boot program. In ext fs format there are only 2 sectors of space. In reiserfs there are 128 but Grub2 doesn't support it! Grub1 does support embedded install to a reiserfs partition so this is the way to do it. Of course Windows file systems always provide enough space and this is why Windows is MBR boot compliant and Ubuntu/Grub is not.

5) I can describe how to install Ubuntu on hd0 in a non-RAID way, with Grub1 if you think this will work. You probably need to disable dmraid in the main menu (F6) of the installation CD to stop Ubuntu getting confused by the dmraid superblocks (that will be on this disk if you have set Windows up to use RAID0). I don't know whether this will work, tho.

In summary,
Boot the alternative installation CD
Create a 500MB boot partition with reiserfs format, mount /boot here
Create an ext4 partition for / and a swap
Install without grub
chroot install grub1, and install boot program to the boot partition

---

### Post by siggi.f on 2011-09-11
Thank You for helping!

3 things i am concerned about:

-maybe the problem is the raid. As i read it's only a software raid even if it is configured in the bios. I didn't know that. The Bootit Bootmanager recognize it as 1 drive, so i thought all that cames behind this bootmanager should see it the same way, as 1 drive.

-my partitions are:
[B][I]8MB    Bootit
20GB  drive C for Windows
20GB   / for ubuntu
5GB     swap
rest     drive D for Windows[/I][/B]
Is it so, that the boot-partition cant boot a partition behind the 20GB
I'll give it a try to exchange the 2 partitions, so that Linux is first and Windows is behind.
[B][I]8MB    Bootit
[/I][/B][B][I]20GB   / for ubuntu
[/I][/B]****[B][I]20GB  drive C for Windows
 [/I][/B]***5GB     swap***
***rest     drive D for Windows***


-Why is there a menu to choose where to install the bootloader, if it does't do what you choose to do?
It should warn you, if it is not possibel, but not mess up the mbr of the drive.



Here is the link to the [knowledge base]("http://www.terabyteunlimited.com/kb/article.php?id=279"). I think i have done all as it is advised

Once a year try escaping from windows, but everytime i fall back due to some problems.
And i think that's the reason why many user don't use this os. :(

---

### Post by mue.de on 2011-09-11
> **siggi.f said:**
> **[SIZE=2]Bootit Menu for partitioning a harddisk:[/SIZE]**


Why is there a menu to choose where to install the bootloader, if it does't do what you choose to do?

From the Bootit knowledge base:
*The most important point for BootIt BM users to observe when installing Ubuntu, is to ensure that the boot loader (Grub2 in this case) gets installed to the Linux partition, which is typically the root partition. The default action is to install Grub2 to the MBR, which will completely overwrite BootIt BM, and require that it be reinstalled from scratch. It can also **lead to data loss**, particularly if BootIt BM is configured to NOT limit primary partitions.*
How can i do that?

I  used several boot-CDs/DVDs and experienced that the question about the aim where to install GRUB has moved to a quite hidden place on the last screen of the install process:
at the right lower corner there is an entry 'advanced / erweitert'? i guess, where you can choose the partition 

Hope it helps

mue.de

---

### Post by YesWeCan on 2011-09-11
> **siggi.f said:**
> Thank You for helping!

3 things i am concerned about:

-maybe the problem is the raid. As i read it's only a software raid even if it is configured in the bios. I didn't know that. The Bootit Bootmanager recognize it as 1 drive, so i thought all that cames behind this bootmanager should see it the same way, as 1 drive.
Thats right. If it were full hardware raid then it wouldnt be a problem. Because it is fake raid each OS has to be configured to use it.

> 
-my partitions are:
[B][I]8MB    Bootit
20GB  drive C for Windows
20GB   / for ubuntu
5GB     swap
rest     drive D for Windows[/I][/B]
Is it so, that the boot-partition cant boot a partition behind the 20GB
I'll give it a try to exchange the 2 partitions, so that Linux is first and Windows is behind.
[B][I]8MB    Bootit
[/I][/B][B][I]20GB   / for ubuntu
[/I][/B]****[B][I]20GB  drive C for Windows
 [/I][/B]***5GB     swap***
***rest     drive D for Windows***

Because this is raid0 on the whole disk the partitions have to be mirrored, they cannot be staggered across the two disks. This is what I would do: Delete all your Ubuntu partitions on both disks. Tell Bootit to make the MBR partition table true to reality. Then boot the Ubuntu alternate install iso (which should detect the fakeraid) and make 3 extended partitions as I described: boot, root, swap. Choose not to install grub.
Then boot desktop live CD and chroot into the root partition, insall grub legacy and put boot code in boot partition. Then you can use Bootit to make the boot partition primary and bootable. I'll provide more details shortly.

> -Why is there a menu to choose where to install the bootloader, if it does't do what you choose to do?
It should warn you, if it is not possibel, but not mess up the mbr of the drive.The Ubuntu installer is he worst of the fedora and SuSU ones. It has git a lot of user hostile behaviour and I cannot understand why Canonical uses it. But there we are.

> Here is the link to the [knowledge base]("http://www.terabyteunlimited.com/kb/article.php?id=279"). I think i have done all as it is advised
My opionion is that the knowledge base is in error. It implies that Grub2 works fine in a primary partition. This is not true.

> Once a year try escaping from windows, but everytime i fall back due to some problems.
And i think that's the reason why many user don't use this os. :(
Ubuntu is not properly designed to do same drive dual booting with Windows. If Ubuntu is installed to a separate drive then all is good. Linux has its own raid system that is incompatible with fakeraid and so fakeraid support is patchy.
Now, if I were in charge of Canonical I would stop fighting/denying Windows and recognize that the best way to attract new users, most of whom will be Windows users, is to make Ubuntu easy and non destructive  to install on existing Windows systems. But I'm just a simple penguin. :)

I think we can get your system working the way you want. Do you want to go ahead and install Ubuntu again without grub and then we'll set up grub legacy for partition booting?

---

### Post by Quackers on 2011-09-11
Not wishing to butt in here, but if it is the case that you are installing Ubuntu or grub2 to a partition named /dev/sdaX (where X is the partition number) whilst using a raid array then corruption can result, as you are trying to write to only one drive of a raid0 array. 
Your raid partitions should be something like /dev/mapper/isw_hdgdfghf_p1 if using Intel raid. Those are the partitions you should be addressing.
Please ignore me if I've missed something!

---

### Post by YesWeCan on 2011-09-11
Hi. Please pitch in...this is a tricky scenario.

 That's right. I mean it is right that one needs to choose the dmraid partition name which will be of the form /dev/mapper/isw_abcd1234

What isnt right is that the installer offers component device partitions or any partitions at all since Grub doest work reliably this way. With fedora and SUSE installers you get verification steps and a final summary of what the installer is about to do, and you have the option not to install grub at all.

If the Ubuntu installer is told to install to the / partition and goes and overwrites the MBR area...what is that all about? Surely a malfunction.

---

### Post by Quackers on 2011-09-11
If the OP is not getting the /dev/mapper named partitions in gparted it may be worth installing kpartx to the live cd/usb desktop first. They should then show up.
It is certainly not safe to use /dev/sdaX partitions when using Intel raid0, as I found to my cost :-)
It can destroy the raid array.

---

### Post by YesWeCan on 2011-09-11
> **Quackers said:**
> If the OP is not getting the /dev/mapper named partitions in gparted it may be worth installing kpartx to the live cd/usb desktop first. They should then show up.
It is certainly not safe to use /dev/sdaX partitions when using Intel raid0, as I found to my cost :-)
It can destroy the raid array.
Ouch. How does kpartx differ from, say, running [COLOR="DarkSlateBlue"]dmraid -ay[/COLOR] to activate the array?
Perhaps you can confim this: I understand the alternate installer automatically recognizes fake raid.

Unfortunately, I don't have a fake raid set up to reverse-document the way it works. :P

---

### Post by Quackers on 2011-09-11
kpartx wasn't previously required for me but with 11.04 it was required so that gparted could see the /dev/mapper partitions and drive. Without kpartx gparted would not see the raid array or its partitions - only the /dev/sda and /dev/sdb drives/partitions.

---

