---
title: "WinXP Unbootable with GRUB Copied on MBR"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by Juan Largo on 2007-01-20
Hi,

The Ubuntu installer automatically copies GRUB onto the MBR without other options.  This is a big mistake, which can render some Windows systems unbootable.

One way this can occur if the primary hard drive is a SATA disk and an IDE disk is added to the system, as is the case for me.  In that case, BIOS will treat the SATA disk as hd1 instead of hd0,and will treat the IDE disk as hd0 instead of hd1.  This sets up a conflict between BIOS and any third-party boot loader.  Any attempt to boot into WinXP (on the first partition of the SATA disk) using any third-party boot loader will fail with an error message that says NTLDR is missing.  The only way to boot into WinXP is to keep the original MBR on the SATA hard disk intact.  If GRUB is copied over the MBR, WinXP will be unbootable.

In other words, the only way WinXP can be booted on my system is through the Windows boot loader.  The correct (only) way to install Linux in a multi-boot setup on a system like mine is to install GRUB on the root partition of the Linux system.  The 512 Byte Linux boot sector is then scraped using the #dd command and transferred to a file on the C:\ partition of the WinXP system.  A line is then added to C:\boot.ini that allows selecting Linux from boot.ini.  

The Ubuntu installer should always provide the user with an option of installing GRUB on the Linux root partition.  The MEPIS installer does this, which is very considerate.  I suspect that the reason many beginners run into horrendous difficulties when trying to install Ubuntu is because it lacks GRUB install options.  I almost made the fatal error of installing a third-party boot loader for my system before I thoroughly checked everything out and discovered the underlying conflict with my SATA/IDE drives and BIOS.  A beginner wouldn't stand a chance under these circumstances, nor would he/she know how to repair his/her system using fixmbr.

---

### Post by AMT on 2007-01-20
That would explain the problem I had when I tried to dual boot Ubuntu 6.10 on my Windows machine. I had to reformat my hd and reinstall WinXP because of the installation nature of Ubuntu. Not only that, my motherboard requires I load additional IDE drivers during the installation of an OS. I didn't have the option to do so with Ubuntu. The Live CD thing is a cool idea, but I don't really see much value in it.  If someone wanted to get a feel for Ubuntu, they would try it on a spare machine or look at the screenshots. At the very least there should be an option to bypass the Live CD as well as the ability to install additional drivers.

- Andrew

---

### Post by scbonney on 2007-01-21
oops.

---

### Post by Juan Largo on 2007-01-21
scbonney-

How were you given the option of booting Windows or Ubuntu after you ran fdisk/mbr from the universal boot disk?  Didn't that action blow GRUB away?  Also, what is the nature of your "current problem?"

---

### Post by scbonney on 2007-01-28
As it happens I had to reinstall ubuntu.  If I knew then what I know now I would have known I didn't know what I was talking about.  Except that if you can't boot anything when a dual boot goes wrong boot disks are nice. Boot disks of any flavor of OS.

---

### Post by housam on 2007-01-28
Maybe the [super grub disk ]("http://supergrub.forjamari.linex.org/")can give you the solution.

---

### Post by geek_Man on 2007-01-28
Yeah, get the Super GRUB Disk. It's really cool.

---

### Post by mjmeche on 2007-01-28
I am having the same problem basically. I am trying to install the 64 bit OS on a Abit An8 32X with an Opteron 170m, 1 Gig of RAm, Primary boot drive for xp pro is a sata drive which is 120 gb partitioned basically in half. One for xp pro and the other for Ubuntu 64. I do have an IDE 250 Gb drive which is for storage. Sata DVD writer and Ide cd writer. After install, it says "remove cd and hit enter" seems that system stops responding. When reset system comes back with no OS. Luckily I have a backup of the xp. 

So what you are saying is when I get to where is says grub to hd0 i should change that to hd1 ? I do know when i looked at device manager on live cd it showed the sata drive as sda.

Any help greatly appreciated beyond wahat I can say. 
I am a noob, but have done installs on regular i386 machines with plain ide.


Got it grub was being put on ide instead of sata,just unplugged the ide devices and reinstalled now it works

