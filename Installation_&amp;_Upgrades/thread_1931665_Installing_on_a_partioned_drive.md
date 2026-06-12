---
title: "Installing on a partioned drive"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by racsw on 2012-02-25
Hello,
I read the Installation manual a couple of times on this question, and I'm still confused, maybe there were too many alternatives, I'm not sure.  But unless I understand the procedure completely, I won't continue, because I can't afford to lose my installed Win 7 system.

Here's the status.
I've got one of these small NoteBook computers with embedded AT&T I use for traveling on my motorcycle.

  At any rate, it came partitioned with approx 140 Gb HD, 60 GB contains the Win 7 OS (Drive C:), and 75 GB for Drive D:.  There was nothing on the D: drive at all, but both are formatted for NTFS. When you buy the Notebook, for whatever reason, they do not give you a CD with the OS, so you can't reinstall it if you screw it up or lose it.  Makes no sense to me, but whatever...

  Very simply, I have experimented with Ubuntu 11.10 on a USB Stick, and would like to install the system on the D: partition.
I don't believe Ubuntu can work with the NTFS system, but needs it formatted some other way.  (ReiserFS, etc)

So I guess I don't know how to do this and preserve the C: drive and it's contents.  As I said earlier, I can't reinstall the Win7 system, so I have to be careful.
  When the Ubuntu Installer opens up, it gives you a variety of choices, and frankly, the choices are confusing in so far as it doesn't clearly state which one is the one to use in a case like mine.

One question I remember that is also confusing is that it wants to know where to put the boot loader (I believe that is what it said) with a bunch of choices.  I don't know what to pick, especially since I'm not familiar with the Win7 OS, I don't know where things are supposed to go.  Obviously, the computer goes to a specific location on the C: drive to get the boot instructions, so this is probably where this boot loader should go.  I don't know where that is, or how to find it.


So I could use someones expertise here who would have the patience to hang with me a bit so I do this right.  

Thank you,
Robert

---

### Post by darkod on 2012-02-26
1. Concerning any possible restore of win7. Usually there would be a partition on the hdd which may be hidden and not showing in Computer. If you open Disk Management you can see all partitions, including one small called System that usually has win7 boot files on it. Again, it's also hidden and not showing in Computer.
Also, usually there is an option to make a set of restore DVDs using the backup/restore software that came on the machine.
My personal opinion about this restore partitions and DVD sets is that they are worthless. But since MS started not shipping OS media, it leaves you little choice. I consider them worthless because what it usually does is restore your computer to the factory setup, meaning you will lose all data, programs, settings, etc.
Imagine this, you have your win7/ubuntu dual boot working fine. Then suddenly win7 gets a broken system file and stops working. If you use the restore approach, it will delete your ubuntu partitions and all data there, your current windows data and programs, and you end up with exactly the same computer you bought, without anything you did meanwhile.
So, for one corrupted file you lose everything. Some help, ha? On the other hand, without install media, what choice do you have? So, in any case, be very careful when using any restore option, and investigate the consequences first.

