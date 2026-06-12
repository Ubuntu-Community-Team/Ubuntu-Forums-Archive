---
title: "Installing without GRUB"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by Guybrush Threepwood on 2006-09-11
Hi,
I recently installed an Ubuntu system on my notebook. A few weeks later, I wanted to delete my Ubuntu partition so I did it from a partition manager located at the Windows partition.
However, GRUB had installed on that partition, so it was still there, but it wouldn't load properly. Finally, I decided to re-format all, and re-install just Windows.
Now, I'd like to have Ubuntu back, but without the burden of GRUB touching my Windows partition. If possible, I'd like not to install GRUB at all, and just use another boot-up manager (like Acronis OS Selector).
So, is it possible either to install GRUB just on Ubuntu's partition, or not to install it at all?
Thank you so much for your help.
PS: Sorry for my miserable English, but I'm not a native speaker.

---

### Post by ajgreeny on 2006-09-11
You need not have formatted and reinstalled windows, although you may not want to hear that now.  You should have simply repaired or reinstalled the windows MBR, which would have left windows exactly as it was.

I think if you use the alternative CD for install you get the option to put grub on another site or partition, but not if you use the live CD install.  You can even put it on a floppy if you have one on your machine.

Just out of interest, why do you think it a burden to put grub on your windows MBR?  If you're going to continue with ubuntu, or even another linux, it will make life so much easier if it is there rather than elsewhere.

---

### Post by coffeecat on 2006-09-11
Grub (stage 1) wasn't installed to the Windows partition, but to the mbr (master boot record) - the first few hundred bytes on the hard disk. It overwrote the Windows bootloader, which you could have restored with the 'fixmbr' command from the Windows install CD without having to re-install Windows.

Anyway, to answer your question, yes you can install Ubuntu without writing Grub stage 1 to the mbr but you have to use the alternate CD - not the live desktop CD. And you can use Acronis as a bootloader for both Linux and Windows - I've done this myself. What you should be aware of though is that Acronis also overwrites the mbr.

Let me make one comment and suggestion. Grub is a very good and versatile bootloader ideal for multibooting different OSs. Your problems arise from not understanding how it works. There are probably several good howtos for Grub on this forum, so may I suggest you look out for them? I, personally, am very happy with Grub now that I have learnt how to configure it.

---