---

### Post by adrian15 on 2007-02-07
> **Juan Largo said:**
> Hi,

The Ubuntu installer automatically copies GRUB onto the MBR without other options.  This is a big mistake, which can render some Windows systems unbootable.

One way this can occur if the primary hard drive is a SATA disk and an IDE disk is added to the system, as is the case for me.  In that case, BIOS will treat the SATA disk as hd1 instead of hd0,and will treat the IDE disk as hd0 instead of hd1.  This sets up a conflict between BIOS and any third-party boot loader.  Any attempt to boot into WinXP (on the first partition of the SATA disk) using any third-party boot loader will fail with an error message that says NTLDR is missing.  The only way to boot into WinXP is to keep the original MBR on the SATA hard disk intact.

I do not agree with you, I think there's an alternative way, (and the problem is not due to Ubuntu but to windows that always wants to be in the first hard disk. If your bios sets IDE as first hard disk and SATA as the second one... why don't you setup your bios so that it is the other way round. Your problem is not Ubuntu but the adding of an ide disk.)

Once Ubuntu installs Grub automatically on the SATA MBR... have you tried editing menu.lst and adding a line like this:

title windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
boot

Does it boot ?

adrian15

---

### Post by Juan Largo on 2007-02-07
Adrian15 -

I must respectfully disagree.  Ubuntu IS the problem if it insists on overwriting the MBR.  Adding an IDE hard disk to my system does not prevent me from booting WinXP on the SATA disk.  However, installing a boot loader on the MBR on my system will  produce a "no NTLDR" error.   

Your suggestion to edit menu.lst will work.  Fair enough.  But why force the user down that particular path instead of allowing him/her to follow a different one?

Your suggestion to modify the BIOS:  I didn't have to modify the BIOS in order to install the IDE disk, so I don't think I should have to modify the BIOS to install Linux -- provided there is an easier way.  For me, the easier way is to install GRUB on the Linux partition, copy the boot sector of the Linux partition to a file on the C: drive, and add a line to C:\boot.ini.  SimplyMEPIS gives me that option, but unfortunately Ubuntu doesn't.  

In addition, some computer OEMs add customized features to the MBR that enable function keys to do certain things during startup.  Overwriting the MBR blows away those features -- permanently.

I still maintain, as stated in my earlier post, that it is very bad form for any OS -- even Ubuntu -- to take "ownership" of the MBR by default and without offering other options.  The whole idea behind Linux is to offer choices and options.

The Ubuntu community should be open to suggestions to improve the product in order to enhance the user experience -- especially for beginners -- and make Ubuntu suitable for as many computer configurations as possible.  I appreciate the workarounds -- I really do -- but I think it would be better to fix the installer instead.

---

### Post by Moulton on 2007-02-07
Look in /boot and /boot/grub to see if the Linux installer saved a copy of your original  MBR.  Look for any file of size 512 bytes with a datestamp that corresponds to when you installed Linux.

You can restore your MBR from that, using the 'dd' command.

---

### Post by confused57 on 2007-02-07
> **Juan Largo said:**
> Adrian15 -

The Ubuntu community should be open to suggestions to improve the product in order to enhance the user experience -- especially for beginners -- and make Ubuntu suitable for as many computer configurations as possible.  I appreciate the workarounds -- I really do -- but I think it would be better to fix the installer instead.

I believe the installer has been fixed, I've read that on step 5 of 6, there is an option of where to install grub...the default is (hd0), but there's an arrow next to it with a drop-down menu that allows you to specify where(hd0,hd1,root partition,fd0), etc.

Each hard drive has it's own mbr, which you probably already know, rather than a system mbr...you just choose which mbr you'll be booting first to boot your OSes, in your case, you've decided to boot from the Windows mbr.

You could also boot first to the Ubuntu mbr, if it is designated as hd0 in grub, then boot Windows from that, it's a choice.

I realize it is "confusing" to beginners(hence my username), but there's always help on the forums to answer any questions, before or after installing...it's up to the new user if he wants to use this option or just try to figure it out on his own.

---