Now back to your issues...
Correct, linux will not install on ntfs, it needs its own filesystem. If you want to use the total size of partition D: for ubuntu, simply boot windows, open Disk Management and delete D:. Leave the space as unallocated.
When you boot the ubuntu cd and start the install, you will have two options: to install with the auto method telling it to use the unallocated space, or use the Something Else manual method and create your own partitions from the unallocated space. I prefer the manual method because it gives you greater control.
In case you do it manually, you need:
root system partition, filesystem ext4, logical, mount point /
swap partition, filesystem swap area, logical, (doesn't use mount point)
(optional) separate /home partition, ext4, logical, mount point /home

Decide how you want to split the size between them. For swap you need about 2GB but if you plan to hibernate you need 1.5 x size of RAM.
All the rest can go to / if you don't use separate /home.
If you use separate /home, give about 10-15GB to /, all the rest to /home.
For bootloader (grub2) installation select the MBR of the disk, which would be usually /dev/sda. It SHOULD NOT have a number in it. The number means partition number, without any number is the MBR.

That's it.
Any questions, ask first. You're doing the right thing asking first.

---

### Post by racsw on 2012-02-26
Darkod,
Thank you for taking the time for this.
I'll start with two things.

1.  There is nothing that I can find called "Disk Management" on this computer.  I checked under "Computer" and "Control Panel".  I guess I could have missed it, but if you could be more explicit, I'll follow your instructions.

2. If I manage to find the spot where it partitions the disk so that I can delete drive D: am I taking the right approach?  If I take your suggestion and use all available disk space, won't it do exactly that?   Another words, I won't be able to add any more files to the C: drive and the Win 7 system.

Because I have about 75 Gb for Drive D: available, I could, if you thought it better, just allocate 60 GB for the Ubuntu system, although I'm not sure how to do this.

There is a spot that is 100 MB that is called the MBR. (Master Boot Record), although it doesn't tell me where it is located.

Just FYI, there is no CD on this computer.  The only way for me to install Ubuntu is to use the 8GB USB Stick that has Ubuntu on it now.  It has a selection on the desktop screen to install it on your computer, either to replace the Windows system you have now, or "Other", which gets into the partitioning stuff and choices I am not sure of.

But maybe for now if you could direct me to this Disk Management selection, at least I can be on the same page.

Robert

---

### Post by darkod on 2012-02-26
Hit the windows logo key on the keyboard. In the start window that shows, the cursor is already located at the bottom where it says 'search for programs and files'.
Start typing "disk mana" and above it will show option Create and format hard disk partitions. Open that.

Whether deleting D: is a right approach only you know. You definitely need to delete it, especially if it's empty as you say. But not all of the space needs to be allocated to ubuntu.

After you delete D:, you can expand C: to take part of that unallocated space, as long as they are next to each other. The expand (or shrink) can also be done in the same Disk Management tool.

It's your choice how much space you want to leave unallocated for ubuntu, and how to organize your disk. But note that you will need a minimum of 20-25GB for ubuntu (in total for all partitions) and that's if you don't save large files there.

Also take into account that win7 will not be able to see the linux partitions so that space is like unusable for it. Ubuntu on the other hand can read and write to ntfs without problem.

---

### Post by racsw on 2012-02-26
That was pretty cool.. (Disk mana)

I attached the pic of my disk layout for clarity.


Tell me if this is right, I'm restating it so I know I am understanding what you said:

  If I delete D:, that leaves C: as an NTFS system, but now designates the space (70.36GB) as "Unallocated", meaning (I think) that this space is not formatted for any file system.

Won't it still list it as D:?

Another question:  How do we find out where the boot script goes?
It shows a 20MB space, and a 100Mb space, but it doesn't say what it's for or where it is.  I assume one of these is where we will need to put the boot script.

---

### Post by darkod on 2012-02-27
Partition #1 is the recovery partition, it clearly says so.
Partition #2 is the 100MB small System partition with the win7 boot files. You need this to boot win7 correctly. Never delete it.
Partition #3 is your win7 OS partition, C:
Partition #4 is your D: partition.

Windows assigns letters to partitions it can recognize (and calls them drives by the way). So, when you delete D:, you are right, it will convert into 70GB of unallocated space with no partition on it, or filesystem. Automatically with this win7 will not assign D: to it any more.

If you want, you can expand C: into part of that space, if you don't want to use the whole 70GB for ubuntu as we already said.

What boot script are you referring to? The bootloader for ubuntu, grub2? If that is your question, it will go to the Master Boot Record of the hdd, in linux terms it's /dev/sda.

---

### Post by oldfred on 2012-02-27
You can make a recovery set of DVD's from the recovery partition. But as Darko says it is not worth much. The only use I might think is if someday you wanted to sell computer and the buyer wanted Windows and you wanted to then reinstall to as purchased.

Any changes to system have some risk, good backups then become important.

You can make a recovery USB and repair USB if you do not have CD/DVD.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

This discusses dual booting with Windows (not much on Linux) but shows how MBR computers boot. The MBR is just the first sector of the hard drive that is before the first partition. This is detailed but just review pictures to understand the basics.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by racsw on 2012-02-29
You guys have been great help.  All that info is indeed helpful.
I've been down mostly due to sickness, but I'm pretty much back to form, and will work on this tomorrow.

The computer isn't much, and is pretty slow as I said in the beginning, and I've always been able to increase the speed by taking an older PC and installing Linux, in various flavors.
So that's the motive behind adding Ubuntu as an alternate OS.
  It would have helped I think if they would have given me the choice of XP or Win7, but that was not the case.

I'll try deleting the D drive tomorrow, then expanding the C drive a little.  My memory sucks, but I recall that any partitioning changes you make deletes the information on any active partition, I hope I'm mistaken.

If I haven't lost everything at that point, I'll install Ubuntu.

The reason I included the pic of my HD partitions was to nail down where the boot loader is to be installed (Grub).  It asks you that in the installation, and I didn't want to put it in the wrong place obviously.  But Darko said to put it in the second partition. (100 Mb)

So we'll see what happens.  I have everything backed up with Carbonite, which works well, but isn't compatible with Linux unfortunately.  I have a Black Armor 500 Gb HD portable that I will make a second backup, but it won't back up the Win7 system.

I can't make a backup system CD or DVD, because it doesn't have one, only a USB.

Cross my fingers I guess.   If things go South, I guess I will be able to install Ubuntu from the USB.  (That will make the wife happy :-( )

Give me a day or so, I'll get back and let you know how it worked.  Thank you again guys.

Robert

---

### Post by racsw on 2012-02-29
I found this information on that MBR question of mine:

*************************************************
Most installations of Windows 7 include a tiny 100 MB partition named 'System Reserved'.  This is also known as the MSR or “Microsoft System Reserved' Partition. For brevity I'll refer to this partition as  MSR throughout the rest of this article.

Note: Some OEM installations may name this partition 'System' or even 'Recovery'. In all cases it will be the 'Active' partition on the same disk as drive 'C'.

Have I got an an MSR partition?

Some OEM installs of Windows 7 don't include the MSR partition. To check whether you have this partition start up Macrium Reflect and look for a 100MB partition on the system disk named 'System Reserved'.

Note: If drive 'C' is your 'Active' partition you just need to backup and restore 'C' for full system recovery.

What does the MSR partition do?

The MSR partition handles the second stage of the boot process after the Master Boot Record (MBR). The MBR resides on the first sector of the disk and is loaded at system start-up, after loading control is passed to the partition boot sector code of the active partition, this is the MSR partition if it exists, if not it will be your 'C' drive. The MSR contains a  '\boot' directory that contains the Boot Configuration Data (BCD). The BCD controls the  next stage of the boot process and loads the Operating System  from drive C:.

The MSR partition is always the 'Active' partition on your system disk and should be restored as the 'Active ' partition. The contents of this partition doesn't change and, by default, isn't assigned a drive letter by Windows so you can't modify it.
*****************************************************

The reason I included this is because perhaps the Boot script should really go on the first partition instead of the 2nd one?

Question:  How do you access those areas like Partition #1 & #2?

---

### Post by oldfred on 2012-02-29
In Linux partitions are sda1, sda2, sda3 etc. partitions from sda1 thru sda4 are primary and sda5 or up are logical. One primary partition can be converted to the extended partition which then is just a container for all the logical partitions.

Darko was very clear that you install to sda not sda1 or sda2. It looks like sda1 is a recovery, sda2 is the Windows (hidden) boot partition or MSR since it is 100MB and has no label like c: or d:. It also lets you run repairs using f8, but if it is damaged then only a Windows repairCD or USB will then fix it.

A Windows boot partition will have nothing to do with Ubuntu and is not a Linux boot partition. If you try to use it for anything from Linux you may corrupt it and then you need the Windows repairCD/USB.

There is one sector at the very beginning of all drives that is the MBR or master boot record. You install grub to the MBR of sda. Grub will then create a chainload entry to the Windows boot partition or MSR to boot into Windows.

Actually the active partition in Windows terms is the partition with a boot flag and is the MSR. Windows boot loader is always in the active or boot flagged partition.

Article is pretty long and detailed, but just reviewing pictures gives some useful info:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by racsw on 2012-03-01
Well, all is going OK at the moment :-)

I deleted D: as instructed, then extended C: to give it an extra 20 GB.  Nothing blew up...

I had a little memory trouble with the partitions (my memory, not the computer)
I used to know all the partition sizes, percentages of each, etc, but those brain cells are extinct.
So without a guide, I simply made 10Gb a swap space, and the rest as "/".  It wanted me to create a swap space, and i didn't know how much to allocate, so i guessed.

Question:  I see Ubuntu now comes with the LibreOffice.  Seems odd.  The normal one to install for years was Open Office, which was free as well.  Why wasn't that used?  It certainly has been out for a long time, from a development standpoint.

So If someone will answer that question, I'll sign off this thread.

I really cannot thank you enough for your patience here, and all your help.  For all the years I played and programmed computers (from 1980), I can't believe something like this makes me so nervous.  That's what happens when you get old I guess...

Thanks again,
Robert

---

### Post by darkod on 2012-03-02
Open Office was bought by Oracle and it seems there was some difference where should it go. Maybe even some doubts whether it will always be free.
So Libre Office was created as alternative, although I can't really be sure how long it will be free either.
At the moment, they are both free. :)

---

