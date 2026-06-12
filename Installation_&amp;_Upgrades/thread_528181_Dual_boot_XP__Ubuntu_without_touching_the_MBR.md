---
title: "Dual boot XP / Ubuntu without touching the MBR"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by StephUb on 2007-08-17
Hi all,

So i am planning installing ubuntu in dual boot with XP on my laptop (just to give me time to be able to use ubuntu days to days)

The thing is that i am worried about the MBR on my laptop, it might be tatooed (wouldn't boot if the MBR is changed) 
So i read somewhere that you can let Windows boot redirect to ubuntu.

My questions are:

Where do you put grub in that case?

How do you tell windows to look for ubuntu boot ??

thanks a lot

PS: i got a Sony Vaio FS790B

---

### Post by ugm6hr on 2007-08-17
There are a variety of ways to do this - but the easiest is to use Grub4DOS.  Just search for it on google.

Essentially, you copy the Grub4DOS program to C:\ (assuming that Windows is on C:\), and manually add a text file C:\menu.lst to tell it where to find Ubuntu.

You just need to be a bit careful when installing Ubuntu to tell it not to install Grub to the default* hd0 *(better to tell it not to install Grub - not sure if this is possible, or else choose *hd0,1*, assuming Ubuntu is on the second partition).

---

### Post by StephUb on 2007-08-17
OK thanks i will look for this grub4dos.

I was thinking changing the file boot.ini of startup and recovery of windows and add ubuntu in this file.
Anyone got ideas or links that can be usefull

---

### Post by ugm6hr on 2007-08-17
> **StephUb said:**
> OK thanks i will look for this grub4dos.

I was thinking changing the file boot.ini of startup and recovery of windows and add ubuntu in this file.
Anyone got ideas or links that can be usefull

That is what Grub4DOS requires.  boot.ini *cannot* directly summon Ubuntu, but it can summon Grub4DOS, which can then access Ubuntu.

---

### Post by Herman on 2007-08-17
I agree with ugm6hr, it is much better to use Grub4dos, (WinGub) than to try to use boot.ini  
Here's how to use WinGrub, [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html")

[EasyBCD]("http://neosmart.net/dl.php?id=1") is nice too, I'm pretty sure it works for Windows XP, although it was originally for Vista. [Computer Guru]("http://neosmart.net/blog/") has put a lot of work into [EasyBCD]("http://neosmart.net/dl.php?id=1") and provides his own web site for it with support for it too.

I don't think you'll find much support for trying to boot with boot.ini.

Actually, it should be okay for you to try using GRUB as long as you make a backup of your MBR first. Here's how to make a backup of your MBR with a 'dd' command from a Ubuntu Live CD, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").

In most computers it is better to use GRUB if you can, but Grub4dos (WinGrub) is almost as good. You are putting yourself through some inconvenience by not using the regular GRUB. Windows is a weaker operating system than Ubuntu and needs frequent re-installing, where Ubuntu does not. You'll just have more work to do, that's all. Besides, it's easier to convert to Ubuntu and delete Windows if you install GRUB to MBR, but I guess you can do that later.

Regards, Herman :)

---

### Post by StephUb on 2007-08-17
Ok i read a bit about grub4dos and wingrub.

What are the differences between the two ?

I found this link for installing both using wingrub:
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

thanks again

---

### Post by Herman on 2007-08-17
Wingrub includes grub4dos and provides a frontend for helping you set up and configure it.

Regards, Herman. :)

---

### Post by StephUb on 2007-08-17
OK thanks a lot for the infos.
i am gonna try that this week end

---

### Post by Herman on 2007-08-17
Okay then, good, WinGRUB is a very good program, let me know if that web page needs improving and I'll look at updating it if needed, to make it easier for others who may need to use WinGrub to boot Ubuntu in the future. :)

Regards, Herman :)

---

### Post by cldmello on 2007-08-17
Thanks a lot for WinGrub!

I re-install Windows every 3 months and need to get back to my Linux without having to loose it as well. This solution works great for me. It allows me to boot into Ubuntu and restore my Grub MBR backup everytime I re-install this crappy windows.

---

### Post by StephUb on 2007-08-17
Ok i think i got it but i still have one question,

Where do i install grub if i don't want it on the MBR ?

i put it on the disk where i installed ubuntu ? ( a kinda /hda2 ??)

thanks again for your help

---