### Post by Herman on 2007-02-07
> The Ubuntu installer automatically copies GRUB onto the MBR without other options. This is a big mistake, which can render some Windows systems unbootable. While this was true, of the earlier 'Desktop' live/install CDs, users have always had the opportunity to choose  the 'Alternate' Install CDs if they wish to carry out a custom install. There are simple instructions in my first sig link under this post complete with illustrations so that anyone can understand what to do.
I have illustrated how to install Grub to MBR, (the preferred option), as well as how to install Grub to the first sector of the Ubuntu partition, or to a floppy disk, or somewhere else if you  like. You can also install Lilo instead, or carry on without any bootloader at all.
The Edgy Eft Desktop CD that I have been using in the past few days does have the ability to install Grub anywhere you like as well, but I haven't tried it out, as I always choose the MBR anyway. If you look, in step 6, about half way down the page, you will see a line that says, 'GRUB will be installed to: (hd0)'. If you click (hd0) with your mouse, you will be given a text box that allows you to type in your alternate location for the first stage of Grub bootloader to be installed. (As confused57 said, sorry for the simultaneous post).

I am interested in learning more about OEMs installing keyboard drivers or code that leads to them in the MBR, I have never heard of that practice before.

If someone is frightened by the prospect of something happening that they don't understand when their MBR is upgraded, they can back up their MBR from any Linux LiveCD with a simple 'dd' command if they like. Restoring this backup if necessary will restore the MBR to exactly the way it was before. [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd"). The 'dd' command used to do that is similar to the 'dd' command they would need to use to copy Grub's stage1 from the Linux partition anyway, so it would not require any extra work or learning than the NTLDR method. Actually, it would be safer, as editing the boot.ini file in Windows imperfectly would also render Windows unbootable. In fact, it would put both operating systems out instead of only one.

As long as the Windows partition number has not been changed, I have never heard of anyone having an 'no NTLDR error' yet here in Ubuntu Web Forums. However, if the Windows partition is copied and pasted, this would cause Windows to be given a new partition number, which can produce that error. A Windows XP boot floppy disk will boot Windows independantly from the bootloader part of the MBR, the Windows boot sector, Ntdetect, NTLDR, and boot.ini. If your partition number has been changed, you can edit boot.ini on the floppy disk from Linux, as the floppy disk is FAT32. Then you can boot Windows and edit boot.ini with the correct partition number.
How to make your own Windows Xp boot floppy, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/").

Editing Grub's device map, which is very simple, should sort out your IDE/SATA problem. [**Editing Grub's device.map**]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map")

Regards, Herman  :)

---

### Post by dannyboy79 on 2007-02-07
> **AMT said:**
>  The Live CD thing is a cool idea, but I don't really see much value in it.  If someone wanted to get a feel for Ubuntu, they would try it on a spare machine or look at the screenshots. At the very least there should be an option to bypass the Live CD as well as the ability to install additional drivers. 


HUH??? The purpose of the Live CD is to be able to try it out WITHOUT affecting your current install. It  runs from the CD, hence why it's called a Live CD. What you want to download is the Alternate CD if you don't want a Live CD. Also, there is ways of getting additional drivers loaded so that your ide chipsets are seen by the installer.

---

### Post by Juan Largo on 2007-02-07
Moulton -

Fortunately, I saved my MBR *before* I installed Ubuntu, in anticipation of boot problems.  So I was able to restore the OEM version of my MBR.  However, I doubt that most beginners would think about doing that ahead of time or even know how.

Herman -

It's very refreshing to know that the "Alternate" versions of the install disk have the option to install GRUB on the Linux root patition.  However, most *beginners* will generally use the Live CD to try out Ubuntu and then use that disk to install it, so those GRUB options you mentioned should be available on the Live CD too.  There are generally three reasons why Linux installations typically go south:  1) an improperly burned CD, 2) problems with partitioning, and 3) problems with the Linux boot loader.

