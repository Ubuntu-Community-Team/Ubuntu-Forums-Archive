---
title: "'SATA' Hard drive installation difficulties."
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by screw_ball on 2005-10-24
I've been using Ubuntu for about four months now.  I used to run Hoary on my eight year-old Dell Inspiron 7000.  I just got a Dell Dimension 9100 desktop, and I'm having a lot of difficulty installing.

I installed Hoary on my old laptop without any problem several times.  Never had a problem before.  Now, when the Hoary (I haven't got my Breezy CDs yet, and I can't burn CD images, as will be explained later) install gets to the partitioning (on my new computer), it says that 'there is no partitionable media on my hard drive', and that I should make sure I have a hard drive connected.  Now, this is a desktop which I have not modified in any way.  I'm pretty damn sure there's a hard drive in there.

But something seems fishy with my HD...  It says it's 'SATA' instead of the usual IDE.  Now, I have no idea what SATA is, but I think it may have something to do with my problem.

My other problem is that Windows (ugh) doesn't seem to be recognizing ANY of my drive correctly, crippling my ability to burn CD images, therefore making it impossible to get Breezy until my CDs are shipped, and using any of the HD-wipe software that's been recommended to me.

My Google searches haven't helped me at all, and XP is suffocating me.  Any help would be gladly appreciated.

---

### Post by Coldie on 2005-10-24
[QUOTE=screw_ball]
My other problem is that Windows (ugh) doesn't seem to be recognizing ANY of my drive correctly, crippling my ability to burn CD images, therefore making it impossible to get Breezy until my CDs are shipped, and using any of the HD-wipe software that's been recommended to me.[/QUOTE]

What does it mean? Windows doesn't recognize any of your drives correctly? I mean it must at least recognize the drive it is installed on.

---

### Post by flower on 2005-10-25
hm... sorry for the wild guess but maybe your new hdd is SATA after all :)
you can check this easily - open your pc case and check what type of interface cable is connected to your HDD ... if it is the older one - the wide flat cable - it is IDE, if it is fancy and tider it's SATA ... 

but ... Ubuntu doesn't seem to have problems with SATA hdd , I've got SATA and I had no problems with it.

better check if the HDD is connected correctly to the motherboard,
and another thing you can try is go to the BIOS and see if there's a setting to force the SATA interface to act as IDE

---

### Post by rsankuratri on 2005-11-06
I am having the same problem with my Dell Dimensions 9100 desktop.  It will not partition the hard drive correctly.  The display does not work.  I do not get the Gnome GUI, but only the command prompt.  It has the following configuration:
1.  250GB SATA Hard drive (Maxtor MXT-SA)
2.  Radeon X600 256MB Graphics card
3.  19 inch Flat panel display (1905FP)
4.  1 GB Memory
5.  Pentium D processor (3.0 G)

Please help.  I would like to wipe out the hard drive completely and start over if possible with Ubuntu 5.10   ](*,)

---

### Post by opera118 on 2005-11-06
[QUOTE=flower]Ubuntu doesn't seem to have problems with SATA hdd , I've got SATA and I had no problems with it.[/QUOTE]

It does have problems with SATA.

---

### Post by rsankuratri on 2005-11-06
Going back to windows xp on my new Dell Dimension 9100 desktop... until I figure out the SATA problems...:confused:

---

### Post by yur1022 on 2005-11-08
[QUOTE=opera118]It does have problems with SATA.[/QUOTE]

Any idea how to overcome it (except getting other distros dealing with sata corectly)? Heard of any words on it from Ubuntu developers?

Thanks

yur

---

### Post by jdong on 2005-11-08
3 of my 5 active computers are pure SATA, and Ubuntu works fine on it (currently using VIA and SIL based SATA chips). I've seen successful uses of Ubuntu on Promise 350's and Intel ICH*'s.


I can't confirm the existence of any known SATA difficulties in the bug database....


Your problem report was very vague (something about *Windows* not recognizing the drive?). Can you please try to clarify for us exactly what's wrong? Thanks!

---

### Post by yur1022 on 2005-11-08
Well, my problem, as reported in another thread, is that Breezy chokes up during the installation bootup. That is, after displaying

[4294675.462000] Attached scsi disk sdb at scsi2, channel 0, id0, lun0

it stops. By reading this, I guess the problem has something to do with sata.
My computer has 2 non-raid sata drives.

yur

---

### Post by jdong on 2005-11-08
This appears to be unrelated to screw_ball's problem, so let's talk about it in a different thread.

---

### Post by yur1022 on 2005-11-09
OK. I posted the question under "Cannot install Breezy ... non-raid sata problem?" about 10 hours ago.

yur

---

### Post by opera118 on 2005-11-09
[QUOTE=jdong]This appears to be unrelated to screw_ball's problem, so let's talk about it in a different thread.[/QUOTE]

