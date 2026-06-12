---
title: "Need Help installing on HP Pavilion P7-1234 computer"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by burialhound on 2012-09-06
I just bought an HP Pavilion P7-1234 and I have never installed a Linux OS before, and I cannot get the Ubuntu install to even start. At boot up I put the install CD in and it won't start, I try to change the boot order to CD/DVD (I don't even know if it changed the boot order or if I can even change it at all)still won't start. I tried install with WUBI with CD/DVD boot help, it gave me the option between Windows and Ubuntu but when I pick Ubuntu it gives an error message about corrupt or unreadable disk (even though I verified the disk!)I have tried a bunch of different Ubuntu disks I own and I'm kinda getting up the wall here, I am starting to think I might not be able to install on this computer. Any help would be very welcome and I would prefer to do a full install over using WUBI. I am willing to get rid of Windows if it will help the situation.               -Thanks!

---

### Post by tolsen27 on 2012-09-15
I just bought the same tower and seem to be experiencing the same difficulties. Have you found any solutions yet?
Thanks!
-Tanner

---

### Post by burialhound on 2012-09-21
> **tolsen27 said:**
> I just bought the same tower and seem to be experiencing the same difficulties. Have you found any solutions yet?
Thanks!
-Tanner

No, I ended up returning the computer. I think it might have UEFI that wont let you install any OS besides Windows (SecureBoot).Until a workaround is found I am going to be buying a computer from ZaReason, they make Linux ready computers.

---

### Post by Cakemix1976 on 2012-09-23
OMG!  I am glad to have seen this post!  I too have a fairly new HP Desktop with Win 7 and have been trying for 4 days now to get ANY version of Ubuntu installed on it!  10.10, 11.04, 12.04 with nothing more than frustration and anger!

I went so far as to download the gparted.iso and delete all the partitions and create a new one, but when I go through the install process it gets to the third screen and it doesn't see ANY partitions at all!  Clicking Install Now only results in "No Root file system is defined.  Please fix this from the partitioning menu."  

I have an older HP laptop that had no problems letting Ubuntu take over the entire hard drive.  I don't need Windows on my desktop machine, but apparently my machine thinks otherwise.  If I knew how to upload pictures I could show everyone that I have deleted the preinstalled partitions and created a new one, and then pictures showing the first 3 screens of the install where it stops and I can go no further.

---

### Post by oldfred on 2012-09-24
Many have installed dual boot with new computer with UEFI. Secure boot will be implemented with Windows 8.

But you need to know if system is BIOS or the new UEFI/BIOS. Some systems with UEFI still install Windows in BIOS mode, others in UEFI mode. If dual booting Ubuntu must be installed in the same mode.

If UEFI Windows, then only the 64bit version of Ubuntu works with UEFI installs.

---

### Post by lalawawa on 2012-10-14
I'm having the same difficulties.  I don't understand the post before this one, I have no idea what UEFI means.  I'm taking the computer back to the store tomorrow and exchanging it.

---

### Post by oldfred on 2012-10-14
@lalawawa
Almost new computers are now UEFI. They may have a fallback to BIOS mode. Some may still have Windows in BIOS mode or may have it in UEFI mode. All new computers with Windows 8 will be UEFI with secure boot, an added complication.

[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)
[http://en.wikipedia.org/wiki/Uefi](http://en.wikipedia.org/wiki/Uefi)
Boot loader comparison
[https://wiki.ubuntu.com/EFIBootLoaders](https://wiki.ubuntu.com/EFIBootLoaders)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by lalawawa on 2012-10-15
Hi Oldfred.  I couldn't figure out how to boot off a CD-ROM or thumbdrive.  If I hit ESC during boot, I would get a menu of a bunch of SAFE modes, but I think I was still within Windoze-land.  I couldn't figure out how to get to the BIOS or UEFI or whatever and tell it to boot off the alternative medium.  The manual that came with the computer was pathetic, nothing whatsoever about the BIOS of UEFI.  Basically little more than how to plug the computer in.

I took the computer back to the store yesterday.  The only reason I bought it was the hard drive had failed on my 5 year old computer.  Best Buy said they'd put the refund on my credit card, which they weren't required to do, all they said when I bought the computer was i could exchange it.

Best Buy is hardly selling  any towers or desktops now, they're really pushing these 'all-in-one' units where everything is built into the monitor (read: you have to buy a new monitor every time you get a new computer).

I bought a new internal disk drive and took it home.  I live in NYC and have no car, which means I have to carry computers on the subway for an hour either direction to get to Best Buy.  I would've liked the Geek Squad guys to put the disk drive in, but it wasn't worth the trip.  I couldn't figure out how to get the old disk drive out of the cage, and there was no remaining slot big enough to put the new one in, so I duct taped the drive where there was room for it.  Booted and it worked.

---

### Post by oldfred on 2012-10-15
@lalawawa
New use for Duct tape? :)

Not sure the best way to install a drive, but one system I had, did have drives suspended, some have rubber mounts to cut noise. Drives usually come out the front. You have to figure out how to remove front panel/cover which may have clips or just be snapped in.

In your case I would have just bought drive on the Internet from whichever vendor had best price like Microcenter, Newegg or Amazon. Everyone has horror stories or success stories for every vendor so I am not sure it really matters.

---

### Post by lalawawa on 2012-10-17
Hi Oldfred,

From what you said in this thread and in another thread about another new model of computer I was thinking of getting, I concluded that what is happening is that PC makers are reorganizing booting and the BIOS such that many new computers bought in stores will not readily boot off CD-ROM, DVD, or thumbdrive.  The UEFI doc you gave links to wouldn't work in my case.  I was trying to boot off a 32 bit CD/ROM, or 32 bit USB drive.  I'm not sure where I would have gone to create a 64 bit CD/ROM.  I did not want to have to wait several days for a set of physical Ubuntu DVD's to show up in the mail.

You were also saying things about needing to wait until 12.10 for this problem to be really solved.  My computer was down, I wanted a computer NOW, I did not want to wait for another release of Ubuntu to show up.

My impression is that the current state of Ubuntu and new PC's is that I can't go to a computer store, buy a computer, come home and install Ubuntu (or any other kind of Linux) on it.  I don't know how one would upgrade to the next rev of Windoze.

This is a serious problem that I hope Ubuntu will work out before long.

---

### Post by oldfred on 2012-10-17
UEFI will not work with 32bit Ubuntu. Since UEFI is only on new computers, there is no reason to run 32bit anymore with a new computer.

You can download the 64 bit version from the Ubuntu site. Most will stay with 12.04 and even 12.04 will get an upgrade to grub2 2.0 that has more changes. Ubuntu has said it will now stay with grub for secure booting of new systems. 

The 12.10 version will be out on Thursday Oct 18.

---

