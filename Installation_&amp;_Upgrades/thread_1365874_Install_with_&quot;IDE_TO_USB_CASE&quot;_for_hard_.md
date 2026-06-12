---
title: "Install with &quot;IDE TO USB CASE&quot; for hard drive"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by bigsmitty64 on 2009-12-27
I had an extra 30 gig  IDE hard drive lying around and decided to install my Ubuntu on it. However, I only have sata hookups left on my mobo. So I bought a case that holds the ide hard drive, and connects to the p.c. via usb.
I installed Ubuntu 9.10 on that drive,no problem, I did NOT use wubi. 
However, I cannot get the p.c. to boot from it for anything. I changed the boot order in the bios to boot to  that (ubuntu) drive first. This is the same setup I had before,but the drive was installed internally. My bios see's it as a usb hard disk, and thats what I chose to boot to.  I tried changing where I plug the drive in (I have about 6 different usb ports) to no avail. It just boots straight to Windows every time! Any help is greatly appreciated. Thanks in advance,
Smitty

---

### Post by bigsmitty64 on 2009-12-27
I Just found [THIS]("http://unetbootin.sourceforge.net/") Would this work in my case?

---

### Post by Herman on 2009-12-27
:) Hello bigsmitty64,
Have you ever booted this particular computer with any other USB device before?

Do you know whether or not your motherboard (and BIOS) supports USB booting?

Some motherboards can do it and others can't. They aren't wired for it.

I am trying to think of a way to test, (besides the obvious method of just trying it), if a motherboard can boot a USB drive or not. Funny thing but after all this time I still don't remember seeing a command for that. 

 Unless ...

---

### Post by Bartender on 2009-12-27
herman, I'd like your thoughts on this.  I've been able to boot from an external, but it's a Vantec dock with its own power supply.  I have it spinning before booting the PC.

I wonder if some USB powered externals aren't up to speed before the PC tries to boot from them, finds nothing, and moves on?

---

### Post by Herman on 2009-12-27
I have a few different kinds of external USB drive now.

One of them is for regular desktop computer sized hard drives and that one has its own separate power connector to the wall socket, and I have no problems with that one.

The smaller USB external drives for laptop sized hard drives don't always get enough power fro the USB ports on all computers to spin them up though, especially if it's a large capacity (in GB) hard drive and/or a small laptop supplying the power.

Flash memory sticks are no problem as far as power goes, (from any computer), and my new 60 GB OCZ SSD drive doesn't seem to require very much power to run either.

The amount of amps available at the USB port is one issue, but besides that, some computers can't boot a USB just because of their design even if they have enough power at the USB port or the USB has its own external power supply.

---

### Post by Herman on 2009-12-27
Pendrive Linux has a way to test it here,[Testing your system for USB boot compatibility]("http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/")

---

### Post by Herman on 2009-12-27
If a computer can't boot an operating system in a USB external hard drive it's still possible to run Linux in the USB.

It's possible to do that by copying the Linux kernel and initrd.img and other files from /boot into another disk that's inside the computer.

You'd need to use a non NTFS partition inside the computer, FAT32 would do if that's all you have, the root of drive C would be okay if your Windows is in FAT32.
Or you could make a small separate FAT32 or ext series partition inside the computer, 100 MB or so would be enough, and make that into your /boot partition for Linux. 

You'd need to install GRUB to MBR, but you could have the rest of your Ubuntu operating system and files in the USB.

---

### Post by bigsmitty64 on 2009-12-28
> **Herman said:**
> :) Hello bigsmitty64,
Have you ever booted this particular computer with any other USB device before?

Do you know whether or not your motherboard (and BIOS) supports USB booting?



Herman, the answer to both of those is...no, I have never tried it before.

> **Herman said:**
> 
"It's possible to do that by copying the Linux kernel and initrd.img and other files from /boot into another disk that's inside the computer."


Problem is I can't get into my Ubuntu o.s.  I can't see it in Windows.

Bartender, It is indeed a self powered case, holding a regular desktop sized hard drive.

Just so everyone knows,
I went into windows computer management, where I can see the drive, and removed the ubuntu installation, so now I'll start from scratch with any advice I get here.

---

### Post by Herman on 2009-12-28
Would you have any problem with moving 30 GB of data from one of your hard drives and storing it in your 30 GB USB external hard drive to make room for Ubuntu in an internal hard disk? :)

---

