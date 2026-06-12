---
title: "Dual Boot Win 7 + Ubuntu skips BIOS boot order (USB drive), goes straight to GRUB"
date: 2014-02-15
forum: Installation &amp; Upgrades
---

### Post by TRS-80 on 2014-02-15
Hello! :)

I have been Googling, to no avail. Found some info that was close, but no cigar. Even read the GRUB documentation, but I can't figure this out...

I have a dual boot set up with GRUB 2.0, I can boot into either Ubuntu 12.10, Memtest, or Win 7, the latter being the default option after a few seconds. All of that works fine and has for some time, since I built this new computer several months ago.

Problem today is, I can't boot from a USB stick. Computer just keeps going straight to the purple GRUB menu. I have changed all combination of options pertaining to boot order within BIOS, to no avail. It's just like they are all ignored.

AFAIK, GRUB should begin *after* the BIOS boot order is finished, amirite? I even tried, and was able to bring up F12 menu and tried selecting all manner of USB-HDD, USB-FDD, USB-CD, etc., again all to no avail.

The USB stick is a Kingston Data Traveler 16GB, formatted FAT32, bootable, with YUMI on it with a few ISOs of utilities, etc.  And yes I am sure it is bootable, I am able to boot into another Thinkpad I have without issue, select various ISOs in YUMI and everything works a treat on the ThinkPad. I just can't get it to work on my main PC. Thinkpad is running XP incidentally, no dual boot.

Scratching my head here. But the fact that it works on the laptop keeps pointing me in the direction of GRUB?

---

### Post by fantab on 2014-02-16
Check in your BIOS if there is an option to enable/disable 'USB Booting' or something like that. 
Also check if USB ports are enabled... Some BIOS have these features.

I think USB-HDD is the option you must try with.

Its not a GRUB issue. BIOS loads first and if it says boot from USB then the boot-loader on the USB will run. 
If USB is not present then HDD or whatever is set as next in the 'Boot Priority' will boot.
From what you describe your BIOS does not see USB either as first boot priority or it does not see the USB at all...

Can you try a different USB with bootable Ubuntu .iso? I mean without yumi.

---

### Post by oldfred on 2014-02-16
In addition to fantab's suggestions.

Some Gigabyte motherboards will not boot a flash drive over 4GB unless you update BIOS/UEFI.

With my old Gigabyte board, I also have many USB boot options. And for a while thought I could not boot flash drive that I also knew worked on my laptop. None of USB options worked. 
Then when changing boot order in hard drive choice, I saw flash drive. Even though in USB port it is seen as another hard drive not a USB device.

---

### Post by TRS-80 on 2014-02-16
> **fantab said:**
> Check in your BIOS if there is an option to enable/disable 'USB Booting' or something like that. 
Also check if USB ports are enabled... Some BIOS have these features.

I think USB-HDD is the option you must try with.

Its not a GRUB issue. BIOS loads first and if it says boot from USB then the boot-loader on the USB will run. 
If USB is not present then HDD or whatever is set as next in the 'Boot Priority' will boot.
From what you describe your BIOS does not see USB either as first boot priority or it does not see the USB at all...

Can you try a different USB with bootable Ubuntu .iso? I mean without yumi.

Yeah I have tried every option I could find in there I thought might even be remotely related to USB, HDDs, boot order, etc. In fact, right now I have first boot device set to USB-HDD, and second and third options disabled, and it still boots straight to GRUB. She's a cheeky box, she does what she wants, not what I tell her. :)

I agree, this is pre-GRUB, as you say.

I will try some other ISOs, maybe even a CD, later when I get home and then report back.

> **oldfred said:**
> In addition to fantab's suggestions.

Some Gigabyte motherboards will not boot a flash drive over 4GB unless you update BIOS/UEFI.

With my old Gigabyte board, I also have many USB boot options. And for a while thought I could not boot flash drive that I also knew worked on my laptop. None of USB options worked. 
Then when changing boot order in hard drive choice, I saw flash drive. Even though in USB port it is seen as another hard drive not a USB device.

You may be on to something here. Mobo is a Gigabyte GA-MA-UD-somethingsomething... I will do some more investigation along those lines (mobo/BIOS) when I get home later also.

---

### Post by TRS-80 on 2014-02-17
OK, turns out that Gigabyte motherboards not being able to boot from USB are a well known problem. Just Google it and you will get tons of results, it apparently has (was?) been going on for years.

I read (and attempted) all sorts of solutions including [delayed timing the insertion of the USB stick]("http://chromasoft.blogspot.com/2010/10/solving-dreaded-gigabyte-wont-boot-from.html") (including a comment in that blog that "+" next to HDD means "choose HDD" not "default" as I had assumed), making sure the partition on the USB stick was less than 4 GB (mine was/is 15 GB), certain brands of USB media (which were not what I have, I have a very recent Kingston Data Traveler, for the record). None of those things worked for me, although some apparently worked for other people.

The suggestion I finally found that *did* work for me was this one involving [HP USB Disk Storage Format Tool and Windows 98 Startup Files]("https://bitcointalk.org/index.php?topic=90858.0"). After making a blank USB, I formatted with Win 98 files per the instructions, and I was able to successfully reboot to a DOS prompt on my USB stick! Yay!

I would like to note that I did not reduce the size of that partition down to under 4GB, I was successful with the full 15GB USB drive. Also, I did not have to press F12 or any of that other stuff, in my case it just booted straight into the USB. You will know when you are getting close when the USB starts to show up in BIOS as an actual HDD. And you will actually boot to it as an HDD, you will set your USB drive to the first hard drive in the boot order listing of HDDs (I left "first boot device" as USB-HDD, and "second boot device" as HDD anyway, just in case, although I don't think it mattered).

But this was still a blank drive (except for the Win 98 boot files). In my case, I wanted to use YUMI instead of Netbootin, as was outlined in the above linked article. Also the warning I received upon first YUMI installation (about overwriting the USB drive MBR) worried me that it would overwrite the Win98 boot files and then not work. But that was not the case, upon reboot I was successful in booting into YUMI. Yay! And there was much rejoicing! :)

So now I am happily reloading all my various ISOs and tools back into my YUMI USB drive. I just wanted to report back the solution and thank you guys for pointing me in the right direction. Cheers!

Oh, and for the record (and search) my mobo is actually the Gigabyte GA-MA790GPT-UD3H. One of the first things I did was to try and flash the BIOS to a newer version (F3 maybe?) but of course that didn't seem to do anything either.

---