### Post by Herman on 2007-08-17
> Thanks a lot for WinGrub! I re-install Windows every 3 months and need to get back to my Linux without having to loose it as well. This solution works great for me. It allows me to boot into Ubuntu and restore my Grub MBR backup everytime I re-install this crappy windows. Hello cldmello, the developer of WinGrub is [bean123]("http://ubuntuforums.org/member.php?find=lastposter&t=513921") who may be somewhere here in this forum.
I just like making web pages that help people install and boot Ubuntu, so I will agree with you and say thanks to [bean123]("http://ubuntuforums.org/member.php?find=lastposter&t=513921") for WinGrub, thanks [bean123]("http://ubuntuforums.org/member.php?find=lastposter&t=513921")! :)

Yes, I used to re-install Windows XP very frequently too as soon as I realized the protection vendors were telling fibs about how well they were able to protect my computer. Evil malware had existed undetected in my computer already for over six months in spite of all the scanning I used to do, before an on-line scan from a rival protection vendor detected the malware that could have turned my computer into a zombie. 
Now that I know about Ubuntu, I have no more need to let Windows be exposed to the internet at all, only for updates. Actually, neither my wife or I use Windows XP at all these days for anything. More of our friends are switching to Ubuntu too. I always tell people if they must run Windows XP for some reason then it's good if you can at least dual boot with Ubuntu so you can use Ubuntu for most things except what you have to use Windows for. Windows will remain fairly clean if you don't receive email in it or venture onto the internet. Ubuntu is better for those jobs. 



StephUb, 
>          Ok i think i got it but i still have one question, Where do i install grub if i don't want it on the MBR ? i put it on the disk where i installed ubuntu ? ( a kinda /hda2 ??) You can 'install GRUB' to your /dev/hda2 or (hd0,1) partition if that's **normally** your Ubuntu partition. Then the IPL (also called 'stage1' ) for GRUB will be written to the boot sector of your Ubuntu partition.

You could also install GRUB to a floppy disk (fd0) or /dev/fd0, or to some other device of your choice like a USB memory stick if you prefer, but to the boot sector of the Ubuntu partition would be the usual next best if you are trying not to touch the hard disk's MBR.
If you have more than one hard disk you could install GRUB's IPL to the MBR of a non-first hard disk, like (hd1) or (hd2), for a second or third hard disk.
[COLOR=Red]Just make sure you don't write it to (hd0,0), because that would **normally** be your Windows boot sector[/COLOR]. Ironically, in an effort to avoid the MBR, where GRUB probably won't actually do any harm at all, some Windows users end up installing GRUB's IPL to their Windows boot sector, where it does stop Windows from being able to boot. (Even that can easily be repaired though).

**Be sure to check first** if your Windows really is (hd0,0) and Ubuntu will be (hd0,1) or something else. Some computers have a recovery partition for a first partition, bumping the partition numbering for subsequent partitions up one, which could again cause someone to make a mistake and installing GRUB to (hd0,1) might be dead wrong. So just be careful. :)

Regards, Herman :)

---

### Post by StephUb on 2007-08-21
Ok thanks again,

I have removed the first recovery partition (i reinstall form master DVD whithout reinstalling the recovery part).
But just to make sure, is Gparted 's gonna give me the disk in hd0,1 ? 
I am remembering something more like hda1...

What software can i use to make sure of my partitions in a hd0,0 hd0,1 hd0,2....  ?

thanks

---

### Post by Herman on 2007-08-21
>  I have removed the first recovery partition (i reinstall form master DVD without reinstalling the recovery part).
But just to make sure, is Gparted 's gonna give me the disk in hd0,1 ? 
I am remembering something more like hda1...
What software can i use to make sure of my partitions in a hd0,0 hd0,1 hd0,2....  ? You don't need any extra software, if you have the Ubuntu LiveCD, for Feisty or whichever Ubuntu you want to install, just boot the LiveCD and take a look at your partitions in 'System'-->Administration'-->'Gnome Partition Editor'.
Gnome Partition Editor is another name for GParted. 

Now, as for device naming, you may be used to calling your hard disks, if you had more than one, first hard disk, second hard disk, third hard disk and so on. Or hard disk 2, hard disk 2, hard disk 3...
Your first partition would be partition 1, your second partition would be called partition2, your third partition would be partition 3, and so on...
simple right? That is in everyday human terms.

Now, in 'Linux' spiel, 
hard disk1, partition1 will be called: dev/hda1
hard disk1, partition2 will be called: dev/hda2
hard disk1, partition3 will be called: dev/hda3'...
and if you had a second hard disk,
hard disk2, partition1 will be called: dev/hdb1
hard disk2, partition2 will be called: dev/hdb2
hard disk2, partition3 will be called: dev/hdb3...
( 'dev' stands for 'device', and 'hd' is short for 'hard drive', followed by a letter representing the hard drive number, and a partition number).