### Post by Herman on 2009-12-28
If you still want Ubuntu in your external USB hard disk you'll have to install it again.
But we still haven't been able to verify at all if your computer's motherboard and BIOS is able to boot a USB. Likely it will install okay, but as you've already experienced, it just won't boot. Probably you'll be able to boot it in some other computer though.

One way to see if your computer can boot a USB would be to try with a Super Grub Disk.

---

### Post by Bartender on 2009-12-28
> **Herman said:**
> The smaller USB external drives for laptop sized hard drives don't always get enough power fro the USB ports on all computers to spin them up though, especially if it's a large capacity (in GB) hard drive and/or a small laptop supplying the power.

Now that you mention it, I remember a friend bought a USB powered external for her Toshiba laptop running XP.  Every time she plugged it in, she got an error message from Windows saying there wasn't enough power.  She returned that external for one with a wall wart, no problems.

So maybe there are at least a couple of potential problems when trying to use a USB powered external as a boot device - certainly the one you describe, where there simply isn't enough power to even spin the drive, and/or it might spin up too slowly and BIOS doesn't wait around to see if anyone's home.

---

### Post by Herman on 2009-12-29
I'm afraid I lost our customer ... we haven't heard from bigsmitty64 in a while ...

I was still thinking about the best way to test whether a computer can boot an operating system in a USB though, and I think probably the best way would be to try booting from a GRUB CD in Command Line Mode.

A person who already has Ubuntu in a computer can  easily make themselves a GRUB2 CD with the grub-mkimage command, if they have GRUB2.

What if it's somebody who doesn't have a bootable Ubuntu installation yet though?
The answer is, Super Grub Disk is now out with a GRUB2 version.
Anybody should be able to download a Super Grub Disk and make it into a CD. [Super Grub Disk Downloads]("http://developer.berlios.de/project/showfiles.php?group_id=10921").
The most recent version at the time I tried was [sgd_cdrom_1.21.iso.gz]("http://prdownload.berlios.de/supergrub/sgd_cdrom_1.21.iso.gz") and although it's based on GNU GRUB 1.96 and not 1.97.4 it still works okay.
Windows users would probably be able to download the file but they'd need to boot a Ubuntu CD to extract the tar.gz on the hard drive, then reboot into Windows again to burn it to disc. If Super Grub Disc can't boot a USB in a computer then probably the computer isn't capable.

I made a new web page today about booting with a GRUB2 Rescue CD from the command line, [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html")

In the process of looking for a blank CD to burn Super Grub Disk to I found something else of interest. 
I rediscovered an old version of PLOP Boot Manager on a CD. 
PLOP Boot Manager is supposed to be able to get a computer that isn't normally able to boot a USB drive to be able to do so with special drivers. I might need to download a newer version and review PLOP Boot Manager again, [PLOP Boot Manager]("http://www.plop.at/en/bootmanager.html"). 

Regards, Herman :)

---

### Post by Bartender on 2009-12-29
herman, thanks for all the great work you've done, and for creating a website so that it's readily accessible instead of lost in old threads.

Lots of the stuff on your website is beyond my LIQ (Linux Intelligence Quotient) but I'm sure it's helped lots of other folks! :)

Have you any thoughts as far as a good way to test whether an external device will work with a PC that **is** fully capable of booting from USB?  If a person's got an external hard drive that's powered from the USB port, it seems that maybe we could suggest some small download be installed to the external instead of going thru the whole process of installing Linux only to find out that the PC's BIOS won't pick it up for whatever reason...

---

### Post by joshedmonds on 2009-12-30
Hi again Herman... if someone is having an issue with the time it takes to spool up the drive (rather than the power draw as such), perhaps introducing a delay simply by using the BIOS manual boot disk selection could help (e.g. 'Press F12 to select boot device' immediately after POST).

This step may be necessary for someone like the OP anyway, for example my (now) mobile 9.10 install is deliberately not included in the PC grub menu because it won't always be there, and isn't seen by the PC as a USB drive in the same way a flash drive is as regards BIOS boot order. Because it is seen as a hard drive it needs to be selected manually.

EDIT: @bigsmitty64 As for unetbootin, around 8.10 I was having a lot of trouble booting from certain devices with some methods of creating liveUSBs, however unetbootin worked every time. Unetbootin does not install the OS though, it just creates the equivalent of a liveCD on a USB. You can make the install persistent but it is a different process and a different result. If you are just trialling an OS before an install on the internal drive, or for a liveUSB with those limitations, I highly recommend unetbootin.

