---
title: "Dual Boot Ubuntu and XP"
date: 2005-02-09
forum: Installation &amp; Upgrades
---

### Post by mhancoc7 on 2005-02-09
Ok this is my first post. I am a Linux newbie so please be gentle.

I was given the Ubutu cds by a friend. I decided that I wanted to setup a dual boot system on my laptop. I tested the Live CD and it worked fine. So I ran the install and it went perfectly. I set it up to install Ubuntu to a 40 gig external hard drive. When the install was compete I was prompted to remove the install CD and the computer would reboot. After the reboot I get the following error.

    GRUB Loading stage1.5.


    GRUB loading, please wait...
    Error 21

Now I can't get my coputer to boot at all. I just get the error and the laptop stops there. I have searched the internet including this forum and have found a few possible solutions. The problem is the solutions require me to enter the BIOS. I can't get into the BIOS. I have tried F10, F2, and just about every key on the keyboard at boot up and I can't find a way into the BIOS.

Here is my system:
Compaq Armada 1750 (winxp)
Fujitsu External Hard Drive

Can someone please help me get this going. At this point I would settle for just getting my laptop back to just boot into Windows and I can format the extenal hard drive and try this all later. Of course I would prefer to get the dual boot working.

Thanks in advance for any and all help, Jereme :smile:

---

### Post by lao_V on 2005-02-09
Jereme, different BIOS has different keys to enter into the BIOS setup. Yours should say it when you switch on your laptop. When you are booting into your system, is your external harddrive connected?
 
 You may already know this but if you want to have a dual boot system with win xp make sure you install xp first and then linux otherwise xp will erase everything from MBR!

---

### Post by mhancoc7 on 2005-02-09
Hi,
Thanks for the quick response.

I did install XP first. It was already running on the laptop.

Yes the external drive is connected.

When I boot up the laptop I get the Compaq screen. It then goes to the screen that says GRUB Loading stage1.5. Then I get the error 21. Before I installed Ubuntu the laptop would first show the Compaq screen and then the Windows XP screen with no mention of which key to press to enter the BIOS. I had the same issue on my desktop once and it took forever to figure out which key to press. I have tried every key that I can think of and all the have been suggested and still can't get in.

Thanks, Jereme

---