I agree with dannyboy79.  The whole idea is to attract new Linux users and convince them to move away from Windows.  If they end up with a system that's unbootable (even if there is a relatively easy fix), this will surely convince them never to try Linux again and cause them to spread the word about how "hard" Linux is to install.  The least obtrusive way to set up a dual-boot system on a Windows machine for a "trial" Linux installation is to use the Windows boot loader that came with the computer.  Then you can "uninstall" Linux very easily by deleting the partition on which it lives.  Installing GRUB over the MBR is very much an "in your face" way to do an install and not a very good way to win people over to Linux.

---

### Post by Herman on 2007-02-08
Juan Largo-
You didn't read my post or confused57's, or you have missed something:
Quote from my previous post:
> The Edgy Eft Desktop CD that I have been using in the past few days does have the ability to install Grub anywhere you like as well, but I haven't tried it out, as I always choose the MBR anyway. If you look, in step 6, about half way down the page, you will see a line that says, 'GRUB will be installed to: (hd0)'. If you click (hd0) with your mouse, you will be given a text box that allows you to type in your alternate location for the first stage of Grub bootloader to be installed. (As confused57 said, sorry for the simultaneous post). Perhaps you don't realize that the 'Desktop' Live/Install CD ***is*** the Live CD ?
 The 'Alternate' CD is the more traditional installation CD that is only good for installing plus a few utility purposes.

> I agree with dannyboy79. The whole idea is to attract new Linux users and convince them to move away from Windows. If they end up with a system that's unbootable (even if there is a relatively easy fix), this will surely convince them never to try Linux again and cause them to spread the word about how "hard" Linux is to install. The least obtrusive way to set up a dual-boot system on a Windows machine for a "trial" Linux installation is to use the Windows boot loader that came with the computer. Then you can "uninstall" Linux very easily by deleting the partition on which it lives. You didn't read dannyboy79's post properly either, or if you did, you haven't interpreted it in the same way that I have. I think dannyboy79 meant that if you aren't sure whether or not you want to install Linux, then just run the LiveCD to try it out. That's the purpose of the Live CD. If the Live CD doesn't work with your hardware, then don't install to hard disk. If you try out Ubuntu in the Live ('Desktop') CD and you like it, you can install it to MBR if you wish. It's up to you. No-one is forcing you.

Actually, the number of people experiencing difficulties installing Ubuntu (with Gnu Grub), is quite small in proportion to the number of installations that are probably going on in the world. The number of new members of Ubuntu web forums may not be an accurate indication, but probably around 450 to 475 per day are joining these forums since I have been counting.
> Sat 18 Nov 2006 13:45:52 EST ,Members: 195,727
13016  new members /  29 days =448.8 per day
Sat 16 Dec 2006 13:32:16 EST ,Members: 208,743
25,825 new members /  54 days   =478.2 per day
Thu 08 Feb 2007 15:53:50 EST ,Members: 234,568When you take into account that many of these people may be performing several installations, really we don't have a large proportion of people experiencing problems, at least not in my opinion.
For many of these people, it will be the first time they have tried disk partitioning and the first time they will have ever installed their own operating system. Some problems are to be expected due to lack of knowledge, but people learn quickly. What proportion of the 450 per day would you estimate would experience a minor booting problem? What proportion would you estimate would experience a boot problem that cannot be easily solved?
I think very few.

It seems to me that people are leaving Windows in droves. They are sick of being frightened all the time and held for ransom by commercial software's new twist on the old fashioned protection racket. "pay us or we won't protect you from viruses, spyware, adware and other assorted nasties.. and pay..and pay..." As long as people can still be frightened , they keep on paying. But people are getting tired of the fear tactics. People are ready to begin learning how to take control their own computers.
For many of these people, although they may not realize it at the time, customizing their grub bootloader will be their first steps in learning computer programming. They want to start learning how to take control of  their own computers and stop relying on others to do everything for them.
Really, Gnu Grub is part of fun for most people. Gnu Grub is actually much, much more than just a dumb bootloader. Grub is actually a small operating system in its own right, capable of running useful and interesting commands for us. To miss out on the Gnu Grub aspect of Ubuntu would be quite a shame, and I feel sorry for those few unfortunate people who own computers that are not able to function well with the Gnu Grub bootloader.
I don't blame people if they have no other choice and they are forced to use NTLDR for dual booting, but I do feel sorry for them.  I would never advise anyone to ever try dual booting with NTLDR unless there was no other alternative.

