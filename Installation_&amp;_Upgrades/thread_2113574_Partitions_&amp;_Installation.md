---
title: "Partitions &amp; Installation"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by ChrisInNevada on 2013-02-07
I am new to Ubuntu and have always used Windows OS.  Due to some political activism, I have come under ongoing cyber attacks and invasions of my overall electronic privacy.  Ubuntu was recommended to me as a slightly more secure operating system than Windows.  I am not sure if that is the case or not, however, if I do decide to install Ubuntu along side of Windows, what is the best way to partition?  I am not sure if I should leave some space for Windows or just close up shop there and trust Ubuntu.  I am reluctant to dump Windows entirely as I have several important documents filed away there.

---

### Post by sudodus on 2013-02-07
Welcome to the Ubuntu Forums :-)

I'm glad you ask before you try, because we can help you to avoid some mistakes. It will be easier to help you, if you describe your computer

- brand name and model (if you want to)
- desktop, laptop, netbook, workstation ... 
- cpu
- ram
- hdd (size, and how much is occupied/free)
- graphics chip/card
- wifi chip/card (if any)

So, please reply quickly with the computer specs, and look at this link
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
while you are waiting for replies with tips what to do.

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by ChrisInReno2 on 2013-02-08
Wow, totally unbelievable that I had to establish a new account on this forum because my password was not being accepted and neither were any of the temporary password resets sent to my email.  Total FAIL in that area.  What's up with that?

Thanks for responding to my previous question.

I have a Dell Inspiron n5110
640 HD
Intel Core i5-2410 M 2.3 Ghz x 4
64 bit

I have tons of free space.

I have never run more than one OS on a single machine.  I'm wondering what some of the potential unforeseen problems or issues might be such as how large should each OS partition be, ect?   My main concern is with security.  As I mentioned, I'm under cyber attack through Windows and wish to avoid further trojan hacks to restore some level of privacy.  I have been told that this platform is more secure than Windows.

Any insights into the pros and cons of running two operating systems would be appreciated.  Thanks!

---

### Post by ChrisInReno2 on 2013-02-08
Another concern I have is opening Ubuntu up to my documents stored in Windows.  I have read some Ubuntu documents that indicate that using Wine can open access to Windows virus and trojans.  This is precisely what I am trying to avoid.  Any thoughts or insights there would also be helpful.  Thanks!

---

### Post by ChrisInNevada on 2013-02-08
Ok, just realized my log in error was my error.  It always helps to use the correct user ID.

---

