---
title: "New to linux..."
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by Toddney on 2005-06-26
Ok, I've played aroudn with a couple different distro's of linux..and I really like Ubuntu..and I really want to learn linux..and I would love to dual-boot my PC.  I have an AMD 64 and I've downloaded the installation and the live cd.  From what I've seen of the Live cd..Ubuntu is an awesome distro..only one I've been able to get the internet working flawlessly.  Anyways..my questions are...I have one 40Gb (windows bootable) hard drive and another 80 Gb (one with my games) hard drive.  I would like to split my 80 gig...can I partition it through the install process of Ubuntu?  Or would I have to do it through like Partition Magic?  Also..do I have to install drivers or anything when I get Ubuntu installed?  Another question is..will I be able to listen to all my music that I have on my windows 40 gig hard drive through Ubuntu?  I don't know much about linux..I still have ot learn how everythign is stored, it's so confusing haha

---

### Post by Alexander Kirillov on 2005-06-26
[QUOTE=Toddney]Ok, I've played aroudn with a couple different distro's of linux..and I really like Ubuntu..and I really want to learn linux..and I would love to dual-boot my PC.  I have an AMD 64 and I've downloaded the installation and the live cd.  From what I've seen of the Live cd..Ubuntu is an awesome distro..only one I've been able to get the internet working flawlessly.  Anyways..my questions are...I have one 40Gb (windows bootable) hard drive and another 80 Gb (one with my games) hard drive.  I would like to split my 80 gig...can I partition it through the install process of Ubuntu?  Or would I have to do it through like Partition Magic?  Also..do I have to install drivers or anything when I get Ubuntu installed?  Another question is..will I be able to listen to all my music that I have on my windows 40 gig hard drive through Ubuntu?  I don't know much about linux..I still have ot learn how everythign is stored, it's so confusing haha[/QUOTE]
 Here are some answers:
 1. You can use Ubuntu installer to re-partition the 80Gb drive for Ubuntu. Make sure you run Windows disk-defragmenting tool on it  before starting installation, though. ANd, as usual, be very careful with   partitioning - double and triple-check your choices before you hit OK button. 

 2. Greater majority of hardware should work with drivers included in Ubuntu - no need to download anything else. Notable exceptions: 
  - Video cards: Nvidia and ATI cards work with default drivers, but no hardware acceleration. If you want accelerated graphics, you'll need to install proprietary drivers 
  - wireless cards: if your card uses one of the chips for which there is no free driver, then you would need to install ndiswrapper (but then, you said internet worked fine with live CD?)
  - modem: many so-called "winmodems", or software modems, require special efforts to get them working 
 
 3. You will be able to read all your files on windows hard drive from Ubuntu (after some manual configuring) - in particular, to listen to the music. However, if your windows uses NTFS filesystem, you will not be able to write to it - it can be accessed read-only. FAT32 can be read and writen to. 