Wrong, this is all the same major problem. It has an easy solution, similar to "getting other distros dealing with sata corectly", namely having an ubuntu installer that uses a modern kernel. New hardware and old hardware gets better and better support in recent kernel versions. However, the ubuntu developers seem to ignore this and says that new kernel versions will appear in the next release of ubuntu (where talking in terms of half a year periods, sorry if you have newer hardware).

If this continues, ubuntu will be labeled as the linux distro that doesn't support new hardware (that Does have linux support!). The solution to this is simply; get another distro, where the developers care about these things. As of now, it seems that a 2.6.14 is difficult to find in any install/live cd on any distro. A 2.6.13 shouldn't be impossible though.
*Edit: Arch Linux has a 2.6.14 kernel. I will try that when I get home this evening, and let you know if it worked for me. Not that I'm willing to use any distro, I like debian / ubuntu, but I prefer a rusty old VW that takes me from spot A to spot B, over a shiny BMW where they forgot to include the engine.*

I'm greatly disappointed of ubuntu because of this, and their 5 year support for next major release seems rather pathetic in comparison to the current status in hardware support.

O

---

### Post by jdong on 2005-11-09
> 

I installed Hoary on my old laptop without any problem several times. Never had a problem before. Now, when the Hoary (I haven't got my Breezy CDs yet, and I can't burn CD images, as will be explained later) install gets to the partitioning (on my new computer), it says that 'there is no partitionable media on my hard drive', and that I should make sure I have a hard drive connected. Now, this is a desktop which I have not modified in any way. I'm pretty damn sure there's a hard drive in there.

But something seems fishy with my HD... It says it's 'SATA' instead of the usual IDE. Now, I have no idea what SATA is, but I think it may have something to do with my problem.

My other problem is that Windows (ugh) doesn't seem to be recognizing ANY of my drive correctly, crippling my ability to burn CD images, therefore making it impossible to get Breezy until my CDs are shipped, and using any of the HD-wipe software that's been recommended to me.


**NO**, it is not the same problem. This seems to be a specific problem with his SATA chipset or SATA drive. 


As far as getting new kernels during releases, I do not know of a SINGLE Enterprise-class distribution that does that. SUSE, Novell Desktop Linux, RedHat Enterprise Linux (CentOS), Mandrake Linux, and Debian all do not provide kernel version upgrades. Surely RHEL will provide a yearly errata package for kernels, but then again Ubuntu would've gotten 2 new kernels in the timeframe. The only distros that provide new kernel versions are the experimental nature or BSD inspired ones: Gentoo, Arch, Fedora Core, and a few others. Just follow their hardware forums for a while and you'll understand the hell with kernel upgrades.

This is no longer the days of Kernel 2.4 where you can pull a new kernel version whenever you want.... New releases of 2.6 have all kinds of new features mixed in with driver updates, and what "fixes" your specific combination of hardware will break someone else's. There's simply no good way of testing for compatibility on a large scale in the middle of a release -- if you follow the kernel developers during the development season, maybe you'll understand the complicity behind kernel updates.

Upgrading the kernel is not the magical answer to everything. While I agree sometimes Ubuntu lacks on providing errata updates like its Enterprise class buddies, those distros only provide these update packs at bi-yearly intervals or so -- so Ubuntu in a way does provide these updates as new interim releases. I've also been told that Dapper Drake will sport upgrade packs.

---

### Post by opera118 on 2005-11-09
The word "enterprise" really doesn't mean **anything**, more that enterprise versions of software and OS's usually suck *ss and have all sorts of sick issues. You can't seriously compare anything useful to RedHat without doing it with irony.

