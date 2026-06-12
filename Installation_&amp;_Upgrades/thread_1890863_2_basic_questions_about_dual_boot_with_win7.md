---
title: "2 basic questions about dual boot with win7"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by phedro on 2011-12-04
Starting with a HP notebook with win7 installed and the usual 4 partitions (System, c, HPTools and Recovery). I made the recovery dvd set and deleted the Recovery partition to install 11.10. After shrinking c I have the 3 win partitions and 250 GB unallocated space for ubuntu.This is what the ubuntu installer shows when I choose "something else" at the where to install ubuntu question.OK.
 Hence on, I found a lot guides on how to manually create 4 partitions (boot, swap, / and home)  prior to installation, so my first question is:
1- can't I just select the unallocated space and let the installer make the job and create the necessary partitions? Previous ubuntu distros had a similar function (use the largest unallocated space) 
2- do I really have to install grub in a different partition and modify win7 boot menu with easyBCD to avoid a mess with dual boot after win7 upgrades?
Thanks for helping..

---

### Post by 2F4U on 2011-12-04
1. Yes. And if I remember correctly the option is named install Ubuntu besides Windows.
2. I don't use Windows, so can't answer that question.

---

### Post by Basher101 on 2011-12-04
You should first create a Logical partition and inside that one you could manually set as many other partitions as you want. Ubuntu is not picky at all regarding partitions..

---

### Post by darkod on 2011-12-04
NO. For any type of setup different from the standard / + swap you can NOT use the standard auto options. For creating your own layout and for better control, select the Manual option (Something Else in the last version I think).
That will show you the partition list of your disk. Create the partitions as logical, that's the only option when you already have 3 primary.
You don't really need separate /boot, no real help. But a separate /home is a very good "investment" so you can do clean installs in the future and keep your /home intact.

I would put grub2 on the MBR, that's its natural location. Don't worry if during any future windows reinstall or upgrade it gets deleted. The recovery of grub2 to the MBR takes literary two commands in terminal from live mode.
As a matter of fact, you will probably run into more issues putting grub2 onto a partition and trying the chainloading from win7 bootloader, than to recover grub2 to the MBR once in a while. I guess you don't do reinstalls every week. :)

---

### Post by phedro on 2011-12-04
That's the point, I'm not interested in having a lot of partition. I can make a primary one (the fourth) of the unallocated space. But I'd rather let ubuntu installer create the necessary partions, I think it should, but am not sure.

---

### Post by phedro on 2011-12-04
> **darkod said:**
> NO. For any type of setup different from the standard / + swap you can NOT use the standard auto options. For creating your own layout and for better control, select the Manual option (Something Else in the last version I think).


But I'd just like to have the standard / + swap, it always worked fine for me. So can I select the unallocated space in the "something else" option and let the installer do the job and create the two standard partitions?

And regarding Grub, do I have to do something special after a standard installation?
Thanks

---

### Post by darkod on 2011-12-04
No, something else is used for manual partitioning. If you select that, the installer will expect you to set the partitions yourself.

If you are interested in the standard setup you can use the "side by side" option and it should allow you to point it to the unallocated space you have (it has to be unallocated, not belonging to any partition).

Not sure how the options are called exactly, I always use manual partitioning.

PS. No, you don't need to do anything special about grub2 if you want to use it on the MBR.

---

### Post by phedro on 2011-12-04
Thanks Darko!
So If I decide it's time to go for manual formatting, do I have to create the three /, swap and home logical partitions?

---

### Post by oldfred on 2011-12-04
Partitioning is very personal as it depends on what you want to do. I also find my own optimal partitioning is not so good a year or two later as I have changed. That said this is one suggestion:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

You can use the Ubuntu liveCD to make Linux repairs, but not many Windows repairs. So it is best to have a Windows repairCD also.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by MAFoElffen on 2011-12-04
> **phedro said:**
> That's the point, I'm not interested in having a lot of partition. I can make a primary one (the fourth) of the unallocated space. But I'd rather let ubuntu installer create the necessary partions, I think it should, but am not sure.
+1 on darko and oldfred's...