EDIT2: This doesn't need a new post, but on my Acer Aspire One, the boot process is so fast that the external USB-powered drive doesn't have time to spool up. Even if I press F12, it hasn't yet registered with the system. To get around this I can let the netbook go to grub (legacy), then reboot, and the continual power allows the drive to register the second time around.

---

### Post by Bartender on 2009-12-30
> **joshedmonds said:**
> if someone is having an issue with the time it takes to spool up the drive (rather than the power draw as such), perhaps introducing a delay simply by using the BIOS manual boot disk selection could help (e.g. 'Press F12 to select boot device' immediately after POST).

 Hey, that's a good idea, at least for testing.  Get to that "quickboot" BIOS option screen and wait five or ten seconds.  Put an ear to the external at the same time and see if you can tell if/when it's up to speed.

---

### Post by Herman on 2009-12-30
> Hi again Herman... if someone is having an issue with the time it takes to spool up the drive (rather than the power draw as such), perhaps introducing a delay simply by using the BIOS manual boot disk selection could help (e.g. 'Press F12 to select boot device' immediately after POST). Yes, that might be the answer for some USBs and computers.

---

### Post by Herman on 2009-12-30
:) Hey! I found out something interesting!

I was still working on this question, (how to tell if a computer's BIOS/motherboard is capable of booting a USB device or not), when something surprising happened!

My main, favourite computer that I assembled myself a couple of years ago has never been able to boot a USB. 
One of the reasons I made it was so I'd have a test computer with several hard disks, IDE and SATA mixed, for testing the Ubuntu installer and doing experiments with GRUB. 
Some of my older computers can boot from USB, so I tried and tried after I first assembled it, but to my disappointment, it has never been able to boot a USB drive. 
I use this computer all the time and as well as being my main computer, I do a lot of boot loader experiments with it.

That made it an ideal machine for trying to see if there's an easy way to tell if a computer can or cannot boot a USB.
I have a new computer right beside it I just assembled a few days ago that can boot a USB, and I was comparing the two to find out the differences. 

They both have ASUS motherboards.
I was comparing the outputs from the dmidecode command, but I'm not sure what to look for there.
One difference between the two computers is the newer one displays a BIOS boot menu if I press F8 during boot-up. 
This computer that can not boot a USB is one that does not display any BIOS boot menu by pressing a key like F8 or F12 during boot-up, or I haven't found the right key yet.
Other computers I have, older ones even, that can boot a USB also have a BIOS boot menu.
For a while I was thinking maybe that could be a way to tell.

When I try to boot a USB with Legacy GRUB in the computer the can not boot a USB it does not include the USB drive in the list of possible devices. 
Trying to chainload the USB anyway gives GRUB Error 21.

A few days ago I wrote a script for adding more lines in my GRUB Menu for booting up extra hard drives, meierfra helped me finish it. See [COLOR=#980101]**[ubuntu]**[/COLOR] [How Do I Chainload With GRUB 2?]("http://ubuntuforums.org/showthread.php?t=1363723") . 
I was actually planning on changing into CLI Mode to do some experiments with the USB drive plugged in but while I was at the GRUB Menu I looked at those new extra boot entries and I selected the bottom one, (my USB drive), not expecting anything to happen, (except an error message probably).

It booted! Suddenly my computer started being able to boot and run Ubuntu in a USB drive!

What happened? 
Further experiments seem to indicate that GRUB2 has improvements in it that give it more ability to boot a USB than Legacy GRUB.

I can use GRUB2 in the same computer, (from a CD or from a hard drive installed GRUB2), and it will list the USB drive with the ls command or using tab completion from other commands in CLI mode. 
Legacy GRUB does not list any USB drives in the list of possible devices. 

I can boot an operating system directly in a USB with GRUB2 or I can chainload the USB and bring up the USB's boot loader.

If the USB has GRUB2 as the boot loader, it will then boot an operating system in the USB or any other operating system plugged into the computer.
If the USB has Legacy GRUB, I get GRUB Error 21.
(it can't 'see' the USB that it's running in! (LOL)).

Is anyone else interested in confirming whether or not GRUB2 can boot USB drives in a computer which is not normally able to?

---

### Post by theozzlives on 2009-12-30
I'm wondering if you're attaching it to a port or a hub. If a hub, is it passive or active? If passive (you don't plug it in), you may need to go with an active hub or plug the HDD into one of the ports on the motherboard.

---

### Post by Herman on 2009-12-30
:) 
Most of the time I'm just plugging my USB drives right into a port on the front of the computer case. 
Sometimes I plug them into back of the computer where they plug right into the motherboard, I'm not sure if that makes any difference. 
In a laptop the socket would be attached directly to the motherboard.

I also plug the my USB drives in via hubs along with other USB devices quite often when there are not enough USB ports available on a computer.
The hubs I use all plug into the USB port only, I don't own any hubs that have their own power cord for plugging in to a wall power socket. 
That's what you're calling an 'active hub' I guess. If that's so then mine are all 'passive' ones. I haven't actually gone looking for them, but I've never noticed any other kind of USB hub for sale. It's not very often I get to visit a computer store though, I live in a remote area. I didn't know those were available but now that you mention it that's an excellent suggestion, maybe it would help those who have the problem of lack of amps for spinning up an external hard disk drive. :)

---

### Post by Herman on 2009-12-30
I have noticed that not all USB cables will drive a USB hard disk, especially longer USB cables.
Usually the ones provided with the USB drive when it's new are usually okay, but if that one gets lost a different cable doesn't always work.
I always imagined the problem would probably be voltage drop over the length of the cord, but it could be interference too.
An IDE cable has a length limit of 18", any longer than that and they start to have problems, and IDE drives have separate power cables of course.
If an IDE cable over 18" long is unreliable, then how reliable can a USB cord be if it's long or if it's a cheap one that's not designed for that kind of job.
The desktop computer I just put together has wires leading from the front panel to where they plug into the motherboard, that could add up to a little bit of power loss or a loss of signal integrity just the same as an extra long USB cable.
Maybe it is slightly better to plug USB drives in at the back of a desktop computer,  so they will be plugged directly into the motherboard.

---

### Post by Herman on 2009-12-31
> I had an extra 30 gig IDE hard drive lying around and decided to install my Ubuntu on it. However, I only have sata hookups left on my mobo. So I bought a case that holds the ide hard drive, and connects to the p.c. via usb.
I installed Ubuntu 9.10 on that drive,no problem, I did NOT use wubi. 
However, I cannot get the p.c. to boot from it for anything. I changed the boot order in the bios to boot to that (ubuntu) drive first. This is the same setup I had before,but the drive was installed internally. My bios see's it as a usb hard disk, and thats what I chose to boot to. I tried changing where I plug the drive in (I have about 6 different usb ports) to no avail. It just boots straight to Windows every time! Any help is greatly appreciated. Thanks in advance,
Smitty:) I believe I have found the answer to bigsmitty64's original question.