Regards, Herman.

---

### Post by confused57 on 2007-02-08
> For many of these people, it will be the first time they have tried disk partitioning and the first time they will have ever installed their own operating system. Some problems are to be expected due to lack of knowledge, but people learn quickly.

I didn't even know what a partition was before I installed Breezy...I had built my first computer about a month before trying out Ubuntu, paid $100 for Windows XP Home, had no trouble installing XP...took quite awhile to get up to speed with updates & patches, then installing all the security programs, i.e. AV, anti-spyware, firewall, winzip, winrar, etc, etc.

I was aware of Linux, but knew absolutely no one who had any experience or had installed any distro of Linux...I googled and found Ubuntu, which appeared to be a relatively easy Linux distro for an absolute beginner and shipit made it even more enticing to give it a try as I wasn't comfortable downloading and burning an iso.  The shipit cd's included an alternate installer and a separate live cd...I didn't know what the live cd was all about, so I just popped in the alternate installer, which was quite intuitive for someone as "raw" as I.
I have to confess though, that I had an old pc, 500 Mhz, AMD K6-2, 256 mb ram that I could use to "experiment" with, especially not knowing what to expect...I didn't want to compromise my main computer, since I was exploring "new territory".
I wasn't really expecting much, but much to my surprise & delight, I was surfing the web an hour after starting the install...and the rest is history.

I now have 2 computers dualbooting Windows & Ubuntu on separate hard drives, using grub to boot to the Windows drive(again, I "chickened" out and installed grub to the Ubuntu drive)...found some excellent instructions by doing a forum search for setting up the system this way.

I've since built a 3rd computer with an IDE and SATA drive, which is devoted entirely to installing and "testing" different Linux distros(about 10 currently)...I've come to realize what a powerful bootloader grub is, when managing & booting that many distros on one computer.  Forum and Google searches have been invaluable in learning how grub works, how to reinstall grub, where to install, etc...I've even installed Gentoo & LFS, which require pretty much setting up the menu.lst or grub.conf from scratch.  Herman's site has been an invaluable resource for setting up grub & getting myself out of trouble when I have grub problems.  Many forum members have their own instructional websites for Ubuntu & Linux to help beginners, as well as more experienced users, maintain and administer their Linux system.  The forum support is second to none for getting assistance, before or after installing.

If my initial experience with Breezy was a total failure, I probably wouldn't have persevered to "make it work"...it would have been "stick with Windows", Linux is not for me.
Thanks Ubuntu, computing is fun again...the more I learn, the more I realize how little I know about Linux.

---

### Post by adrian15 on 2007-02-08
Juan Largo there is something that I do not understand.
I need more information about the IDE disk... was there a Windows installation before on it?

adrian15

---

### Post by Juan Largo on 2007-02-08
Herman -

My original post in this thread was based on my experience with the Ubuntu Live CD that I downloaded in November 2006.  If I understand you correctly, there is a later version, called Edgy Eft Desktop CD, which gives you the option of where to install GRUB.  If Edgy Eft Desktop is now the "official" trial version Ubuntu, and if Ubuntu have discontinued the version of the Live CD I downloaded in November, then I agree that Ubuntu have fixed this problem and this entire thread is moot.

For the record, my first Linux test drive was with Knoppix, which is totally a live CD and doesn't even come with an installer.  I think Klaus Knopper made an excellent call by not having an installer, since I would have completely screwed up a real installation at that stage.  Later, I learned how to do a "poor man's install" with Knoppix on my hard disk using a virtual file system and cheat codes for booting into it.  After playing around with Knoppix for a while, I experimented with VMware and virtually "installed" about a dozen or so Linux distros before I felt I was finally ready to attempt a "real" Linux installation. 

Unfortunately, some Linux beginners jump right in and attempt a full-blown installation without doing very much preparation.  I don't have any statistics or know how many of them succeed or fail, but I would guess the failure rate is pretty high, mainly because of the three reasons I mentioned in my previous post.

adrian15 -

