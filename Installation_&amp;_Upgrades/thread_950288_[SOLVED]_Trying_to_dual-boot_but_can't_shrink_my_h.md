---
title: "[SOLVED] Trying to dual-boot but can't shrink my hard drive..."
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by Virtualboxbuntu on 2008-10-17
I have Vista on my 200GB partition and I'm trying to shrink it so I can install Ubuntu on a 40GB partition (that doesn't exist yet). No matter what I try from within Windows, it insists that access is denied.

Can I safely use GParted or another LiveCD to shrink it? I've heard about how you need your Vista Installation disk to repair Windows if you do this (I don't have it). I've been trying for a week now trying to figure out how to shrink my partition.

BTW: I don't really want Windows anyway, it's only for some Windows-only games.

BTW: I'm new to the forums. I don't know if this is the right category or not.

---

### Post by cybergalvez on 2008-10-17
> **Virtualboxbuntu said:**
> I have Vista on my 200GB partition and I'm trying to shrink it so I can install Ubuntu on a 40GB partition (that doesn't exist yet). No matter what I try from within Windows, it insists that access is denied.

Can I safely use GParted or another LiveCD to shrink it? I've heard about how you need your Vista Installation disk to repair Windows if you do this (I don't have it). I've been trying for a week now trying to figure out how to shrink my partition.

BTW: I don't really want Windows anyway, it's only for some Windows-only games.

BTW: I'm new to the forums. I don't know if this is the right category or not.

Not with Vista, from what I've read and from personal experience it will mess up your Vista partition
Jose

---

### Post by cariboo on 2008-10-17
Use the Vista disk management applet to resize you hard drive, before you resize you should defrag your hard drive at least twice.

Jim

---

### Post by Virtualboxbuntu on 2008-10-17
> **cariboo907 said:**
> Use the Vista disk management applet to resize you hard drive, before you resize you should defrag your hard drive at least twice.

Jim

I have defragged dozens of times.

That's what I'm trying to do. Whenever I click Shrink it says Access Denied. Does the same thing on the cmd with diskpart.

---

### Post by lincoln32 on 2008-10-17
it will deny if you are using that partion for operating system. I did the duel boot with vista using a live g parted disk and found it easy to do and worked well till i gave up on windows for good. also you may want to add a home partion due to all your documents and setting will be saved in home partion and you can change any linux system and upgrade and not have to save or relace settings or files saved

---

### Post by Mark Phelps on 2008-10-17
Regarding using GParted to shrink the Vista volume ...

Sometimes it works, sometimes it doesn't -- and when it doesn't it hoses up your Vista installation so it won't boot anymore.  If you have a Vista DVD, you can boot from it, run a startup repair, and you should be OK.  If you don't have a Vista DVD, and you don't have a recovery CD, you won't be able to repair the Vista installation.

There appears to be no way ahead of time to predict whether or not the resizing will cause problems.

---

### Post by caljohnsmith on 2008-10-17
Virtualboxbuntu, although it is of course more ideal to shrink Vista with its own software, you can still do it with gparted, but as mentioned you will most likely have to do a minor repair on Vista to get Vista booting OK again. I've seen a number of threads in these forums of people who have shrunk Vista with gparted and then got Vista working OK again as long as they could use their Vista Install/Recovery CD to do a repair (or there are a few specific commands you can use instead); I have only come across maybe one or two threads of someone who could not get Vista working again after resizing it with gparted, but I'm pretty sure there were other factors involved. Anyway, I think the odds are in your favor that you'll be just fine. :)

Since you don't have a Vista Recovery CD, you can download one from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let us know how it goes. :)

---

### Post by Pumalite on 2008-10-17
Disable your PageFile before shrinking.

---

### Post by Virtualboxbuntu on 2008-10-17
> **lincoln32 said:**
> it will deny if you are using that partion for operating system. I did the duel boot with vista using a live g parted disk and found it easy to do and worked well till i gave up on windows for good. also you may want to add a home partion due to all your documents and setting will be saved in home partion and you can change any linux system and upgrade and not have to save or relace settings or files saved

Perhaps you can advise on how big my /home partition should be, on a 40GB hard drive?

I've shrunk my system partition from Disk Management before. I don't know why it's refusing now.

---

### Post by Virtualboxbuntu on 2008-10-17
> **caljohnsmith said:**
> Virtualboxbuntu, although it is of course more ideal to shrink Vista with its own software, you can still do it with gparted, but as mentioned you will most likely have to do a minor repair on Vista to get Vista booting OK again. I've seen a number of threads in these forums of people who have shrunk Vista with gparted and then got Vista working OK again as long as they could use their Vista Install/Recovery CD to do a repair (or there are a few specific commands you can use instead); I have only come across maybe one or two threads of someone who could not get Vista working again after resizing it with gparted, but I'm pretty sure there were other factors involved. Anyway, I think the odds are in your favor that you'll be just fine. :)

Since you don't have a Vista Recovery CD, you can download one from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let us know how it goes. :)

Ok, I'll try that. Making the recovery CD publicly available is probably the first thing Micro$oft has done properly. :lolflag:

I downloaded the CD and I'm going to boot it before I shrink anything to make sure it works.

Will PartedMagic work instead of GParted (I already have it on a CD)?

---

### Post by Virtualboxbuntu on 2008-10-17
> **Pumalite said:**
> Disable your PageFile before shrinking.
I've read that some programs don't work without a page file. Is it safe to disable my page file? And how do I disable it, anyway?

---

### Post by alex1996arm on 2008-10-17
or you can just use wubi to install inside windows

---

### Post by alex1996arm on 2008-10-17
you know wubi?
just put your 8.04 cd into the drive while windows is running and follow the on-screen instructions

---

