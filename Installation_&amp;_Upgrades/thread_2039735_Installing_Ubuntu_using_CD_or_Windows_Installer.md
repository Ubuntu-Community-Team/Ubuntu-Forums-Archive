---
title: "Installing Ubuntu using CD or Windows Installer"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by WindsOfChange on 2012-08-09
Hi Members,

I just joined today and I am finally making the move to Linux. I'm installing Ubuntu on my windows 2000 computer that I built back in 2001. This computer has a server motherboard and is very stable and a workhorse. It has never let me down. Windows recently announced that they are no longer supporting IE6 via their automatic updates. 

My computer only runs IE6 as that was the last browser update for win2k. Thus my system has now been placed on life support because of the increased hardship of having to loacte win2k system files without updates.
   
  There is nothing wrong with my system but every now and then, a drive crashes and I have to re-install windows 2000. Now that I cannot get automatic updates, it becomes way more difficult to reinstall critical files. Yes I can do it manually by searching for files on the net but I'm tired of having to be "forced" to dig for drivers, system files and programs that used to be available to me at the click of a button. 

I always use Firefox for everything else. I only use IE6 for automatic updates via Microsoft's update page (that can only be accessed via Internet explorer 6 (IE6). 

My computer has a "dual" Pentium III "copper mine" CPU's, I have 1 gig of DDR memory (4 gig max on motherboard). VIA Apollo Pro Chipset and a 40 gig drive that is partitioned in the following order:

C drive: 15 gigs (contains the windows 2000 OS)

D drive: 15 gigs (for installing programs)

E drive: 8 gigs (used for storing data, documents etc.)

F drive: 1 gig (initially set up as a location for temp files but never used)

I'd like to install Ubuntu but not sure if I want to install via the CD image (which creates a partition) or as a virtual Drive (using it alongside windows). I have searched the net and read a lot of interesting articles but still not sure what path to choose. 

I primarily use my system for composing music on a Digital Audio Workstation using Sonar and a M-Audio Delta 98 sound Card. I also do video editing (using another program). I use Adobe Photoshop, study programming using Microsoft Visual Basic 2005, and follow the currency markets and stock markets using NinjaTrader 6.5 as well as a host of other interests. As you can see my system is used for many areas and they all function together well. I’d like to keep it that way after installing Ubuntu (if possible).

  Please help answer the following three questions. Thank you very much.
  [FONT=&quot]
**1st question please:**[/FONT]

1) What exactly is a virtual drive or virtual machine? I read terms like
   
   Virtual Box 
  Disk Image
  Virtual Machine
  Physical Host
  Host Computer’s File System
   
  I understand that “Virtual Box” is software that is installed on a windows computer and allows the user to install Ubuntu into the software to run alongside windows?
   
  I just can’t seem to understand the concept of “Virtual”. I do have “Virtual CloneDrive installed on my system as well as that is used to read and install programs that are downloaded in an ISO Image format.
   
  But virtual still confuses me. To me…storage is storage, no matter if its physical storage or virtual storage. The computer still needs to make “room” store either or both of these formats. Correct?
   
  **2nd question please**
   
  2) What is the best way to install Ubuntu? As a virtual drive or via the installation CD? I would like to utilize a full desktop Digital Audio Workstation (DAW) inside Ubuntu using either Ubuntu Studio, Muse, Rosegarden, Qtractor or Ardour. If Ubuntu was installed on a virtual drive, what performance issues might I run into verses installing a DAW into Ubuntu that was installed on an actual partitioned area on my hard drive?
   [B]
  3rd question please:[/B]
   
  3) Are we talking about a dual boot when running both windows 2000 and Ubuntu on a partitioned area or virtual drive? Or does the Ubuntu installation CD take care of all that configuration so when I boot up my system it will ask me if I want to run Win2k or Ubuntu?
   
  Thank you kindly for your help.

---

### Post by cortman on 2012-08-09
For a system with those specs, I'd recommend a lightweight Ubuntu derivative such as Xubuntu, Lubuntu, or Bodhi Linux (my personal preference is Bodhi). Don't bother with any virtualization if you don't want to keep Windows. Just boot from the CD and the installer will step you through. Just make sure you select the right HDD for installation.
And first and foremost, before you do any kind of installation BACK UP YOUR DATA. I can't stress that enough.

---

### Post by WindsOfChange on 2012-08-11
Hi Cortman. Thank you for the suggestions. I forgot to mention that I also have an extra 40 gig drive that I can install into my system. Will that help with the options I have for installing Ubuntu?

---

### Post by cortman on 2012-08-13
> **WindsOfChange said:**
> Hi Cortman. Thank you for the suggestions. I forgot to mention that I also have an extra 40 gig drive that I can install into my system. Will that help with the options I have for installing Ubuntu?

It depends what you want to use it for; personally I'd use it as a backup drive. Attach it before the installation and Ubuntu will automount it from then on. Just be sure you know which drive you're installing the operating system on.

---

### Post by jemadux on 2012-08-13
wubi is for testing not to use on daily base so burn a cd

---

### Post by WindsOfChange on 2012-08-27
Ok Thank you all. I will install from the CD

---