In my case, I bought a new computer that came with a 250GB SATA disk with WindowsXP pre-installed on it, along with a rescue partition on that disk.  I then made additional partitions on the SATA disk for Linux, data files, and a partition for sharing files between Linux and Windows.  The IDE disk is a 120GB Seagate disk that I pulled from my old machine, which I use for backing up the main SATA disk -- ghosting the WindowsXP and Linux partitions, backing up mail folders, data, etc.  By the way, Hewlett Packard has excellent support for Linux, so I would highly recommend HP hardware to Linux users.

---

### Post by Herman on 2007-02-09
> My original post in this thread was based on my experience with the Ubuntu Live CD that I downloaded in November 2006. If I understand you correctly, there is a later version, called Edgy Eft Desktop CD, which gives you the option of where to install GRUB. If Edgy Eft Desktop is now the "official" trial version Ubuntu, and if Ubuntu have discontinued the version of the Live CD I downloaded in November, then I agree that Ubuntu have fixed this problem and this entire thread is moot. Well, if you downloaded 'Dapper Drake', that's the currently [COLOR=Red]long term supported[/COLOR] stable version. Edgy Eft is the most up to date [COLOR=Red]stable version[/COLOR], but soon, (I don't know when, April 19th?), Fiesty Fawn will be released, but a lot of us will be installing before it is officially released. That's not safe (as in stable), and even for a while after the official date, new releases often take a while to settle down. The way I do it is to have my whole partition backed up, so if anything bad happens, I can copy and paste it back again with GParted in a matter of about ten minutes. Most people who preview the most advanced software have some really fast  way of totally backing up and restoring if necessary.
> For the record, my first Linux test drive was with Knoppix, which is totally a live CD and doesn't even come with an installer. Yes, Knoppix is a good distro, I like it too. I just run it from a Live CD though.
```
Unfortunately, some Linux beginners jump right in and attempt a full-blown installation without doing very much preparation. I don't have any statistics or know how many of them succeed or fail, but I would guess the failure rate is pretty high, mainly because of the three reasons I mentioned in my previous post.
```I can't see any problem with that as long as people are confident enough in their computer skills to have their data backed up, and know how to re-install their other operating system. Really, what's the worst that can possibly happen? You could have to reformat the entire hard disk completely and have to start again from scratch. Just ask me, that happened to me once. (It had nothing to do with Ubuntu). It didn't bother me too much though. I had all my important information backed up, and within a few of hours I had everything re-installed and running again. The only difficult thing about it is if you have a Windows installation. Windows is a bit complicated to back up and restore. Other than that, it does Windows a lot of good to have a nice clean re-install. I used to do it regularly when I was a Windows user. All you do is put the CD in the drive and let it go. What's so bad about that? :)
But I do think it is important for people to make sure they are able to completely restore what they had before they begin any disk partitioning or operating system installations.

Regards, Herman :)

Edits: Typing in red print is where I corrected the post to agree with dannyboy79 in the following post, thanks dannyboy79. :)

---

### Post by dannyboy79 on 2007-02-09
> **Herman said:**
>  Well, if you downloaded 'Dapper Drake', that's the current stable version. Edgy Eft is the most up to date

I have to correct you here, Edgy Eft is the most current stable release of Ubuntu. The only difference between Edgy and Dapper as far as stability and support is that Dapper as Long Term Support where Edgy doesn't.

This is per the Ubuntu website:

Choosing an Ubuntu Release
There are now two versions of Ubuntu, choose which is best for you: 

Ubuntu 6.10, the newest Ubuntu release: If you would like to benefit from the latest Ubuntu features, this is the release for you 

Ubuntu 6.06 LTS, Ubuntu with long-term support: Choose this to benefit from the long support life-cycle of the 6.06 LTS release. This version is supported for 3 years on the desktop and 5 years on servers.

---

### Post by Eric B on 2007-02-09
I am having the same problems as Juan.

I have 2 IDE drive with no OS, just data, and 1 SATA drive with Windows. I made room for Ubuntu, installed it. I get to the boot loader, and it cannot find NTDLR nor can it boot Ubuntu. Putting an OS on my IDE drives sucks because they are smaller and used to back up important data. I have more tha nenough room for OSes and unimportant things on the SATA.

