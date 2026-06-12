---
title: "How to Install Ubuntu on External HDD from Windows?"
date: 2016-06-24
forum: Installation &amp; Upgrades
---

### Post by dj505 on 2016-06-24
Hi all!
Quick question. Is there any way to use Windows to install Ubuntu on an external drive without using live media? Like plugging the external drive into the computer and writing the ISO file? Or do I have to use live media of some sort?

---

### Post by sudodus on 2016-06-24
You can install the live system into the external HDD, but I think you mean something else, to get an installed system directly.

Then it is possible to install from a compressed image file directly to a HDD, SSD, or pendrive (internal or external), but from a system running in one drive to another drive (and to overwrite what is in that drive.

See this link: [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

It is also possible to boot a live session directly from an iso file via grub and from there install into the external HDD. This is in principal similar like using live media, but you need no extra drive, you can boot from an iso file that is stored in your internal HDD via an extra menu entry in the grub menu. I call this method 'grub-n-iso'. See for example the following link

[Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

[Manually editing the GRUB files](https://help.ubuntu.com/community/Grub2/ISOBoot#Manually_editing_the_GRUB_files)

---

### Post by TheFu on 2016-06-24
"any way" - sure.  You can mirror an existing, working, Linux setup. Just use a bit-for-bit copy tool. Any of those will work, unless it is UEFI. Then things are probably different and I can't help. Don't touch UEFI systems.  I've moved a Linux install (physically just moved the HDD) from a Pentium4 to a Core i7 box without major issues.  Just the networking and GPU drivers needed a little help.

There are also mini-installers. and server installers. Neither of these are "live CD" media.

Perhaps if you describe the end-goal, we can suggest the best way to accomplish it?

---

### Post by dj505 on 2016-06-24
My main end goal here is just to install Linux to a hard drive and stick it in an old computer dedicated to run some old arcade games, which I've done previously on Linux. Just need a way to install Linux on a hard drive seeing as I only have a Windows PC and no flash drives or flash drives available, just an external hard drive.

---

### Post by yancek on 2016-06-24
You don't need live media such as a CD/DVD/flash drive to install Linux.  You can boot many Linux iso files directly and install to another hard drive.  You can boot an extracted Linux iso copied to a partition on a hard drive and use it to install.  You can boot a windows extracted iso from a partition on a hard drive and use it to install windows.  For the first option you need Grub2, for the second and third options, you need Grub or Grub2.

So in your case, without a CD/DVD drive or a flash drive or a capable bootloader, the answer is no.   Probably the closest you could get it to do a hard disk install using unetbootin explained at their page below.  All this does though, is put a Live CD on the hard disk which is going to be read-only and you will be unable to save any changes on reboot.  You could also install just Grub2 and use that to boot but if you are not knowledgeable about the Grub bootloader, this will probably create more problems for you.

[https://sourceforge.net/p/unetbootin/wiki/installmodes/](https://sourceforge.net/p/unetbootin/wiki/installmodes/)

---

### Post by sudodus on 2016-06-25
> **dj505 said:**
> My main end goal here is just to install Linux to a hard drive and stick it in an old computer dedicated to run some old arcade games, which I've done previously on Linux. Just need a way to install Linux on a hard drive seeing as I only have a Windows PC and no flash drives or flash drives available, just an external hard drive.

The method to install linux from a compressed image file works also from Windows. You want to run it in an ***old*** computer. If you tell us more about the computer, it will be possible to give better advice, to suggest something, that is likely to work well in that computer. So please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

***Edit:*** A 'middle of the road' alternative is to install a persistent live system, but I think we can also help you get an installed system into your external drive. See also this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by yancek on 2016-06-25
I might be reading the question incorrectly but, from my reading of it the OP wants to boot either the downloaded iso directly or perhaps the extracted iso from his windows bootloader which is the only OS he has installed.  An unknown windows OS?  I don't see anything in the links posted above related to that.  He apparently has no usb or access to any and no CD/DVD so wants to boot from the HD.  Easily done with Grub or Grub2.  I know it is possible although more complex to boot an installed Linux from an old XP install or from bcdedit in newer windows.  I'd be curious to read about booting a Linux iso from windows.

---

### Post by TheFu on 2016-06-25
> **dj505 said:**
> My main end goal here is just to install Linux to a hard drive and stick it in an old computer dedicated to run some old arcade games, which I've done previously on Linux. Just need a way to install Linux on a hard drive seeing as I only have a Windows PC and no flash drives or flash drives available, just an external hard drive.

If you can install it into the disk temporarily installed a different PC, but targeting the settings for the final PC, that would be the easiest.
If the PC had a way to network boot, PXE boot, that could be done as well.  I've never done that with Ubuntu, but have with CentOS and fedora. Another PC, setup in a specific way (non-trivial) is required.

Sometimes it is easier to just buy a cheap computer which does support USB booting and use that.  Heck, a $35 R-Pi will be easier and probably faster and definitely lower power use.  Just had to put that out there. Completely understand if that isn't an option.  I have a few boxes to "reuse" that I'm unwilling to part from too.

Netboot an option? Do you have another PC to setup, even temporarily, to support a PXE install? It would need about 10G of disk and doesn't need to be completely dedicated.  Heck - if you have that, then perhaps installing the HDD from the target machine for an hour would be easiest.

A guide to using grub2 to boot an ISO off a HDD: [http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/](http://www.howtogeek.com/196933/how-to-boot-linux-iso-images-directly-from-your-hard-drive/) - don't think this will work without grub2 already installed and controlling windows boot.  

I've heard about **easyBCD** - as another alternative. Never used it myself. [https://neosmart.net/wiki/easybcd/portable-entries/iso-images/](https://neosmart.net/wiki/easybcd/portable-entries/iso-images/)

---

### Post by yancek on 2016-06-25
Reading in more detail the unetbootin page, I tried doing the 'frugal install' method which basically puts the iso on the windows partition and creates a 'unetbootin' entry in the windows boot menu.  Selecting it boots whichever Linux system you selected with unnetbootin and from there you can run the installer.  Probably in a case like this, it would be a good idea to create unallocated space before running unetbootin.

---