### Post by confused57 on 2006-09-11
Using the alternate installation cd, you could install grub to floppy during install:
[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

That way, you could boot up with the floppy to start Ubuntu...or you could look into GAG or Super Grub Disk to boot with:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You'd need to install grub to the Ubuntu root partition(using the alternate cd) to use the GAG or Super Grub Disk.

---

### Post by Guybrush Threepwood on 2006-09-12
OK, thanks!

---

### Post by henteaser on 2007-10-11
I think this issue is still not clear. Is there any way to install Ubuntu without tampering on other operative systems (or their mbr:s)? Will this work if I install Ubuntu on another hard drive with my primary drive disabled, or do I have to manually disconnect the drive.

I don't like anything that installs without my permission, and installing grub on a floppy seems to be a tedious workaround. Many people don't have floppy drives anymore, that's not a good solution.

---

### Post by Joeb454 on 2007-10-11
> **henteaser said:**
> I don't like anything that installs without my permission

Surely the fact that your installing a Linux distro means that your allowing grub to overwrite the MBR.

And I prefer grub to the Windows Bootloader (even the Vista one, which is better than XP's). Purely because it's allowed me to dual-boot Ubuntu/Vista, and there's no way Vista would let me do that without some serious tweaking

---

### Post by henteaser on 2007-10-11
> **Joeb454 said:**
> Surely the fact that your installing a Linux distro means that your allowing grub to overwrite the MBR.


Yes overwrite the MBR on the drive I'm installing to — but not on any other drives. It's this devious behaviour that I dislike and that has hindered me from starting to use Ubuntu.

I guess grub is something that one must live with, but is there any way to make it only load ubuntu without asking anything (even for 0 seconds) and to only reside on the drive with ubuntu?

---

### Post by Herman on 2007-10-11
> I think this issue is still not clear. Is there any way to install Ubuntu without tampering on other operative systems (or their mbr:s)? Will this work if I install Ubuntu on another hard drive with my primary drive disabled, or do I have to manually disconnect the drive. If you install with the 'Alternate' CD, you will be able to install GRUB to any device you like, or even choose not to install GRUB anywhere at all. (however, that might be rather pointless unless you know what you are doing -boot with a [Super Grub Disk]("http://geocities.com/supergrubdisk/") maybe).

There is a MBR in the first sector of every formatted hard disk, and after that the rest of the first track of the hard disk is empty and not formatted with any operating system's file system. The MBR does not belong to any operating system,

The first hard disk's MBR is more important than the MBRs of other hard disks, (if present), because the BIOS usually only looks at the first hard disk's MBR when the computer boots up.

The boot sector of the Windows partition is not the same thing as a MBR, a boot sector is the first sector of an operating system's partition and that may contain code to load the boot loader. Windows boots by its boot sector, but Linux doesn't have anything in it's first sector by default, GRUB  or LiLo can be installed there though.
I would say that an operating system's boot sector is part of an operating system, because it's in an operating system's partition, whereas the MBR of a hard disk is not.

GRUB does not install to the Windows partition, not ever, (unless you force it to by mistake somehow),  and Ubuntu doesn't touch the Windows partition at all either. Not unless you tell it to. I don't know how people get the idea that that happens, I think people who say that are not well informed about the subject.

If you decide you don't want the MBR that belongs to your first hard disk changed, then you will need some way to boot Ubuntu. 

>  I don't like anything that installs without my permission, and installing grub on a floppy seems to be a tedious workaround. Many people don't have floppy drives anymore, that's not a good solution.> Yes overwrite the MBR on the drive I'm installing to &#8212; but not on any other drives. It's this devious behaviour that I dislike and that has hindered me from starting to use Ubuntu.

I guess grub is something that one must live with, but is there any way to make it only load ubuntu without asking anything (even for 0 seconds) and to only reside on the drive with ubuntu? Well you can install GRUB to MBR in your second hard disk then, and boot your second hard disk by pressing the F8 or F12 key, like Gn2 describes in this thread, [Dual Boot on Two Drives]("http://ubuntuforums.org/showthread.php?t=275728")
You can do it that way, but I think you will find that inconvenient and tedious after a while and decide to install GRUB to MBR in your first hard disk after all. But try that if you want, you are welcome to install Ubuntu and boot it any way you like.

Or you could use WinGrub, [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html")

Regards, Herman :)

---

### Post by Herman on 2007-10-11
There's also LiLo and GAG too, You don't have to use GRUB at all if you don't want to.
 [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html")                      LiLo the Linux Loader Page, about installing LiLo in Ubuntu and booting ,[GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")  GAG Boot Manager, a Windows and Linux booting alternative.

LiLo can be installed with the 'Alternate' CD as well, and to any device you like. 

Check my sig links for how to use the 'Alternate' CD to choose a boot loader and install it wherever you like.

I think that after you have tried all the alternatives you will eventually agree with the rest of us that it's most convenient and best to install GRUB to MBR in your first hard disk, if you are going to keep Linux for very long.

Regards, Herman :)

EDIT: Oh, I also have a [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html")    About Knoppix_V5.1.1DVD, you can use that without touching your hard drives at all and still be able to use much of the same great open source software that we al use.

---

### Post by henteaser on 2007-10-11
> **Herman said:**
> 
The first hard disk's MBR is more important than the MBRs of other hard disks, (if present), because the BIOS usually only looks at the first hard disk's MBR when the computer boots up.

---

If you decide you don't want the MBR that belongs to your first hard disk changed, then you will need some way to boot Ubuntu. 

 Well you can install GRUB to MBR in your second hard disk then, and boot your second hard disk by pressing the F8 or F12 key, like Gn2 describes in this thread, [Dual Boot on Two Drives]("http://ubuntuforums.org/showthread.php?t=275728")


Thanks, this is actually what I want. It may be true that old BIOS:es only look on the first disk, but my BIOS looks where I tell it to look. I actually find it easier to control my boot drive from BIOS; it has a hot-boot meny accesible by pressing F11 (as you mentioned). I prefer to manage my hard drives as separate units (black boxes) and don't want one drive to depend on what's happening on the other.

Looking at the referred thread I see that I physically need to disconnect the other drives, not just disable them in bios.

---

### Post by Herman on 2007-10-11
> Thanks, this is actually what I want. It may be true that old BIOS:es only look on the first disk, but my BIOS looks where I tell it to look. I actually find it easier to control my boot drive from BIOS; it has a hot-boot meny accesible by pressing F11 (as you mentioned). I prefer to manage my hard drives as separate units (black boxes) and don't want one drive to depend on what's happening on the other.:) Sure, no probs!
Thanks to Gn2 as well, hello Gn2! :)