### Post by lao_V on 2005-02-09
Have you tried ESC or DEL key. I will check out my compaq laptop when I get home and let you know for definite (if you don't get a reply by then!)

---

### Post by mhancoc7 on 2005-02-09
Yes, I have tried Esc, Del, F10, F2, F5, ...

Maybe I am just not quick enough. I will have to try it out some more.

Thanks, Jereme

---

### Post by lao_V on 2005-02-09
Jereme, something I found on the net. Not sure how accurate this is as I've never had an armada:
 
  > The armada 1700's didn't have inbuilt BIOS settings for setup etc...it had to be installed on the hard drive or run from a floppy disk. 
If it is installed on your hard drive you can run the bios setup by pressing F10 when you notice a cursor in the top right(?) corner of the screen shortly after turning the unit on.
Otherwise you'll have to download the setup from [www.compaq.com](www.compaq.com) and put it on a floppy and run it from there; the floppy created is bootable so your laptop should go straight into the setup. 
 
 on [http://www.askanowner.com/qa/view.asp?s=1&qid=63300](http://www.askanowner.com/qa/view.asp?s=1&qid=63300)

---

### Post by mhancoc7 on 2005-02-09
Thanks!

I am getting closer. I know have Set up disk and a Diagnostics tool disk. I have ran the set up disk, but I can't find what I need to change. The advise that I gotten from another forum is the following:

Enter Standard CMOS Setup

set the Primary Master to:
   Type = User, Mode = LBA
by scolling through the options

then set the Primary Slave to:
   Type = Auto, Mode = Auto

I can't find anything that will let me do this in the set up disk. Am I looking in the wrong place. Remember I am a newbie so any guidance will be greatly appreciated.

I tried to install the set up from the set up disk, but it tells me that I do not have enough room to put the necessary Diagnostices Partition.

Thanks, Jereme

---

### Post by lao_V on 2005-02-09
Jereme, are you able to get into BIOS from the setup disk you have? Usually its a blue screen. Here you are able to change the system settings (time, boot-up sequence etc)

---

### Post by mhancoc7 on 2005-02-09
Well I get a screen that lets me Run Computer Setup or Install Computer Setup.

When I click Run Computer Setup I got to a Computer Setup screen with a nice GUI. I have several options. System Features, Communication, Storage, etc. I click System Features and then Boot Management. It gives me three options, Enable NumLock on boot, Disable diskette boot ability, and Enable QuickBoot. It also has a tab for MultiBoot which lets me Enable MultiBoot and rearrange the Boot order of the CD Rom, Hard drive bay, and the Multibay. I am in the BIOS or am I doing something wrong. I have had to get into the BIOS of my desktop before and this is not at all what I saw.

Thanks, Jereme

---

### Post by macmils on 2005-02-09
The easiest way to fix this should be to boot on an XP cd, go in to a rescue mode, if possible drop to a command prompt and type fdisk /mbr to restore the WindowsXP boot record.

The problem sounds as though GRUB can't find it's second stage installer (stage1.5) as it's on the external hard disk and grub see's the disk mappings for finding the /boot partition differently at boot time than when the system is running. 

Is this an external USB hard disk?

---

### Post by mhancoc7 on 2005-02-09
Well that's another issue. I don't have the Win XP cd. I bought the laptop on Ebay and it did not come with the disks

Yes it is a USB external hard drive.

Is there anyway to fix this without the XP disk?

Thanks so much, Jereme

---

### Post by macmils on 2005-02-09
The only way I can think of off hand is to boot off the Ubuntu cd and if there is one, go in to the rescue mode (I don't actually know if there is one) and try:

grub-install /dev/hda

then reboot. With a bit of luck you boot in to a grub prompt.

From there you would only need to type:

rootnoverify (hd0,0)
chainloader +1
boot

and WindowsXP would start


As another thought, do you have a friend who could make an XP rescue floppy for you? You might get fdisk on that.


If you had a knoppix livecd, you could boot on that, resize your windows partition to give enough room to create a linux partition to be used as boot, create the linux partition and then install grub on to that.

---

### Post by macmils on 2005-02-09
[QUOTE=macmils]The only way I can think of off hand is to boot off the Ubuntu cd and if there is one, go in to the rescue mode (I don't actually know if there is one) and try:

grub-install /dev/hda

then reboot. With a bit of luck you boot in to a grub prompt.

From there you would only need to type:

rootnoverify (hd0,0)
chainloader +1
boot

and WindowsXP would start


As another thought, do you have a friend who could make an XP rescue floppy for you? You might get fdisk on that.


If you had a knoppix livecd, you could boot on that, resize your windows partition to give enough room to create a linux partition to be used as boot, create the linux partition and then install grub on to that.[/QUOTE]


Okay, I've just checked and on the Warty 4.10 install cd there isn't a rescue mode (that I could find).

If you have a copy of the livecd, you could boot on that, open a terminal, sudo su - , then try /sbin/grub-install /dev/hda

---

### Post by mhancoc7 on 2005-02-09
Ok I booted up using the Ubuntu LiveCD and typed into Terminal /sbin/grub-install /dev/hda. I get the message cannot create directory '/boot/grub" : Permission denied.

I do have the Knoppix LiveCD as well.

I have a Recue Disk for my Dell desktop that runs WinXP. Can I use it to get into the BIOS on my Compaq laptop?

Thanks, Jereme

---

### Post by macmils on 2005-02-09
Okay, it was worth a go.


I don't see that you need to get in to the BIOS of your laptop to fix this. The problem exists on the Master Boot Record of your hard disk. Grub has installed itself on it, but can't find it's secondary files that exists under /boot/grub which it needs to run. Those files were installed on to your usb Hard Disk. 
Because it can't find those files, unless you can make the BIOS recognise your USB device as an external disk or boot device, the same as the linux kernel saw it when it  installed, the boot record will remain corrupt. Not all BIOS's can use USB as a boot device.

To fix the problem either:-

From your Dell PC create a WinXP rescue disk, boot on it and run "fdisk /mbr". You may have to copy the fdisk program from your PC to the rescue floppy aswell.
This will create a Master Boot Record that can launch windows.


Secondly, boot knoppix, use qtparted or parted from under it's menu system and resize you windows partition to leave as much space as you can for a linux install on your internal hard disk. Reboot and install Ubuntu or any version or linux using the free space on the internal hard disk. Now you can configure the dual boot loader. 

Hope that helps.

---

### Post by mhancoc7 on 2005-02-09
Ok so I will be installing Ubuntu on the partition that I create on the Primary hard drive. Can I then access the external harddrive from both WinXp and Ubuntu? If I am able to do what you said then I am going to also partition the external drive into two 20gig partitions. Can I then access them by both Winxp and Ubuntu? I hope that I am making sense. The reason that I ask is because I eventually wanted to test out using Win4Lin under Ubuntu to run Windows 98se. And the plot thickens... ha ha

Oh yeah, how do I create the Rescue disk?

Thanks, Jereme

---

### Post by macmils on 2005-02-09
Yup, once ubuntu is installed and you plug in the USB drive it will automount the partitions. You'll want to delete these and create new ones. (Use fdisk as root)

If you want Windows to be able to access them aswell, then using Ubuntu create vfat partitions with fdisk and toggle the type to 'b' (W95 FAT£"), and formart them with "mkfs.vfat -F 32 /dev/<device partition>. (You'll need to be root to do).

Ubunut and Windows will recognise these and allow read / write access.

As for the rescue disk, I havn't used Windows for a while so I don't know off hand how to create the disk, but I'm sure I've done it in the past. 
I personally would do the repartitionng with knoppix and do it that way.

---

### Post by mhancoc7 on 2005-02-09
[QUOTE=macmils]Yup, once ubuntu is installed and you plug in the USB drive it will automount the partitions. You'll want to delete these and create new ones. (Use fdisk as root)

If you want Windows to be able to access them aswell, then using Ubuntu create vfat partitions with fdisk and toggle the type to 'b' (W95 FAT£"), and formart them with "mkfs.vfat -F 32 /dev/<device partition>. (You'll need to be root to do).

Ubunut and Windows will recognise these and allow read / write access.[/QUOTE]


Ok, that went a little over my head, but at least I know that it is doable. First I jsut need to get the MBR back to boot up windows. Then I will add the partition necessary to install Ubuntu to the Primary hard drive and then I will tackle the rest.

How do I go about creating the Rescue Disk. I know that my Dell Desktop came with a Rescue CD will that work? 

Thanks so much for your help!! Jereme

---

### Post by macmils on 2005-02-09
[QUOTE=mhancoc7]Ok, that went a little over my head, but at least I know that it is doable. First I jsut need to get the MBR back to boot up windows. Then I will add the partition necessary to install Ubuntu to the Primary hard drive and then I will tackle the rest.

How do I go about creating the Rescue Disk. I know that my Dell Desktop came with a Rescue CD will that work? 

Thanks so much for your help!! Jereme[/QUOTE]
 I don't know off hand how to create one from Windows, it's been a loooooooonnnnnnnggggg time since I've had to. You might be able to use you Dell rescue CD, but be carefull, it might only restore on a dell system, of blank your entire hard disk and reinstall windows.

I would use the knoppix approach myself but that could be a bit daunting.

S.

---

### Post by macmils on 2005-02-09
Here's a URL to a howto that might help


[http://www.hut.fi/~tkarvine/linux-windows-dual-boot-resizing-ntfs.html](http://www.hut.fi/~tkarvine/linux-windows-dual-boot-resizing-ntfs.html)


Just ignore the bit about Fedora and redo the Ubuntu install instead. Make sure that when you install Ubuntu, you don't do the whole disk, and only add partitions the free space that you crated with the resize.

---

### Post by lao_V on 2005-02-09
To create a rescue/MS DOS startup disk do the following on your WinXP machine.
 
 
[list]
[*]Insert a floppy drive   
[*]Open Explorer   
[*]Right click on floppy A:\ and select format   
[*]tick the box for MS DOS startup disk. 
[/list] You may have to copy the fdisk program manually from the windows or system32 folder

---

### Post by mhancoc7 on 2005-02-09
How about this, I have enough space on the Primary Hard drive to do a minimal Ubunu install (350 MB). Could I go in now and with the Ubuntu Install CD and install the minimum install to the Primary Hard drive. Would the grub be then set to dual boot correctly? And then if so I could format and partition my extenal hard drive to be used by WinXp and Ubuntu. I could also delete a bunch of unused applications from the Primary Hard drive and reinstall the full Ubuntu (1.8GB) to the Primary Hard drive.

Thanks, Jereme

---

### Post by macmils on 2005-02-09
I doubt it. Windows usually allocates all the free space of the Hard Disk to it's own partition and sets it to a NTFS of FAT type. Ubuntu and nearly all linux distros require linux partitions creating, which Windows dosn't recognise.

The chances are that you may have free space on the hard disk when your in Windows, but it's in the Windows partition. Again repartitioning would be needed. On the other hand if there is free unallocated space on the hard disk, then yes should be able to do a minimal install, but you wouldn't get all the benefits of the stanard apps installed by Ubuntu.

---

### Post by mhancoc7 on 2005-02-09
Can I use the Ubuntu Install CD in expert mode to create a partition on the Primary drive for the Ubuntu install or do I need to do this with the Knoppix live CD?

I made the MS-DOS Startup disk. Thanks, lao_V. Now when it starts it starts at A:\. What do I need to do from there to run fdisk/mbr?

Thanks, Jereme

---

### Post by macmils on 2005-02-09
[QUOTE=mhancoc7]Can I use the Ubuntu Install CD in expert mode to create a partition on the Primary drive for the Ubuntu install or do I need to do this with the Knoppix live CD?

I made the MS-DOS Startup disk. Thanks, lao_V. Now when it starts it starts at A:\. What do I need to do from there to run fdisk/mbr?

Thanks, Jereme[/QUOTE]
 Once repartitioned, the Ubuntu install will ask you how you want to create the partitions and do it for you.

fdisk c: /mbr 

or 

c:
fdisk /mbr

is the command your looking for.

---

### Post by mhancoc7 on 2005-02-09
[QUOTE=macmils]Once repartitioned, the Ubuntu install will ask you how you want to create the partitions and do it for you.[/QUOTE]

So are you saying yes I can repartition my Primary Drive using the Ubuntu Install CD in expert mode. If so I want to be sure I know what I am doing so I do not lost the data on the Primary Drive.



> fdisk c: /mbr 

or 

c:
fdisk /mbr

is the command your looking for.

Is this for the MS-DOS startup disk. I tried it and I get Invalid drive specification.

Thanks again, Jereme

---

### Post by macmils on 2005-02-09
[QUOTE=mhancoc7]So are you saying yes I can repartition my Primary Drive using the Ubuntu Install CD in expert mode. If so I want to be sure I know what I am doing so I do not lost the data on the Primary Drive.





Is this for the MS-DOS startup disk. I tried it and I get Invalid drive specification.

Thanks again, Jereme[/QUOTE]
 No, I was saying you can create the new partitions using Ubuntu, not resize the existing Windows partitions if thats what your asking.

If the fdisk command isn't working it sounds like the existing partition maybe a NTFS partition. I've seen theres another thread recommending booting on an XP install CD and using the rescue console to fix it, but I know you havn't got that :(

---

### Post by mhancoc7 on 2005-02-09
I just checked out your link for the Fedora Linux and WinXP resizing and dual boot. That looks pretty straight forward. If I read it correctly I can resize my current Primary Hard drive and create FREE space for the Ubuntu install. If that's the case that is going to be tonights project.

The one problem that I have is that I can't resize my Primary hard drive to leave enough space for a full Ubuntu install, but I can make enough for the minimum install. I just hope that once I do that I can log into Windows from the Grub Menu and clear up some disk space and then reinstall the full Ubuntu over the minimum install. 

Does that all sound feasible.

Thanks, Jereme

---

### Post by macmils on 2005-02-09
[QUOTE=mhancoc7]I just checked out your link for the Fedora Linux and WinXP resizing and dual boot. That looks pretty straight forward. If I read it correctly I can resize my current Primary Hard drive and create FREE space for the Ubuntu install. If that's the case that is going to be tonights project.

The one problem that I have is that I can't resize my Primary hard drive to leave enough space for a full Ubuntu install, but I can make enough for the minimum install. I just hope that once I do that I can log into Windows from the Grub Menu and clear up some disk space and then reinstall the full Ubuntu over the minimum install. 

Does that all sound feasible.

Thanks, Jereme[/QUOTE]
 That sounds like the thing to do.

Once you've got a minimal Ubuntu install completed you'll need to look at how to add the dual boot options in to grub (Hint: the commands I listed a while back should help a little), but it sounds like you'll have a fun night ahead.

Good luck and I hope it goes well.


S.

---

### Post by mhancoc7 on 2005-02-09
Thanks so much for your help. :grin: 

I will hopefully get it all fixed up tonight and if so I will let you know.

Thanks, Jereme

---

### Post by thestarman on 2005-02-09
[QUOTE=mhancoc7]Well that's another issue. I don't have the Win XP cd. I bought the laptop on Ebay and it did not come with the disks

Is there anyway to fix this without the XP disk?[/QUOTE]

Jereme,

    Hate to point out the obvious, but unless the seller shipped you an official Microsoft certificate for that install, then he sold it to you illegally and you are illegally using that OS and just told everyone here.

    To fix it:  You won't get exactly the same code as you would from the XP install CD's  'fixmbr' command, but if you can locate a Windows 98/98SE (not Millenium Edition!) boot diskette and go to a simple A:\> prompt.  ENTER:  fdisk /mbr 
    That will replace the GRUB code in your MBR sector with the standard MSWIN4.1 MBR code which is plenty good enough to boot up any Windows OS with!   GRUB shouldn't have changed anything in your Partition Table which is why this works more than 99% of the time for such a problem.

Daniel.

---

### Post by mhancoc7 on 2005-02-10
[QUOTE=thestarman]Jereme,

    Hate to point out the obvious, but unless the seller shipped you an official Microsoft certificate for that install, then he sold it to you illegally and you are illegally using that OS and just told everyone here.

    To fix it:  You won't get exactly the same code as you would from the XP install CD's  'fixmbr' command, but if you can locate a Windows 98/98SE (not Millenium Edition!) boot diskette and go to a simple A:\> prompt.  ENTER:  fdisk /mbr 
    That will replace the GRUB code in your MBR sector with the standard MSWIN4.1 MBR code which is plenty good enough to boot up any Windows OS with!   GRUB shouldn't have changed anything in your Partition Table which is why this works more than 99% of the time for such a problem.

Daniel.[/QUOTE]

Well, the seller on Ebay mentioned a Certificate when I purchased it. When I got the laptop it had a Product Key sticker on it and was labled as a certificate. 

I was finally able to get my laptop back up and running using a WinXP setup boot disk that I downloaded from Microsoft. I tried fixmbr from the Rescue mode and that did not work so I tried fixboot and it worked perfectly. Now it logs right into WinXp. The only thing that I can't get to work now is the 40gig external hard drive. WinXp does not recognize it. So now to fix that. I will be trying to do the dual boot later, but for now I will just be glad that I didn't lose anything or fry my laptop.


Update/Edit: I was able to get my external hard drive working. Just needed to go into disk management and set up the drive letter and then format.

Thanks to all your help!!

God Bless, Jereme

---

### Post by lao_V on 2005-02-10
Jereme,
 
 WinXP doesn't recognize anything that's not FAT/NTFS. I've mentioned this elsewhere on this forum, if you really want multiple operating system on your PC (specially with Windows on the main partition) then use VMWare workstation.
 
 It doesn't partition anything and you can install/delete as many OS as you like without having to worry about boot issues.

---