GRUB has a different numbering system.
In GRUB's way of numbering things, we start counting from zero,
The hard disk is given a number instead of a letter,
The GRUB numbers are enclosed in brackets.
hard disk1 (MBR) will be called: (hd0)
hard disk1, partition1 will be called: (hd0,0)
hard disk1, partition2 will be called: (hd0,1)
hard disk1, partition3 will be called: (hd0,2)
and if you had a second hard disk,
hard disk2 (MBR) will be called: (hd1)
hard disk2, partition1 will be called: (hd1,0)
 hard disk2, partition2 will be called: (hd1,1)
 hard disk2, partition3 will be called: (hd1,2)

It's actually quite simple and most don't need to know it anyway if they just want to let Ubuntu install GRUB to MBR, 
You can also use your LiveCD to make a backup of your bootlaoder area of your MBR, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")., if you want to make sure. I recommend you do that.
I didn't mean to imply in any way that you should delete your recovery partition. Actaully, now that might confuse matters worse already than they were before. Now you new partition will be whichever partition number was left vacant when you deleted your recovery partition. So now you will really need to be paying attention during install not to install GRUB to your Windows boot sector by accident.
It would be simpler now, for you to just make a backup of the MBR first, do the default and let Ubuntu install GRUB to MBR andsee if everything works okay.
In 999.9 out of 1000 computers or better, GRUB will work great.
If GRUB doesn't work, then you can always restore your MBR from the backup, and boot another way, such as WinGrub.
However, if you want to try to aviod installing GRUB to the MBR at all, still make a backup anyway, then try to install GRUB to whichever partition will be your Ubuntu partition. 
Good luck, and all the best, I hope it all goes well for you.
Regards, Herman :)

---

### Post by StephUb on 2007-08-21
OK i got the theory.

As far as my recovery partition, i didn't delete it. I upgraded my HD for a bigger and faster one so on the reinstall of Wxp, i choose not to reinstall the recovery partition.

So if i understood all well, using Gparted to see my partitions, they should all appear and i have to make the naming by myself. I explain..

I am gonna see 
only one disk
Partition 1 XP NTFS
Partition 2 Ext3 for ubuntu
Partition 3 Linux Swap
Partition 4 Documents Fat32

so it's gonna be
1= hd0,0
2=hd0,1
3=hd0,2
4=hd0,3

and i should install grub on hd0,1

thanks again for the help

---

### Post by Herman on 2007-08-22
> and i should install grub on hd0,1:)  Yes, almost correct,  (hd0,1) remember, the brackets are important. You'll probably get some kind of an error message if you forget to use the brackets. :) Anyway, I think you understand the main idea okay now.
> As far as my recovery partition, i didn't delete it. I upgraded my HD for a bigger and faster one so on the reinstall of Wxp, i choose not to reinstall the recovery partition. :) I, okay, I am less worried now, thanks for clarifying that. 
Actually, I do delete my own recovery partitions myself too, so I can use the extra disk space. I use Partimage or Clonezilla in Linux if I need to back up and restore a partition. But I don't think it would be right for me to tell other people to do that in case it causes them some kind of unforeseen problems.

>  I am gonna see 
only one disk
Partition 1 XP NTFS
Partition 2 Ext3 for ubuntu
Partition 3 Linux Swap
Partition 4 Documents Fat32 Have you already made your partitions? 
Most people will probably use the Ubuntu installer's partitioner to make their partitions, so they probably would not know what their partitions will be ahead of time. That's okay if you did, or even if you just have a plan in mind about how you would like your partitions to turn out.

Yes, Windows is normally in partition number 1, or (hd0,0) in most cases. 
It's also quite normal for Ubuntu to be in partition number 2, or (hd0,1). Ubuntu doesn't mind what partition number it is given.
Partition 3 Linux swap and partition 4 FAT32 Documents will be okay too.

Just a hint though, it could be a little better if you make an extended partition for partition 3, and then inside it make your Linux swap a logical partition, it will be number 5 and your FAT32 Documents partition will be number 6, logical.
The reason I think that might be a good idea is because we are only allowed up to four primary partitions per disk. The way you are planning to do it will work, you only want four partitions right now, *but*, if you decide you might want another partition in the future, you won't be able to. You will have already used your allowance of four primary partitions. You are 'painting yourself into a corner' in a way, but with partition numbers.
If you make one of your primary partitions an extended type of partition, you can then have a great number of logical partitons in a series inside it. Therefore it would be wise to consider making an extended partition now, to keep your options open for the future. :)

But you don't have to listen to me, I am just trying to be helpful, and I don't mean to be bossy. :) (Just freindly advice).

Regards, Herman :)

---

### Post by Herman on 2007-08-22
Here is a great website all about installing with the Ubuntu Live CD, [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
I'm not sure if you will have already read that or not, but I think you should read it if you haven't yet.

Here's the officail link too, [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Regards, Herman :)

---

