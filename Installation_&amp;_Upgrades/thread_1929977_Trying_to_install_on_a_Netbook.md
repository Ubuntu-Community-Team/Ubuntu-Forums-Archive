---
title: "Trying to install on a Netbook"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by racsw on 2012-02-22
Hello,
It's been years since I've worked with Ubuntu.
I've got a Samsung Netbook computer, no CD, no hard disc drive, just a USB port, 1 GB of Ram, and a 100 Gb Flash Drive (I think that's what you call it)

I tried installing Ubuntu on an 8 Gb Stick, but although the installation went ok, the boot setup screen has no options to boot anywhere but the flash drive.  So it won't work off the stick.

The Netbook comes partitioned with 30 Gb for Windows (C:) and 70 Gb for anything else, but in this case it would be ideal to install Ubuntu there, at least I think so.

The reason I want to install Linux on the D: partition is so I can get the computer to speed up a little, it's ridiculously slow.  The RAM is not upgradable, and it runs Windows 7 Starter.
I don't want to lose my Win system however, it has some programs I need that aren't found in Linux.

After installing per instructions using PenDriveLinux, I see another installer,Wubi.exe.  Unfortunately, the choices it offers does not contain one that I can use.

Can you tell me if I'm wasting my time installing Unbuntu on this Netbook, but if not, how do I go about it?  Please remember that I can't boot off of anything else than the standard Flash Drive.

Thanks,
Robert

---

### Post by deonis on 2012-02-22
What is your model of Samsung netbook? Did you try installing 10.04? I have N145 netbook and 10.04 works ok on it...

---

### Post by racsw on 2012-02-23
The problem is not the version of Unbuntu.
The problem is that it has no CD-ROM, and the Boot Setup does not offer any alternative boot locations. (CD, USB Flash Drive, etc)

So there's no way to install it that I can see.

The Samsung Model is NP-N310.

---

### Post by deonis on 2012-02-23
My bad, If you don't have the boot option from a USB stick then you have only one reasonable option to solve your problem. You will need to remove the hdd from your PC and connected it to another PC, then do a full installation of Ubuntu and put it back to the netbook. Also check for a BIOS update for your netbook, maybe you will have the boot option after an update. In addition, you might get some boot options if you strike Esc button instead of F2. Sometimes Sumsung guys do funny things with their bioses. :)

---

### Post by efflandt on 2012-02-23
Are you sure that there is no option in CMOS setup to enable a hotkey during BIOS splash to select a different boot device?  Otherwise how could it even reinstall or install a different Windows version from USB DVD (if you had one)?

My Acer tablet is almost like a netbook (same weight), except with detachable keyboard and included Win7 Pro.  I had to enable the boot device hotkey in CMOS setup before it would appear during boot (once I figured the secret to get into CMOS setup). And even after that I have to hold a Windows button under the screen while pressing the on button with keyboard attached to see BIOS splash screen hotkeys.  Fortunately it came w/2 GB RAM and has internally USB connected slot for up to 32 GB SD, so I was able to install 64-bit 11.10 to SD slot from bootable install iso on USB.

So I figure a netbook with no optical drive (CD or DVD) must be new enough to have some way to boot an alternate device, if you can figure out the secret to unlock that.

I did upgrade the Dell netbook of a coworker to 2 GB RAM.  It was rather involved because it required splitting the case and removing keyboard (a YouTube video helped a lot).  But he only runs Win7.

---

### Post by racsw on 2012-02-23
Well, I've got good news :popcorn:

Someone mentioned the ESC key, so I thought I'd give that a try.
I did get into the CMOS screen, and it doesn't list any other bootable devices.

So anyhow, when I did it, another screen came up with C: Drive, or USB Ubuntu (Drive E:)

That worked.  Hot bananas!

Wow, things have changed a lot from when I used Ubuntu years ago.
It really has some very nice changes, like the instant mount of whatever partition it sees just by clicking on it.

So what I'm going to do is install Ubuntu on my D: drive instead of keeping it on the USB stick.
Can you guys tell me if the installation procedure will ask me what partition (system) will be the default for boot?
Otherwise, we used to have to modify a Grub bootloader script manually to do this.  Do you know where that is stored?

BTW, I can't answer the legitimate question someone asked which was "How do you reinstall the Win7 system if it goes down?"
Good question...  since there is no CD, or even a Win7 disk that you get with the Notebook (It's Notebook BTW, not Netbook, I was mistaken)   

Lastly, so much has changed, and I've destroyed a lot of memory cells over the years, so is there a book out for a recent Ubuntu system I can buy?

Thank you all for your help guys, I really appreciate it.
I take this on my motorcycle when I'm traveling around the country and out.  It doesn't have a HD, and its got a very durable screen and outer casing, so unless I submerge it, it just keeps on ticking and isn't susceptible to vibration.,
It ain't fast, but neither am I ;-)

Thanks,
Robert

---