>  Looking at the referred thread I see that I physically need to disconnect the other drives, not just disable them in bios. Well that depends on your beliefs really, and how certain you feel you need to be of installing GRUB's IPL definitely only  where you want it as opposed to the risks you might be taking reaching inside your computer case if you aren't used to doing that type of thing.

Occassionally the IPL for GRUB can be installed differently than directed due to all kinds of strange reasons, for example a mistake in the way IDE drives are plugged in jumpered, or when IDE and SCSI or SATA drives are mixed, that can sometimes confuse GRUB. I haven't seen too many problems like that for a while though.

I would think just disableing the other (first) disk in BIOS should do the job well enough.

Remember you can make a backup of your first hard disk's MBR if you want to make sure too, that should only take you a few minutes with the Ubuntu Live CD, here's the link: [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")

Regards, Herman :)

---

### Post by henteaser on 2007-10-11
I tried installing using the advanced options on the live cd, there's an option of where to install the boot loader. However, I have two IDE drives and one SATA, so maybe this confused grub because its install failed (fatal error). The drives were visible there even though they were disabled in BIOS.

It's not the risk of onening the case I fear, I just don't want the hassle. And I know that I can restore the MBR (or create a new one) with testdisk for instance...

---

### Post by Herman on 2007-10-11
Okay, so if your installation completed all but the last operation, installing GRUB bootloader, you can try booting Ubuntu with [Super Grub Disk ]("http://geocities.com/supergrubdisk/")to see if it will boot.
Super Grub Disk is avaliable in CD form (iso file), for floppy disk or for USB disk. It's free and it's an extremely small download.

Since you have more than one hard disk, once you boot Super Grub Disk, you would go through language selection to the 'English Menu'--> Advanced --> 'Gnu/Linux (Advanced)'-->'Boot Gnu/Linux'.
You can try 'Boot Automatically', and Super Grub Disk will scan your computer for Linux operating ssytems and offer you a list of them to choose from, (if you have more than one Linux installed).
If you choose 'Manual', you will be asked to select a grub file (/boot/grub/menu.lst), a first, second, third or fourth hard disk, then a partition number between one and ten until you find your Ubuntu operating system and boot it by its own Grub menu.
If that doesn't work, try the same thing again but try the 'Direct Boot' option.
There are other ways to boot Ubuntu with Super Grub Disk as well.

It you can boot, then you can also use Super Grub Disk to install Grub for you to whichever hard disk you like next time you reboot.
Otherwise you can do that manually with the command line if you prefer.

If you can't boot even after you have tried a few different ways with Super Grub Disk, maybe your operating system really isn't installed properly.
Maybe try the install again and hope for better luck, and/or check your CD for fingerprints, diirt or scratches and maybe clean the lens of your optical drive with a QTip and some denatured alchohol.

Regards, Herman, :)

I have to go sleep for a while but I'll be back later to check and see if there's anything more I can help you with.

---

### Post by henteaser on 2007-10-11
Got it fixed now. The problem was that I used incorrect grub syntax: I wrote (hdb) for second drive instead of (hd1). It's confusing because right next to the advanced button in last install step there is a list of changes to the partitions, and they are listed with linux syntax of hda, hdb and sda and so on...

I got it to work by doing this again and typing hd1 in this window. That put the grub on my primary ide slave drive. But then I received error 17 (cannot mount selected partition) when selecting the options from grub during startup (stage 2 I think). This was because within grub, the correct drive should be referenced as (hd0,0) instead of (hd1,0). I changed this manually.

---

### Post by Herman on 2007-10-12
There you go, you're doing fine with GRUB! :)

Regards, Herman :)

---