Yes, 2.6 versions breaks things more than 2.4 versions did, but still it would be useful to get at least the installer on several kernels (no matter what kernel I feel like using when I've successfully installed the os). That IS a good solution. If 2.6.12 is default, fine. But give me an ubuntu installer with 2.6.13, otherwise I will not be able to install it no matter what! Talking about enterprise.....

I just tried Arch linux with 2.6.13 in its installer 5 minutes ago, it finds my hard drive easily with no problem at all. This is an issue!

So, when do you think I will be able to install ubuntu? In an enterprise point of view, that is...

O

---

### Post by jdong on 2005-11-09
Breezy was stabilized against a modified 2.6.12 kernel, incorporating many new patches from 2.6.13 and HEAD git trees.


If you're still having problems getting Ubuntu to install, report it as a bug in the Ubuntu Bugzilla.... It's very difficult to work around this, without a developer looking at the specific case.

I can tell you that in general SATA issues are fairly rare...

Oh yeah, drop the "Ubuntu sucks" attitude a bit when talking to the devs... they tend to get real fired up about it.

---

### Post by opera118 on 2005-11-09
[QUOTE=jdong]Breezy was stabilized against a modified 2.6.12 kernel, incorporating many new patches from 2.6.13 and HEAD git trees.[/QUOTE]

Obviously something was missing since Arch Linux on 2.6.13 saw my hard drive. Note, I do not have the acpi problem many others have, so either it's a particular driver missing, or it's some general sata/ide-thing that must be weird in the installer.

[QUOTE=jdong]Oh yeah, drop the "Ubuntu sucks" attitude a bit when talking to the devs... they tend to get real fired up about it.[/QUOTE]

I wouldn't mind not being able to install Ubuntu if I thought it sucked. This issue sucks, not being able to install sucks, and I think it would be very useful for Many if the installation came (unsupported, fine) with different kernels.
If I would settle with just any distro, I wouldn't be here.

Is there Any way I can "patch" the installer .iso with my own kernel in a way that doesn't require weeks of work? I'm willing to find this problem myself then. Maybe if I got the installer's kernel .config as a start.

O

---

### Post by jdong on 2005-11-09
[QUOTE=opera118]Obviously something was missing since Arch Linux on 2.6.13 saw my hard drive. Note, I do not have the acpi problem many others have, so either it's a particular driver missing, or it's some general sata/ide-thing that must be weird in the installer.
[/quote]
Which is why I want you to head over to the developers in order to isolate the problem.

> 
I think it would be very useful for Many if the installation came (unsupported, fine) with different kernels.

As I said, no major distro really does that... There are so many stability and platform targeting issues associated with multiple kernel versions.

> 
Is there Any way I can "patch" the installer .iso with my own kernel in a way that doesn't require weeks of work? I'm willing to find this problem myself then. Maybe if I got the installer's kernel .config as a start

I know for sure you can build your own debian-installer images, but am not personally familiar with the process. Ask on #ubuntu-devel on freenode for that kind of info.

---

### Post by yur1022 on 2005-11-10
Well, interesting, though hot, debates ...

Is any Ubuntu developer reading this thread and able to contribute a few words to this issue? Even better yet, is there any solution, such as kernel options or installation floppy/CD with patches applied?

yur

---

### Post by jdong on 2005-11-10
Few Ubuntu developers visit the forums. You're not gonna get their attention from here. Sorry to say that, but it's a fact. The mailing lists, IRC channels, and Bugzilla database are the 3 best ways of getting ahold of developer attention.

---

### Post by yur1022 on 2005-11-10
Somewhere I read an article saying that turn SATA raid on even if one has a single drive in order to install Breezy. I did it, but still got the same error. I guess all my options are now gone. So, I should wait for the next release of Ubuntu ... (and give away those handsome CDs I received from Ubuntu developers).

yur

---

### Post by scottd18 on 2005-11-27
[QUOTE=yur1022]Well, my problem, as reported in another thread, is that Breezy chokes up during the installation bootup. That is, after displaying

[4294675.462000] Attached scsi disk sdb at scsi2, channel 0, id0, lun0

it stops. By reading this, I guess the problem has something to do with sata.
My computer has 2 non-raid sata drives.

yur[/QUOTE]
I seem to be having the same install problem as yur1022. My brand new Dell Dimension E310 chokes at about the same point with 5.1. I can get Knoppix 3.9 and 4.02 to boot. I'm not sure the Ubuntu installer is going to play nice with this SATA hardware. I really hate to wait until the next version comes out. I bought this box specifically for Ubuntu. 

Any help would be appreciated greatly.

Scott D

---

### Post by grus on 2005-11-30
I've finally been able to successfully install breezy (both amd64 and i386 works) on my Dell Dimension 9100. To enable the installer to correctly detect both SATA and IDE drives, choose Raid Autodetect/ATA mode in BIOS. Unfortunately the cdrom only works using DMA in this mode (you will get CRC error on files if not), and you have to install ubuntu in expert mode.
To enable DMA for cdrom either enter -d1 as parameter to the cdrom module, or enter the console and type hdparm -d1 /dev/hda.

Good luck.

---

### Post by jdong on 2005-11-30
I've been having problems with crappy BIOS chipsets, especially those with dual SATA controllers (like the typical VIA+Promise setup that Asus utilizes)...

The correct boot sectors do not show up when either (or both) controller is in RAID mode...

For example, this is my setup:

CH0 CH1 } RAID0  array, Windows fun
CH2 } standalone SATA drive, Ubuntu target

Now, whenever I try to write a MBR to CH2, the contents are sent to the CH0+CH1 array. Whether or not I plug in the RAID0 array **affects what shows up as the MBR on CH2**! So apparently the BIOS does some kind of redirection for MBR access attempts, which can SERIOUSLY screw up boot sectors... Attempts to contact asus for further documentation has been ignored for a week now.

---