### Post by ke5sfy on 2013-02-08
One thing I have done recently was to install an internal drive bay adapter that lets me swap physical hard disks into the same slot.  If I want Windows, then I power down, remove the Ubuntu disk, insert the windows disk and boot the system.  This allows me to boot any O/S I want without the trouble of reconfiguring GRUB.  GRUB is the boot loader of choice for Ubuntu and other Debian based Linux systems.  During my last hardware upgrade I installed a second drive bay which allows me to copy all of my home folder to a second disk and then eject that disk for safe keeping.  The bays I used can be found on Newegg here:   [http://www.newegg.com/Product/Product.aspx?Item=N82E16817990014](http://www.newegg.com/Product/Product.aspx?Item=N82E16817990014)

I converted to Ubuntu three years ago on my home system and if I run windows at all it is under VirtualBox .  Linux is much more stable and does a much better job of handling and recycling memory unlike windows.

ke5sfy

---

### Post by sudodus on 2013-02-08
> **ChrisInReno2 said:**
> ...
I have a Dell Inspiron n5110
640 HD
Intel Core i5-2410 M 2.3 Ghz x 4
64 bit

It has the horsepower to run any of the Ubuntu Flavours, [vanilla] Ubuntu with fancy Unity desktop environment, Lubuntu ultra light-weight with LXDE, Xubuntu light-weight XFCE or Kubuntu with fancy KDE desktop environment.

But according to Dell's spec pages, there can be different graphics chips in that model. Can you find out about that (using the Control Panel in Windows)?
> 
I have tons of free space.

Good! Then we can help you to shrink the disk space for Windows and create an extended partition with a root partition for Ubuntu and a swap partition inside it. Unless you want to dispose of Windows completely.
> 
I have never run more than one OS on a single machine.  I'm wondering what some of the potential unforeseen problems or issues might be such as how large should each OS partition be, ect?   My main concern is with security.  As I mentioned, I'm under cyber attack through Windows and wish to avoid further trojan hacks to restore some level of privacy.  I have been told that this platform is more secure than Windows.

What version of Windows are you running? Windows 7 or 8? If it is a new Windows system, it might be more complicated to make a dual boot system. Can you find out in the BIOS/UEFI menu, if BIOS or UEFI is used?

Anyway, if you decide to wipe Windows, it might be a good idea to backup a complete image of the drive (so that you can restore the system if you change your mind). And you should make a simple backup copying your personal files (documents, pictures etc) before continuing. So get an external drive (USB3 or eSATA) for the backup if you don't have one already.
> 
Any insights into the pros and cons of running two operating systems would be appreciated.  Thanks!

When you have installed a dual boot system, it is rather straightforward to run. The only thing to remember is that you should avoid hibernating, because if you boot into the other system after hibernation, what you did after last reboot or poweroff might be partially lost.

Anyway, I suggest that you download iso files for Ubuntu 12.04 LTS (and/or the other flavours Lubuntu, Xubuntu, Kubuntu, which is easy if you have a fast internet connection). Burn boot CDs from the iso files but don't install at once. Nota bene: ***You should make a boot CD from the iso file by an imaging operation***. Do ***not*** simply 'copy' the file (as you would with a data CD or DVD).

An alternative is to make a boot USB drive with the tool Unetbootin. You can download ***Unetbootin*** to Windows to make a boot drive of a USB pendrive (preferably a USB 3 pendrive, which will be much faster than a standard USB 2 drive. (Once in Ubuntu, you can install the linux version of Unetbootin.)

Try them (running a live session) booted from the CD(s) and test which of the flavour you like the best. If you have problems, post it here, and we are many people who can help (if I'm not on-line, others will be).

Once you know what you want, we can help you either to prepare for dual boot with new partitions for Ubuntu or to wipe Windows. From the live session you run gparted to prepare the partitions and file systems. And from the same live session, you can install [KLX]Ubuntu.

---

### Post by roten on 2013-02-08
You can also try*** tails*** See this link

[https://tails.boum.org/download/index.en.html](https://tails.boum.org/download/index.en.html)

---

### Post by ChrisInNevada on 2013-02-08
Thanks everyone for all the great info!  I'm trying to get through the begin stages of learning an entire new OS.  

Sudodus, I am running windows 7.  I will have to get back to you on the graphics specs.  I am already set up with an external hard drive so I'm good to go with back ups.

---

### Post by ChrisInNevada on 2013-02-08
I was speaking with a tech today who suggested doing a fresh install of Ubuntu and creating a virtual box for windows 7.  Does this sound like a good idea?

---

### Post by sudodus on 2013-02-09
> **ChrisInNevada said:**
> I was speaking with a tech today who suggested doing a fresh install of Ubuntu and creating a virtual box for windows 7.  Does this sound like a good idea?

If you have an installation CD/DVD for Windows 7 with a licence key, yes.

But If you have only the installation in the computer and some rescue disk or rescue partition or a complete cloned image, it will probably only install into the same computer, not install into VirtualBox, because the virtual machine is 'another computer' and there is a copy protection feature in Windows to prevent that.

That is not a problem with free software, so Ubuntu is portable. If you avoid installing proprietary software, an installed system will be portable (to be cloned to another internal drive or to an external USB or eSATA drive). In other words, you can have your whole computer environment in a pendrive, and boot it in most computers with intel and amd CPUs.

---

### Post by ChrisInNevada on 2013-02-09
Sudodus, thanks again.  I do have a Windows 7 license key.  I think I will research how to install a virtual box for Windows.  It seems to me to be more efficient than a dual boot system.

---

### Post by ChrisInNevada on 2013-02-09
I believe I have an Intel(R) HD Graphics 3000 video chip. ?

---

### Post by ChrisInNevada on 2013-02-09
Sudodus, I'm not sure what you mean here:
 
***"You should make a boot CD from the iso file by an imaging operation***. Do ***not*** simply 'copy' the file (as you would with a data CD or DVD)."
 
I have downloaded and burned Ubuntu 12.10 to test drive the OS.  This disk also includes installation files.  Is this the boot CD described above?
 
You also recommended I install 12.04.  Why do you recommend 12.04 over 12.10?  Thanks again!

---

### Post by sudodus on 2013-02-09
> **ChrisInNevada said:**
> I believe I have an Intel(R) HD Graphics 3000 video chip. ?
Then I think that Ubuntu will work well with a built in driver, so you need not worry about the graphics.
--
Can you find out if Windows is booted from BIOS or UEFI? If BIOS, it is 'straight-forward' to install a dual boot system, while it is difficult but possible with UEFI (sometimes called EFI).

---

### Post by sudodus on 2013-02-09
> **ChrisInNevada said:**
> Sudodus, I'm not sure what you mean here:
 
***"You should make a boot CD from the iso file by an imaging operation***. Do ***not*** simply 'copy' the file (as you would with a data CD or DVD)."

See for example this link

[[COLOR="red"]http://www.ubuntu.com/download/help/burn-a-dvd-on-windows[/COLOR]]("http://www.ubuntu.com/download/help/burn-a-dvd-on-windows")
> 
I have downloaded and burned Ubuntu 12.10 to test drive the OS.  This disk also includes installation files.  Is this the boot CD described above?
 Probably. Try it!> 
You also recommended I install 12.04.  Why do you recommend 12.04 over 12.10?  Thanks again!

1. Because 12.04 is a version with long time support, LTS, until April 2017, while 12.10 reaches end of life in April 2014.

2. Because 12.04 has had longer time to mature (bugs are found and removed). Unless you want bleeding edge software, LTS versions are recommended, since it causes much less problems. The only other reason to select the newest version is if you have new hardware or firmware, that is not recognized by an aging LTS version.

---

### Post by ChrisInNevada on 2013-02-09
Sudodus, thanks, my Windows 7 boots from Bios.  I have nothing indicating a boot from UEFI.

---

### Post by sudodus on 2013-02-09
> **ChrisInNevada said:**
> Sudodus, thanks, my Windows 7 boots from Bios.  I have nothing indicating a boot from UEFI.
Good luck looking for a way to install your Windows to VirtualBox :-) You may find a way, that I don't know about.

Otherwise, I think I can guide you to get a working dual-boot installation with Windows and Ubuntu (with BIOS). Many people at the Ubuntu Forums have done it, so you can get help easily and quickly if I would be absent for a while.

---

### Post by ChrisInNevada on 2013-02-09
Sudodus, I found this on installing Windows 7 to a virtual bow in Ubuntu:
 
[http://askubuntu.com/questions/207308/how-do-i-use-virtualbox-and-install-windows-7](http://askubuntu.com/questions/207308/how-do-i-use-virtualbox-and-install-windows-7)

---

### Post by ChrisInNevada on 2013-02-09
Ok, so I have decided to install 12.04.  However, there are 2 partitions on my current hard drive.  Are these both associated with windows 7 or is the hidden drive associated with my bios?  I am thinking the hidden partition is windows associated due to windows office starter programs, etc. but am hesitant to over write both drives without being certain of this.  Thanks!

---

### Post by ChrisInNevada on 2013-02-09
Both partitions, that is, not both drives.

---

### Post by ChrisInNevada on 2013-02-09
I found the answer I was looking for.

---

### Post by sudodus on 2013-02-09
> **ChrisInNevada said:**
> Ok, so I have decided to install 12.04.  However, there are 2 partitions on my current hard drive.  Are these both associated with windows 7 or is the hidden drive associated with my bios?  I am thinking the hidden partition is windows associated due to windows office starter programs, etc. but am hesitant to over write both drives without being certain of this.  Thanks!

Probably both partitions belong to Windows, I think the hidden one is a rescue partition.

If you are still not sure, post the output describing the partitions!

---

### Post by sudodus on 2013-02-09
> **ChrisInNevada said:**
> Sudodus, I found this on installing Windows 7 to a virtual bow in Ubuntu:
 
[http://askubuntu.com/questions/207308/how-do-i-use-virtualbox-and-install-windows-7](http://askubuntu.com/questions/207308/how-do-i-use-virtualbox-and-install-windows-7)

As far as I can understand, you need a license key to install Windows 7 to a virtual machine. I find nothing stating the opposite in your link. So I still recommend that you shrink the Windows partition and install a dual boot, unless you really want a pure Ubuntu installation and are prepared to pay for a new Windows 7 license (and waste the existing one) ... or skip Windows.

If you choose the dual boot alternative, then I suggest that you use Windows to shrink your Windows partition. And then you use the unallocated space to install Ubuntu. Tell us how big is the drive and how much disk space much is used and free! Then we can discuss partitions sizes before you go ahead.

---

### Post by n4pgw on 2013-02-10
> **ke5sfy said:**
> One thing I have done recently was to install an internal drive bay adapter that lets me swap physical hard disks into the same slot.  If I want Windows, then I power down, remove the Ubuntu disk, insert the windows disk and boot the system.  This allows me to boot any O/S I want without the trouble of reconfiguring GRUB.  GRUB is the boot loader of choice for Ubuntu and other Debian based Linux systems.  During my last hardware upgrade I installed a second drive bay which allows me to copy all of my home folder to a second disk and then eject that disk for safe keeping.  The bays I used can be found on Newegg here:   [http://www.newegg.com/Product/Product.aspx?Item=N82E16817990014](http://www.newegg.com/Product/Product.aspx?Item=N82E16817990014)

I converted to Ubuntu three years ago on my home system and if I run windows at all it is under VirtualBox .  Linux is much more stable and does a much better job of handling and recycling memory unlike windows.

ke5sfy

Rather than swap drives, I have installed an additional drive just for Ubuntu.  It creates a boot manager on the primary drive and allows access to Ubuntu and windows at boot time.  

I learned the hard way that it is easier to install windows first before ubuntu. If you need to install windows after Ubuntu is installed, disconnect the ubuntu drive first.  Then repair the ubuntu boot manager.

---