---

### Post by Herman on 2007-02-09
Hello there Eric B,
I guess nobody noticed you here until now because you tacked you post onto the bottom of an existing thread instead of staring a new thread. That's okay, but sorry to have kept you waiting for so long.
You should still be able to easily boot both operating systems with a [Super Grub Disk]("http://supergrub.forjamari.linex.org/")
To fix this more permanently, it will be important to take a look at a few of your files in your Ubuntu partition so we can try to see what the exact problem is.
If you can post the feedback from the following three commands here it will make it possible for me or someone to help you.
```
sudo fdisk -lu
``````
sudo gedit /boot/grub/device.map
```Just the bottom portion of the menu.lst file is all that will probably be needed.
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Juan Largo on 2007-02-10
Eric B -

I'd be interested to find out which version of Ubuntu you installed (Dapper Drake 6.06 or Edgy Eft 6.10)?  If the former, I think you made my point.  Dapper Drake automatically overwrites the MBR, which led to your problem (same as mine).  Herman was kind enough to offer you help; however, the installer set a trap for you.  Evidently, the SATA/IDE combo fools GRUB into pointing to the wrong disk for both Windows and Linux.  

I'll say it again:  For *some* people (but not everyone) installing GRUB on the MBR works fine.  But for others, the least obtrusive way to do ease into a dual boot setup with Windows is to use the boot loader that came with the comptuer.  That choice should be up to you.

---

### Post by geek_Man on 2007-02-11
Grub isn't fooled, that's just the way it works.

---

### Post by Herman on 2007-02-12
By the way, for the record Eric B easily solved his booting problem in this thread, two days ago, [http://www.ubuntuforums.org/showthread.php?t=357199](http://www.ubuntuforums.org/showthread.php?t=357199) with a little help from mikewhatever and confused57.

Thu 08 Feb 2007 15:53:50 EST ,Members: 234,568 
2356 new members / 4 days =589 per day
Mon 12 Feb 2007 18:07:40 EST Members: 236,924
During the last four days, 2356 new member joined Ubuntu Web Forums, an average of 589 per day. We have had a small number of booting problems, but most were solved easily. (I don't know of any that haven't been solved or aren't in the process of being solved). Only one that I know of might require a Windows re-install and is probably due to partitioning problems, the exact cause of which are impossible to determine.

For the vast majority of these installations, the grub bootloader automatically configures itself, and on the rare occasions when it isn't able to do so quite perfectly, we have grub's command line interface to rely on to solve the problem. Due to increased documentation and user awareness, more users are able to solve their own booting problems using the grub CLI. There are some very capable helpers here in this forum waiting to help otherwise.
Certian other bootloaders make no attempt at all to automatically configure themselves on any occasion and definitely require manual editing each and every time. I am sure that all hell would break loose if users were forced to use that certian other (dumb) bootloader. Luckily they have a choice, and the vast majority choose grub.

The 'Alternate' CD has always been available since Ubuntu 'Warty' first became available, allowing users the full range of choices for bootloaders and other options, but a few users complained it was 'too complicated'. (Because they had too many options). So the 'Desktop Live/Install CDs were invented. The 'Alternate' CDs have always been available if anyone doesn't want to use the simpler 'Desktop' CD. Now we have users complaining they want the 'Desktop' CDs to have more options. ](*,) Gah!
So the wanted options have already been added, but that's not good enough, it has to be made retrospective for earlier releases as well! 

I'm glad I'm not a developer, I'm getting a headache just thinking about it.

(Herman)

---

### Post by Juan Largo on 2007-02-12
geek_man:

That was an interesting response.  It's not a bug, it's a feature!

Herman:

I didn't have any problem booting into my system with that "other dumb boot loader" after I installed the IDE disk because it didn't try to reconfigure itself.   Sometimes a "smart" boot loader can be too smart for its own good.

This will be my last post in an Ubuntu Forum, since I decided to move on to MEPIS.  And yes, I'm aware that MEPIS owes a lot to Ubuntu.  However, because they're only #4 on Distro Watch, they seem to try harder.

---

