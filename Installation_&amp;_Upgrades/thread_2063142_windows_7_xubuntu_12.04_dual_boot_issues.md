---
title: "windows 7 xubuntu 12.04 dual boot issues"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by Jpendragon on 2012-09-26
A problem forced me to reinstall xubuntu. When I did, GRUB threw a hissy fit and was like "oh my  god, I don't know what's going on!" so I tried every combination of  reinstalling things like grub and the swap space, ect. Finally I just  started from scratch and reinstalled windows. Then I followed [http://www.linuxbsdos.com/2012/05/17...and-windows-7/]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/")  <<this person's instructions on how to get it to dual boot  (although I shrunk the windows partition in windows and then added a  FAT32 partition in Gparted to be my data partition). But when the  installation was over, and it asked to restart my computer, it restarted  into Xubuntu, not Windows (he predicted Windows).

I can access windows by pressing esc on the brand-name screen of my computer and navigating to the boot menu, where it gives me an option to boot windows or xubuntu (although it says ubuntu). How though do I get it to give me a menu (like grub used to, or like this guy says you can convert windows boot loader to)?


(((And side note, how do you tag old threads as [SOLVED], because I've never figured it out.)))

---

### Post by oldfred on 2012-09-26
Post link to BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

And see link in my signature.

---

### Post by Jpendragon on 2012-09-27
Okay, I'm kinda sick of everything that's been complicating this. And I'm really confused and tired of trying to guess at all these things and f***ing up my harddrive. I don't care about the data or the partitions on my computer right now; they aren't working, and everything important has been backed up.

I want to dump everything on my drive and start over.

This is the configuration I want.

I have a 1Tb drive. I want to devote:
25% to Windows 7 Ultimate 64bit 
10% to Xubuntu 12.04 (Unless there is a new, non-beta version)
65% to an extra partition that both windows and xubuntu can read/write on.

With two partitions for windows (the 100Mb system partition and the main one)
I want the /home folder on a separate partition for xubuntu, so with the boot partition and the swap partition (5 gigs), that will be four partitions
And then one partition at the end.
So a total of 7 partitions.

I want it so that either GRUB or (preferably) Windows Boot Loader to pop up when I turn on the computer and ask me whether I would like to run Windows 7 or Xubuntu.

I have a few concerns as well:
A past problem that occurred caused me to have old partition data interfering with new installations. I would like to avoid this because using fixparts was complicated and I don't remember how I did it.
Also, when I installed windows last time, and tried to shrink the partition, it wouldn't let me shrink it past 50% of the drive because of an immovable file, I will NEED for Windows to take up less than that amount of space, so I assume Windows will need to know ahead of time that it only has 25% of my drive to work with.

Please, if someone could give me step-by-step instructions on how to do what I want to do, that would be amazing. I know that it is asking a lot, but I've been working on partial advice and googling, and guessing this whole time, and it's just led to screw up after screw up and post after post on this website. This is literally the fifth post in a month I've had to make for this problem. I don't want to be coming back a week later. If this problem is solved, I am unlikely to have real problems for a very long time and I may finally be able to stop pestering you and leave you all alone.

---

### Post by oldfred on 2012-09-27
Windows default install is the two partitions with the first 100MB as a  boot/repair partition. But if you create the NTFS partition in advance with the boot flag, it will just install to one partition. The main reason for two is so you can encrypt your main partition. A second reason is that you may be able to get into your repair partition, when the main partition needs repairs. But just create the Windows repairCD or USB and install Windows 7 to one NTFS partition. That should be sda1 and has to be a primary partition.

I usually only suggest using one more primary for data which can be NTFS and shared with Ubuntu.

The third primary then is the extended partition for the rest of the drive. Note that one primary is still available just in case you need another primary, but it may be difficult to reconfigure.

Then in the extended create / (root), /home, swap and any other data partitions you might want. all as logical partitons. I like to have an extra 25GB partition or two just so I can install the next version of Ubuntu and fully test it without eliminating my main install.

My standard suggestions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
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

Update:
We have seem some issues with large drives like yours and grub2. With old systems there was a BIOS limit that systems would not boot from partitions beyond 137GB. We seem to be seeing something similar with new systems. Not sure if bug in Grub2 or a BIOS setting emulating the old issue. Make sure / is smaller, may be better to have it right after Windows c: drive, and have NTFS shared data as a logical.  Also make sure BIOS is set to AHCI. Seems to be more an issue where users install / as one very large partition so some of the grub files are close the start of the drive and some then may be way later on drive. So smaller / should also work.

---

### Post by Jpendragon on 2012-09-27
Okay.... so if I'm correct, step one would be to load a live USB of xubuntu, use GPARTED to make three partitions. Two primary as NTFS, the last one is extended into two ext4 partitions and one swap? (Two side notes, I can't figure out how to make an extended partition; is it acceptable to just make a bunch of partitions? And do I just not make a "boot" partition for grub to load itself on?)

Then install windows onto one NTFS primary.

Then install Xubuntu onto the appropriate ext4 partitions?

Will GRUB or Windows Boot Loader work then to help me choose the OS I want to use on startup?

---

### Post by Jpendragon on 2012-09-27
Gave it a shot as best I could, I created the NTFS partition and the windows installer said "Windows cannot install to this partition because it is GPT table" or something like that.

It's 64bit btw.

---

### Post by oldfred on 2012-09-27
Unless you have a new UEFI system you have to use MBR(msdos) as the partitioning. gpt is the new partition scheme which is required for drives over 2TB or with UEFI. Windows only works with gpt when using UEFI to boot.

Gparted should have defaulted to MBR with a drive of 1TB. Otherwise it is the first selection you have to make.

This screen shot is to show how to select gpt, but at the top is msdos which also is known as MBR. You need to select msdos. It is under device, create partition table, advanced. It should default to msdos.

If you just create partitions they will be primary until you create 4. Just create the first NTFS to the size you want for Windows, add boot flag and install Windows make sure it boots, do all the updates that you need and then back that up so you do not have to go thru all the updates again.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Then create the additional partitions with gparted and install Ubuntu.

---

### Post by Jpendragon on 2012-09-28
I created a new partition table. I made the one with the proper boot flag, but I never saw anything about GPT or MBR. I'm booting the Windows disk now..... Okay, it has the same complaint. I'm going to try making the partition again...

Okay, I missed it the first time. MBR is not an option though. The default was MSDOS. (Other choices: aix, amiga, bsd, dvh, gpt, mac, pc98, sun, loop.) I'm gonna leave it with the default and see what happens. I'm gonna bet it won't work though.

Trying windows disk again. This time windows boot manager appeared and asked me what to boot from the disk. Only one choice, I think it was something like Windows [EMS enabled]. It still says it can't be installed there. "Windows cannot be installed to this disk. The selected disk has an MBR partition table. On EFI systems, Windows can only be installed on GPT disks.

...

.....

*headdesk*

-EDIT-
I decided to give a GPT partition table a shot just for the hell of it.  So far there's been one difference: when managing flags, boot wasn't the  top flag. One was Bios-grub, and another started with an A.

It says "Windows cannot be installed into this hard disk space. The partition is an EFI system partition (ESP)."

---

### Post by waltclay on 2012-09-28
I also crashed my dual boot while installing xubuntu. Learn the lesson: stay away from xubuntu.

---

### Post by Jpendragon on 2012-09-28
Well then I have a couple questions for oldfred, would you suggest ubuntu as apposed to xubuntu? Would it be easier for you to help me then? Is the panel in ubuntu customizable like it is in xubuntu? If I don't like the panel being on the left and want it on the bottom like on a mac (or on xubuntu for that matter).

---

### Post by JKyleOKC on 2012-09-28
I've been following your problems from the beginning; it looks as if your BIOS setting may still be attempting to force UEFI, and your Windows installation disk isn't willing to work with that.

You might consider virtualization as a solution to your problem, since you say you want to devote only 10% of the drive to the Windows system. I've been using this solution for several years now since most of my customers use Windows but I prefer to keep all Microsoft programs quarantined here.

If you want to give it a try to see whether it would work for you, here's the outline of the procedure. I can give you step by step instructions if you decide to try it:

1. Repartition and reformat the drive giving 100 MB at the start for /boot, 10 to 20 GB next for /, the same size as your RAM plus 10% for swap, and the rest for /home. Don't worry about Windows at this stage.

2. Install Ubuntu or Xubuntu, your choice. The underlying system is the same for both but the accessories differ. Since I use Xubuntu I can only give step by step instructions for it. You might need to run Boot-Repair at this time to resolve any differences due to BIOS settings, but it should fix things easily.

3. After *buntu is up and running, go to [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) and add their site to your repository list as described there. This will keep you informed of updates and security fixes. Then download the VirtualBox package, and also the Extension kit. Install VirtualBox, then the Extension kit. This gives you the virtualization environment.

4. Run VirtualBox. It will give you a wizard for creating a virtual machine. Use it to create your Windows machine, giving it a "new" virtual drive of 100 GB or so. This will take space from your /home/you directory in the *buntu system. Set its CD drive to the physical drive of your system. When the machine creation wizard finishes you have what is essentially a second machine in which to install Windows.

5. Put the Windows CD in the drive. Then in VirtualBox, select your new machine and click the "Start" icon. It should automatically start the Windows installation into the virtual machine. Since the virtual machine is, at this point, absolutely blank with no preconceived settings, the Windows installer should not have any complaints.

6. When Windows finishes installing, install the "guest additions" from the vbox menu to make USB and folder sharing work, then restore your WIndows programs as you would normally had you booted into Windows.

Instead of dual booting, this approach always boots into *buntu initially. To run Windows, select VirtualBox, then "Start" the virtual machine. I've created a launcher on the panel to do this automatically for me. You can move data back and forth between the two systems, using vbox's "shared folders" capability, so do not need the shared data partition. And you can have both systems up on your desktop at the same time to make life even easier.

As I said, this might be a solution to your compatibility problems. While it certainly sounds a bit complicated to set up initially, it ought to be less complex than what you have already gone through...

---

### Post by oldfred on 2012-09-28
Good suggestion by    	JKyleOKC on virtualization.  I do not use it but have thought about it. I have seem many suggest that as an alternative to dual booting.

Windows will only install to gpt partitioned drives if you have a new system with UEFI. But if installing only LInux or Windows is in virtual memory you can use gpt. With gpt you do have to add a small 1MB unformated partition with the bios_grub flag.

Does Xubuntu not have gparted? Some versions do not. But you can easily download it into your liveCD or download a gparted liveCD.

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

I have Ubuntu, but installed gnome-panel which is the old style menu system. I have seen varieties of customization but do not know any details on how.

More showing background, but you can see what can be done. 
[http://ubuntuforums.org/showthread.php?t=2036126](http://ubuntuforums.org/showthread.php?t=2036126)

---

### Post by JKyleOKC on 2012-09-28
> **oldfred said:**
> Does Xubuntu not have gparted? Some versions do not. But you can easily download it into your liveCD or download a gparted liveCD.

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)Just ran "which gparted" on my Xubuntu 10.04.4 system and got no results. However I seem to recall that it's there on the 12.04.1 Live CD that I used to install my 64-bit system. And as you say, it's easy to install. Having a rescue CD available is always a good idea; my problem is that I have too many of them and cannot always find the most recent!

---

### Post by Jpendragon on 2012-09-28
I didn't see your posts when I edited this into my last post to save space. Learned my lesson. Won't do that before. I had already done this early in the morning, this was just the first time I'd told you guys.


oldfred:
-EDIT-
I gave something else a shot and it might have worked. I created an  empty MSDOS partition table and tried to install windows. My plan was to  install windows, then shrink it down to the half of the drive that it  refuses to give up, then create an NTFS partition in that extra space.  Open Gparted to mark it with boot. Install Windows to the new partition  as well, toss old Windows install. Then move on.

It said I couldn't install to the drive, that it might be incompatible,  and that I should make sure something in BIOS is active or checked or  something like that. But I happened to look at the next button anyway,  and it was clickable. (Now that I think of it, Most of the time I was  assuming it wasn't because it, said I couldn't install.

Anyway, I went through with it and before I ran updates of any kind, I  tried to shrink the partition (I thought to save time since I planned to  delete it anyway.) Well... Turns out that for whatever reason, it could  shrink it down to 20 gigs or so. I shrank it to 200. So there is the  100Mb partition, the 200,000Mb partition, and roughly 700 gigs left. Is  this compatible with your instructions? Should I next install  Xubuntu***? Or should I make the large NTFS data partition already? Or  what? 

I know I should do the mirror thing, but I don't have an external hard  drive that is large enough to be honest, I can look into one in about a  month though.

*** Still curious how you feel about the difference between xubuntu and  ubuntu though. And if it would be significantly easier for you to help  me with ubuntu. I've been using xubuntu for almost a year though. So I  am more used to its interface (as well as the customization ability of  the panel).
-/EDIT-


JKyleOKC:
Yes, I remember you and how helpful you were before. :)

I have considered a virtual machine a few times, but ultimately decided against it as I use both Windows and Linux roughly equally. (Or rather mostly Windows during the school year, and mostly Linux during break-times.) I felt my situation warranted a dual boot system rather than having one emulate the other. However, I will copy your instructions and keep your advice in mind should it seem to be the best course later. Although right now I think I'm on the right track with the dual boot.

---

### Post by oldfred on 2012-09-28
I think all the installs once installed, do not have gparted as you cannot edit the partition you are in. I immediately download it as I have multiple drives and also like the visual view it gives of a drive. It is in the Ubuntu liveCD, not sure about other version's liveCD.

I used to always download several repairCDs and went thru a lot of CDs every 6 months when I reinstalled. I now just copy the ISOs to a flash drive and boot my repair ISO & installer from flash drive with grub2 & loopmounting. Easy to update and a lot fewer CDS. I still occasionally do a CD just as anther boot option. 


Does Windows boot ok? The you can create the / (root) partition, NTFS data partition, swap, /home and any others you need. Create then all as logical or inside one large extended partition that uses the rest of the drive.  If you want to leave some unallocated, make sure it is inside the extended or you may run out of primary partitions.

---

### Post by Jpendragon on 2012-09-28
Windows does indeed boot just fine. I'll create the other partitions I need with gparted and then install later (I'm at work now). Do I create one with /boot mount point for GRUB? If not, where will GRUB install (As in, the dropdown menu beneath the partition view in xubuntu installer, where to I say to send it)? OR am I avoiding GRUB altogether by doing this so that Windows Boot Loader can be used to create a GRUB-like menu?

Thanks for all your help btw. I really hope I haven't been a nuisance.

---

### Post by oldfred on 2012-09-28
Windows will not boot Ubuntu, you will need grub2's boot loader installed to the MBR. A lot of grub is in the /boot folder whether in a separate partition or part of root. But bits of grub are in various locations.

Whether you need a separate /boot or just have the boot folder in the / (root) partition is unknown. I like and use small / partitions of 25GB and no separate /boot partition, and have had no issues where ever installed on my 650GB drive. But we are seeing errors where grub is not working on large / partitions or partitions high on large drives. Not sure if BIOS or grub issues. I would install with 25GB / (root) and see if it works. 

Is BIOS set to AHCI? Windows needs settings changed first if BIOS is not already set to AHCI.

---

### Post by Jpendragon on 2012-09-28
Hey, I'm on break. I'm repartitioning right now. The option for an extended partition under the new partition is grayed out. Also, I thought this screenshot would be relevant. The number of drives it says is there is weird, and it's three as apposed to two.

Also, what is the danger with having more than 3 primary partitions? I'm pretty sure I've had more than that before. How do I set partitions to logical or extended when the options are grey?

-Edit-
I Went ahead and set it to install without the extended. I hope that wasn't a mistake. I had to head back to work.

---

### Post by oldfred on 2012-09-28
If you have gpt you do not have extended and logical. All partitions are primary.

Windows creates a partition for something that is unformated. Your sda2 is that and it is ok. But sda3 should show ok, in gparted. What message does it say. Sometimes chkdsk is required in Windows even after a new install.

---

### Post by JKyleOKC on 2012-09-28
With the extended partition option greyed out, I suspect that it's using UEFI-gpt partitioning. This technique does not use extended partitions since it's not subject to the 4-primary limit; that limit applies only to the msdos/MBR technique.

If your BIOS was still set for UEFI, then Windows probably installed in that mode and that means you'll have to install *buntu in that mode also. The installer is supposed to detect this and make the correct choice, but it does not always do so. If you are unable to boot into *buntu after the installation, Boot-Repair should fix things up for you nicely -- it did for me after I was caught in that situation. Some of its actions in doing so sound dangerous (such as purging some of the grub modules) but trust Yann's work and it comes out correct at the end!

If, however, you CAN boot into *buntu after installing, go into a terminal window and type "dmesg|grep EFI:" to determine for sure which way your system is set up. If you get a couple hundred lines of output from that command, it's in UEFI. If you get nothing at all, it's in msdos/MBR mode and you will be limited to four primary partitions including the extended one.

To answer your second question, the danger in going past three, in msdos/MBR mode, is simply that you would not be able to create any more no matter how much space was unassigned. Using the fourth spot for an extended partition that covers all the space remaining makes that space still usable for new partitions.

---

### Post by Jpendragon on 2012-09-28
I told Gparted to make a new partition table in MSDOS, but then I told Windows to install in that unassigned space. So it might have changed it. I have those three in the above image right now, plus linux swap, /root, /home, and the extra NTFS partition, a total of 7 right now. So I'm assuming it's UEFI.

I'll check the alert on sda3 when I get back home.

I don't know how to check if AHCI is checked though.. I'll look in the bios though to see if there is anything.

---

### Post by JKyleOKC on 2012-09-28
I hope that by "/root" you really mean "/" since there really is a partition named "/root" that is only the home directory for the super user, and won't include the rest of the system. However the *buntu installer should sort that kind of stuff out for you...

---

### Post by oldfred on 2012-09-28
I think with UEFI, there is no AHCI. One user posted his UEFI system called the BIOS version AHCI, so I guess that is BIOS only.

---

### Post by Jpendragon on 2012-09-28
Yes, I meant /, rather than /root. I was going to just type /, but then decided to type root instead, but derped and wrote both. 

Anyway. xubuntu installed seemingly just fine. Grub is no where to be seen though. When I turn on the computer, it automatically boots xubuntu. To boot Windows, you have to enter the boot menu and select "Windows Boot Loader." It boots fine though. I'm pretty much back where I was at the beginning of this post except now I have the shared partition instead of two huge ones. How do I get Grub working (or perhaps to recognize that there is in fact more than one partition?)


I'll enter in that code you gave me later (my roommate is using my monitor right now), but with the info you have so far, what might I do.

---

### Post by JKyleOKC on 2012-09-28
At this point I would edit the /etc/default/grub file (using "sudo nano" or your favorite editor) to put "#" characters at the beginning of each of the two lines that refer to HIDDEN_TIMEOUT, then save the file and run "sudo update-grub" to [it the changes into effect. This will give you some time to press the left shift key at the start of the boot sequence, which ought to display the grub menu instead of just booting directly into Xubuntu.

I would actually use grub-customizer rather than editing the default file directly, but installing that program might not be so quick and easy. If you do get it installed, it has a check box to force the menu to display.

I suspect that update-grub is failing to find the Windows installation; running Boot-Repair might correct that, and you can have it just generate the report without making any change to your system at all. That report will include a description of what would be changed if you selected "Recommended Repair" too, so I would run it for the report only and see what it says. Post the URL it gives here so Fred and I can look at it...

---

### Post by oldfred on 2012-09-28
Boot-Repair should be able to add valid Windows chainload entries. Yann has updated Boot-Repair to add correct entries as grub2's os-prober adds BIOS/MBR type entry when for UEFI it has to be different.

Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

So it has been mostly Yann reporting this. They finally changed it to confirmed, but it would not hurt for you to add "Does this bug affect you". You do have to create another sign on in Launchpad.

---

### Post by Jpendragon on 2012-09-30
I ran boot repair first since I didn't trust myself editing files as much as I trusted a program. It worked in that Grub shows up, and both xubuntu and windows are selectable... However, the entries are overly complicated and buried in a list. 

I was wondering, this is sort of only cosmetic, but take a look at the attached file. Could I simplify the list someway? Preferably to only show Xubuntu 12.04 and Windows 7 as two different entries? 

Oh, and somewhat less of a hurry, is there a way to set it so that it doesn't automatically load an OS without me telling it which one? I use windows and xubuntu roughly equally, and I'd like it not to make assumptions.

-edit-
Btw, if it helps, the washed out entry is the same as the one below it except it doesn't say recovery mode, it is xubuntu.
Windows UEFI Loader is windows 7.

---

### Post by JKyleOKC on 2012-09-30
Load "grub-customizer" to adjust the timeout. You cannot disable the automatic boot, but you can extend the time out so much as to not be a problem. The default is 10 seconds. If you increase it to 3600, it will not happen until an hour has gone by.

This program will also allow you to turn off specific entries in the list. It's good, though, to leave the "recovery" entry in it. If you turn it off and something goes wrong, you might not be able to get back into *buntu. However turning off the memory-check entries should not be a problem.

You can also turn off two of the three Windows entries. Just be sure that the one you keep is one that actually works. The reason for three is simply that it's not yet possible to know during the repair which one will be the one that works! I've turned off the one that doesn't work, here. It's easy to do with the grub-customizer program...

---

### Post by Jpendragon on 2012-09-30
And it works. It f*in' works. My headache is finally over!

Thank you so much. Both of you. You guys are great!


(Complete side note: JKyleOKC, what is your avatar from? It's been driving me crazy. It looks like a combination of Jack Nicholson and an animation professor at my school.)

---

### Post by JKyleOKC on 2012-09-30
That's a freeze-frame from a mobile-TV application I helped develop back in 1995. My buddy shot a minute or so of me while we were talking, and I liked this frame well enough to adopt it as my avatar in all the forums that I frequent. I don't look a lot different now, 17 years later!

---