Good sources of information: 
 - ubuntuguide.org
 - HOWTOs forum: [http://ubuntuforums.org/forumdisplay.php?f=58](http://ubuntuforums.org/forumdisplay.php?f=58)

---

### Post by wylfing on 2005-06-26
[QUOTE=Alexander Kirillov]
 1. You can use Ubuntu installer to re-partition the 80Gb drive for Ubuntu. Make sure you run Windows disk-defragmenting tool on it  before starting installation, though. ANd, as usual, be very careful with   partitioning - double and triple-check your choices before you hit OK button. 
[/QUOTE]
**WARNING!** Repartitioning a disk is destructive. You should expect to lose all data on the disk. Before running a disk partitioning tool, back up everything on the disk.

By running the Windows defragmenter, you'll have a nonzero chance of your data being intact after repartitioning. However, do NOT count on it. Back up your stuff!

---

### Post by irusun on 2005-06-26
[QUOTE=wylfing]**WARNING!** Repartitioning a disk is destructive. You should expect to lose all data on the disk. Before running a disk partitioning tool, back up everything on the disk.

By running the Windows defragmenter, you'll have a nonzero chance of your data being intact after repartitioning. However, do NOT count on it. Back up your stuff![/QUOTE]
That sounds a little heavy.  I think Wylfing is only pointing out that you should definitely back up any important data - there is always the *possibility* that you will lose all data on the disk - whether to user error or a software bug.  Most of the time though, it works fine.  And this goes for any partition managing utility, whether it's partman, parted, partition magic, etc.

---

### Post by Toddney on 2005-06-26
Cool, thanks for the replies guys.  I plan on picking up Linux For Dummies (yes i know it's sad) just to help me out with how the whole file system works.  It should also help me with start using the terminal in most cases.  Any other useful tips?

---

### Post by Alexander Kirillov on 2005-06-26
[QUOTE=Toddney]Cool, thanks for the replies guys.  I plan on picking up Linux For Dummies (yes i know it's sad) just to help me out with how the whole file system works.  It should also help me with start using the terminal in most cases.  Any other useful tips?[/QUOTE]
 If everything wors as it should, you shouldn't need to understand how filesystem works - yopu should only know how file manager works.. In real life, sometimes you do need to know the internals...

---

### Post by Toddney on 2005-06-26
Hey one more question!  Ok, to make my life easier and the hopes of not endangering my games on my 80Gig hard drive, I found an extra 80 gig hard drive in one of our older computers, so I put it in there...and I will probably just use that for linux.  Now when it asks me to install the bootloader..how do I go about doing this so it asks me on startup which OS to boot to? (XP or Ubuntu)?  I know I install the acutal OS on my spare 80 Gig...but do I install the bootloader on teh 40 gig that has my windows OS on it?

---

### Post by irusun on 2005-06-26
[QUOTE=Toddney]Now when it asks me to install the bootloader..how do I go about doing this so it asks me on startup which OS to boot to? (XP or Ubuntu)?  I know I install the acutal OS on my spare 80 Gig...but do I install the bootloader on teh 40 gig that has my windows OS on it?[/QUOTE]
The default bootloader for Ubuntu is "grub" - and yes, that would be installed on your boot drive (the 40 gig).  Ubuntu should automatically add Windows to your grub menu.lst file, so when you boot, you can choose between Ubuntu and Windows.

---

### Post by mingus on 2005-06-26
[QUOTE=irusun]The default bootloader for Ubuntu is "grub" - and yes, that would be installed on your boot drive (the 40 gig).[/QUOTE]

This is the default and typical choice, which overwrites the W$ Master Boot Record with grub; there are other methods, too.  I strongly recommend that you have the W$ media to recover the MBR in case of a grub install problem, either a W2K/XP install CD or a W98/ME/DOS bootable floppy.

---

### Post by Toddney on 2005-06-26
I'm scared, haha I don't want to mess up my Windows MBR...but another question that I read about..should I worry about partitioning my new 80gig with a FAT32 partition..so i can transfer files easily between windows and linux?  or not worry about it?

---

### Post by mingus on 2005-06-26
[QUOTE=Alexander Kirillov]Make sure you run Windows disk-defragmenting tool on it  before starting installation, though[/QUOTE]

Defragging will eliminate most of the data movement required, but bad sectors or filesystem pointers can still cause partitioning to choke.  For extra safety run chkdsk /r before defragging.

---

### Post by wylfing on 2005-06-28
> **mingus]Defragging will eliminate most of the data movement required, but bad sectors or filesystem pointers can still cause partitioning to choke.  For extra safety run chkdsk /r before defragging.[/QUOTE]
And this is why I said to back up   said:**
> I'm scared, haha I don't want to mess up my Windows MBR
Once again, I advise you to back up your data. The install process should work fine, and when you boot you should see a nice menu asking which OS you want to run, and they should all run without a problem. But things do go wrong. In rare cases, people are unable to boot Windows anymore. So back up, and have your Windows install media prepared in case the worst happens.

[QUOTE=Toddney]should I worry about partitioning my new 80gig with a FAT32 partition..so i can transfer files easily between windows and linux? or not worry about it?[/QUOTE]
I assume you are talking about the drive you're going to install Ubuntu onto. While this would theoretically work, I would feel uncomfortable giving Windows read/write access to my Linux installation. It might think it needs to "fix" an "error" or something equally disastrous. You're better off making your older 80 GB drive FAT32 and sharing files back-and-forth through that.

---