But let me explain a little differently: You have a limit of 4 primary partitions. What also counts as 4 is if you have 3 primary -and- 1 extended partition. Within an extended partition you can have unlimited logical partitions. (some say 512 logicals, but I haven't really tested that limit.)

If you have your 3 windows partitions and try to add the Linux ext4 as a primary partition... your at your limit and won't be able to add a swap partition. 

If you go manual  
- Add the 4th partition as all unused space as "extended" 
- Then create logical partition on unused space (minus twice your RAM size for the Linux swap) 
 -- Options: ext4, mount at "/", format 
- Create logical partition on unused space as Linux-swap

Note: Win has to boot in a primary, but can read/write to an logical NTFS partition.  Linux and Unix deosn't care what kind of partition it's in. Even on a fresh disk, I usually put Linux distros in Extended/Logical to save primaries for something that is not.

I always use manual partitioning.

---

### Post by critin on 2011-12-04
> **phedro said:**
>  After shrinking c I have the 3 win partitions and 250 GB unallocated space for ubuntu.This is what the ubuntu installer shows when I choose "something else" at the where to install ubuntu question.OK.
 Hence on, I found a lot guides on how to manually create 4 partitions (boot, swap, / and home)  prior to installation, so my first question is:
1- can't I just select the unallocated space and let the installer make the job and create the necessary partitions? Previous ubuntu distros had a similar function (use the largest unallocated space) 
2- do I really have to install grub in a different partition and modify win7 boot menu with easyBCD to avoid a mess with dual boot after win7 upgrades?
Thanks for helping..

In  my experience, I like to make the unallocated space into one extended partition so you can add partitions later if you want to add/try a different version OS.  It can hold as many partitions as there is room for.  

Install ubuntu into the expanded unallocated space and it will partition for you.  
If you choose install 'side by side' with windows it will do exactly that and will not use the separate partition of unallocated space--it will try to squeeze ubuntu into Windows partition, you don't want that.

---

### Post by phedro on 2011-12-04
> **critin said:**
> Install ubuntu into the expanded unallocated space and it will partition for you.
So, should this expanded unallocated space be formatted as an extended partition or just left as unallocated space?
> **critin said:**
> If you choose install 'side by side' with windows it will do exactly that and will not use the separate partition of unallocated space--it will try to squeeze ubuntu into Windows partition, you don't want that.
No, I definitely don't want that. Otherwise I should have not shrinked the c partition...

---

### Post by darkod on 2011-12-05
> **MAFoElffen said:**
> 
If you go manual  
- Add the 4th partition as all unused space as "extended" 
- Then create logical partition on unused space (minus twice your RAM size for the Linux swap) 
 

Unfortunately I have to correct his slightly.

The creation of the extended partition (and the logicals inside) is different depending on the OS you do it from. In your case, during the ubuntu install, the manual partitioning option will give you only options to create Primary or Logical partition in the unpartitioned space. The word Extended doesn't exist if I remember correctly.
This is because linux automatically joins all logical partitions that are next to each other in one extended partition.
For example, you have your first three primary partitions and 100GB in unpartitioned space.
In linux you would: start creating logical partitions from that space, for example 20GB logical for /, 75GB logical for /home, 5GB logical for swap area. Linux will automatically show 100GB extended partition containing the 3 logicals you created. But they need to be physically next to each other. You can't have like primary-logical-primary-logical-primary. In this case the two logical can't be joined as one extended, and with 3 primary you are beyond the 4 partitions limit.

In windows, again if I remember Disk Management correctly, you will first actually create extended partition from the 100GB space, without specifying any filesystem, and only after that inside the extended you create the logical partitions.

As already said many times, it's best to use manual during the install and just create one bigger for the / partition and one smaller for swap area,
or
one 15-20GB for /, one smaller for swap area, and the rest for /home.

/ and /home would be ext4 filesystem type.

---

### Post by critin on 2011-12-05
I hope you're not becoming confused--lol  Everyone has their own way of  doing the same thing.  I don't make swap partitions but let the  installer do it.

In unallocated space, choose make extended  partition.  Then you can make separate smaller partitions inside if you  wish to and have plenty of room.  Format the smaller partition or let  the install do it.  I let the installer do everything it can.  

A pic of my setup to show what I mean--notice the extended partition.

---

### Post by sant on 2011-12-06
A good tutorial on installing  Windows 7 and Ubuntu side by side :
[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

---

### Post by Mark Phelps on 2011-12-06
> **sant said:**
> A good tutorial on installing  Windows 7 and Ubuntu side by side :
[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

That is NOT a "good tutorial" -- as it recommends shrinking the Win7 OS in such a way that risks corrupting the Win7 filesystem.

A much better way is to use the Win7 Disk Management utility to shrink the Win7 OS partition.

---

### Post by sant on 2011-12-06
The tutorial advices on that risk:
"Whenever you use a partitioning tool against an installed system, there's a chance of a problem, filesystem corruption and who knows what else. There is no guarantee for success. Re-partitioning of installed operating systems is risky. This is why you should always create your setup BEFORE installations, so you never have to face this kind of problem."
and explains how to fix it.

---

### Post by darkod on 2011-12-06
> **sant said:**
> The tutorial advices on that risk:
"Whenever you use a partitioning tool against an installed system, there's a chance of a problem, filesystem corruption and who knows what else. There is no guarantee for success. Re-partitioning of installed operating systems is risky. This is why you should always create your setup BEFORE installations, so you never have to face this kind of problem."
and explains how to fix it.

Yes, it does warn you and there are always chances things to go wrong. But I also have to object to the word "good" at least as far as partitioning is concerned.
Since windows is picky about tools it can handle, it's much much better to recommend using the windows Disk Management for any resizing of the windows system partition. After all at least they started to offer a tool to do it from windows for free, not to have to buy Partition Magic like before, etc.
Trying to simplify things too much has gotten a lot of people into trouble, and even hating linux. Don't get me wrong, my opinion is that anyone trying to install any OS should do their partitioning lessons first, but life is not ideal right? :)

Offering a tool that "does it all", trying to be helpful, has totally opposite effect when windows stops booting because of the resize. I wonder if a better way would have been "hey, make unpartitioned space first any way you want, then install" approach. At least they won't blame ubuntu. :)

---

### Post by Mark Phelps on 2011-12-06
Well ... I guess we can all cite text from the tutorial ...

My comment about it NOT being good was based primarily on the following wording (from the tutorial): 

> To this end, we will use the GParted partitioning tool to resize (shrink) the Windows installation and create new partitions for Ubuntu. 

This clearly indicates that their intention is to use GParted, not the Windows 7 Disk Management utility, to shrink the Windows OS partition.

Warnings aside (which, I have found most folks ignore anyway) advising the use of GParted to do the shrinking is a BAD idea.

---

### Post by critin on 2011-12-06
With  250 GB unallocated space for ubuntu, I wouldn't even offer the choice of 'if you want to Install side by side with windows'.  Using a separate partition is always safer and easier for new users-IMO.  Once you learn how to partition, installing is a snap, and using the os is enjoyable.  But we have to learn how to partition unless we simply use a separate disk.  Windows does not like to share its space and with large disks, it shouldn't have to.

---

### Post by randomname9438 on 2011-12-14
Hello Forum,

I'm new to all this, but I've done enough research to determine how I want to setup my hard drive and the partitions for my installation(s) but I am running into a problem that I am unsure how to fix...

Basically, I four partitions...

Pt.1 - Win7 (50GB)
Pt.2 - Ubuntu (50GB)
Pt.3 - Swap (8GB)
Pt.4 - Storage Space (Remaining Space) 

I want Pt.4 to be a mutual partition for both Win7 and Ubuntu to use for my documents, pictures, videos, etc. 

What would be the best arrangement(s) for these as well? Win7 will go first, but how should I create/arrange the other three?

Thus far, I have most of the help I need with this. My problem is in trying to get these laid out BEFORE installation so they are the right sizes, etc. 

Due to my recovery discs, I have limited installation options for Win7. To begin, I'd have to insert the discs, tell it to create and install to a 50GB partition, and go from there. No help needed.

Once I get ready to start the Ubuntu installation, if I navigate to the "advanced partitioning tool" so I can create these areas accordingly, I run into errors regarding mount points, boot, etc. I am unsure how to create these manually, thus, I would like help from someone in what exactly to do so I can create the remaining three partitions, install Ubuntu accordingly, swap, and then I can copy over my personal files, etc. etc.

So... would anyone be kind enough to explain step-by-step how to use the advanced partitioning tool (in terms of the options for mount, boot, root, whatever...)? Or, point to another guide. I did some digging but wasn't sure exactly what key words to use. 

Thanks in advance!

---

### Post by oldfred on 2011-12-14
Often best to create your own thread if you have specific instructions.

It has been pretty well discussed in the previous comments. But if you want screen shots these show the process in detail. Sceens only have minor changes from most versions to another, as the install process is the same. 

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by randomname9438 on 2011-12-14
THANKS! 

I don't mind following other guides, sometimes though, it's more of a matter of not knowing what to search for. I'm quite familiar with Windows I think, and I've used gParted several times but I'm used to being able to create the partition and go - the other options of mounting points or what not is new for me. 

Again, thanks! I appreciate the help. The guides answered the "in between" questions that I had. I've done the dual boot setup a few times with no problems, it was just a matter of tweaking it to how I wanted to make it run personally.

---