It's PLOP Linux Boot Manager, [PLOP Boot Manager Home Page]("http://www.plop.at/en/home.html") 

PLOP Boot Manager is the easiest boot manager I have ever used, it scans the PC automatically and it found all my drives.
It offered me a list of partitions in each drive to boot, (we need to have a boot loader installed in a boot sector though or nothing will happen, PLOP is a boot manager, but not a boot loader).
At the end of the list of hard drive partitions was a listing for my floppy drive, and amazingly an entry to boot the CDROM drive!
And at the end of the list there is the USB option.

My dog was able to scroll down the list and hit the USB option, yes, my dog did it! 
He was a bit apprehensive at first when I was trying to coax him into the computer chair, I think he was a little suspicious, wondering what I was up to *this* time. 
But eventually I got him up there and he pressed the keys to scroll down and and boot the USB!
(Well, I was holding his paw, but it was his paw that was pressing the keys!)

PLOP Boot Manager can really boot a USB even when the computer can't normally boot one.
It's only a small download and even a Windows user should be able to figure it out.
All you do is burn the plptnoemul.iso to a CD and boot it. PLOP Boot Manager will do the rest.

Actually, the burning to CD part would probably stump my dog, I haven't trained him how to burn CDs yet.

Anyway, I'm sure by now you get my message, PLOP Boot Manager is the EASY way to boot a USB, and a lot of other things too, for that matter.
I don't know why PLOP Boot Manager is not more well known.

---

### Post by Bartender on 2009-12-31
herman, some very interesting posts here.  I sure appreciate your talent for digging into an issue and coming up with unique solutions.

The oldest functional system I have is an ASUS board running a Pentium III.  I'll go check to see if it has USB boot ability.  If not, maybe I can run a test or two for you as long as it doesn't involve a lot of CLI work.

The Plop boot manager sounds interesting.  I tried GAG last week and made a mess of things.  If Plop is easier maybe I won't screw it up.

---

### Post by dandnsmith on 2009-12-31
Some of those ASUS boards appear to have the ability to boot from USB devices, but just don't do it in reality (except for some odd exceptions).
I speak from having tried it with A7N8X-X and A7V8X boards (mostly unsuccessful)

---