### Post by ShinobiTeno on 2008-10-17
> **Virtualboxbuntu said:**
> I've read that some programs don't work without a page file. Is it safe to disable my page file? And how do I disable it, anyway?

Yes it is safe,if you have >=1GB of ram, it should fit and work. Do a minimal boot, disable all unnecessary programs from autostart. Last os I used was XP, but i bet they didnt change anything, it was <WindowsKey>+<Pause/Break>. It should bring up System MSGBox. Search for VirtualMemory in one of the tabs.

Btw, i dont know, it could be that u cant resize the disk, cause its system(C). Commercial progs do this good(Acronis DiskDirector, do NOT use PartitonMagic>it has bugs and is depricated).

You can also do a search for Hiren BootCd, and burn-boot it. Its unofficial admin cd in *doze world, but it has halflegal status (unlike in linux, win32 progs are $$$ware, but makin such cd legally would cost billions of $). I bet for one, noncommercial , oneway use its nothin. Just trying to save u several days of unneeded troubles...

... and welcome to Linux!:guitar:

---

### Post by Pumalite on 2008-10-17
> **Virtualboxbuntu said:**
> I've read that some programs don't work without a page file. Is it safe to disable my page file? And how do I disable it, anyway?
Make it '0' before shrinking and later return it to its normal value.

---

### Post by Virtualboxbuntu on 2008-10-17
I know, but I really want Ubuntu as a normal operating system. I'd rather have a Linux-only system with Windows in Virtualbox than Windows+Wubi. Unfortunately I don't have the Windows install disk, otherwise I'd do that.

---

### Post by Virtualboxbuntu on 2008-10-18
I'll try disabling the paging file. It's actually under systempropertiesadvanced.exe in Vista. I have 2GB of RAM, so it should work. At least, that's what Shenobi says...

I'll post back when I find out if it'll let me shrink.

Linux partitioning is so much easier *sighs*

---

### Post by Virtualboxbuntu on 2008-10-18
Aaarrrgh. I disabled the page file, booted into Safe mode and logged into the master administrator account. I opened Disk Management. I click Shrink and entered the information. It loaded for five minutes (I heard it writing to the hard drive) then insisted that my access was denied. Same thing with DISKPART.

So now I'm back here with my page file re-enabled. I've burned the Vista Repair CD, my Linux install CD, and I'm downloading the GParted CD. I plan to use GParted to shrink since vista is being a pain in the you-know-where. Is there anything I should know before I resize with GParted? Should the page file be enabled or disabled?

I just realized something - I have three primary partitions already (one system drive, one recovery drive, and one I made for storing my videos (it worked from Disk Management a year ago)). That means I need all logical partitions for Linux. Can Linux run off a logical partition? I know Windows can't. :confused:

---

### Post by ShinobiTeno on 2008-10-18
Be careful when messing with Vista partitions, afaik its much more jealous when someone messes with its "C:" disk, then XP or 2K) **Be sure to make backups** and be prepared to reinstall the system from scratch up in the worst case. At least be prepared for vista to refuse to boot.

I suspect you cannot resize, cause its "C:" and always locked. As I sayd, Disk Director can resize in offline, when system is still booting, thus only known tool that can resize "C:" from "C:".

> **Virtualboxbuntu said:**
> That means I need all logical partitions for Linux. Can Linux run off a logical partition? I know Windows can't.

Afaik yep, provided you manage to load its kernel, / can reside within logical partition =). You can boot if you use a bootcd/usb/floppy, create a separate, small primary "/boot" partition in the beginning, or ... [use windows bootloader to start the kernel. ]("http://www.tprthai.net/bootmgr.htm") Primary partition marked with Active flag is needed to kickoff the bootloader, if its flexible enough, it`ll do it.

Why dont you just drop all data somewhere and do a total re-GParted`ing))

---

### Post by caljohnsmith on 2008-10-18
> **ShinobiTeno said:**
> 
Afaik yep, provided you manage to load its kernel, / can reside within logical partition =). You can boot if you use a bootcd/usb/floppy, create a separate, small primary "/boot" partition in the beginning, or ... [use windows bootloader to start the kernel. ]("http://www.tprthai.net/bootmgr.htm") Primary partition marked with Active flag is needed to kickoff the bootloader, if its flexible enough, it`ll do it.

Why dont you just drop all data somewhere and do a total re-GParted`ing))
He shouldn't have to use a boot CD, USB drive, or floppy to boot Ubuntu unless there are special circumstances like having Grub out of the range that BIOS can access, or in the case of trying to boot a USB drive with a computer that does not boot USB devices. Most likely, if he has a relatively recent computer, he should not have any problem and not have to create any boot CDs or anything. :)

---

### Post by Virtualboxbuntu on 2008-10-18
A total GParted resizing never occured to me. I'll back up my videos to my external drive. Since my other 100GB partition isn't a system partition Vista shouldn't mind.

If Vista gets messed up and the repair CD doesn't work, I have the factory recovery discs, but I will probably not bother with them. I would be much better off with a Linux-only system than a Windows-only system. But I'd prefer a dual-boot system if I can have one.

It will be so much better than Windows... no defragmenting, no viruses...

---

### Post by Virtualboxbuntu on 2008-10-19
I installed Linux a few hours ago, and had no problems at all. I didn't even have to use GParted, Disk Management let me delete my 100GB partition.

I used to think that Aero was cool, but now it sucks compared to compiz fusion.

Thanks for all your help guys!:KS

---

### Post by Tharmas on 2008-10-27
Hi,Virtualboxbuntu
Could you please elaborate on what you exactly did to solve your problem? And what do you exactly mean with "*A total GParted resizing*"?
I don't have windows but I'm trying to help out a friend (she plans to install Ubuntu keeping Vista) with the same problem as you?

---

