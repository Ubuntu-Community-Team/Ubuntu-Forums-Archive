---
title: "[SOLVED]Can't boot to a live USB on either computer. Trying to save data from a dying"
date: 2016-02-04
forum: Installation &amp; Upgrades
---

### Post by launchpadnet.justj on 2016-02-04
Toshiba Satellite laptop.

What I'm trying to do: boot the Toshiba laptop into Ubuntu or Xubuntu live usb stick... so that I can move some folders & files to an external usb drive. ()A brother-in-law asked me to rescue those files for him if possible.)

Problem: Neither that laptop and my own Acer Aspire laptop seem to recognize that the usb stick is even there and boots as normal (on mine), or unsuccessfully tries to boot into Vista (on my brother-in-law's Toshiba).

I changed the boot order on both to move the usb boot option above that of the hard drive.

I also tried to use an old GParted CD rom I had made some years ago on the Toshiba and it boots to that... but I have no clue on what to do from there and I'm not sure if it could copy the files from the hard drive to an external drive even if I knew what I was doing.

To my newbie mind that indicates that at least the RAM & motherboard & CD etc. work, which gives me hope that if I could get the laptop to boot into Ubuntu or some other live version of Linux. My preference is to use a usb stick. I've been trying with one that I formatted to FAT 32 & it is 4.88 GB with 4.87 GB free.

On my first try I tried Knoppix, after seeing [this Youtube tutorial]("https://www.youtube.com/watch?v=HQI1VsXkeTE") that did exactly what I hoped to do in re: copying those files.

I used [the Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") from Pendrivelinux.com to make a "live CD" (for usb).

I tried all three usb slots on the Toshiba & it ignored them  completely every time. I then tried it on all three usb slots on my  Acer, but unfortunately had the same result.

But Knoppix was about 4.17 GB in size & said something about it being compressed & might use 2 GB for persistence or whatever.

So, I reformatted it and tried to make a live CD for usb using Xubuntu. Unfortunately, I had the same result once again on both computers.

So I'm wondering if I'm doing something obviously wrong such that someone could set me straight. A couple of possibilities I'm wondering about:

1. I'm not sure if the Toshiba is a 64 bit system or 32 bit, so I downloaded the 32 bit version figuring it would be able to run on either a 32 bit or a 64 bit machine... is that incorrect?

2. Should I be downloading some special "live CD" version rather than a generic version of the OS and then using [the Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")  to convert it to a live CD format?

Other questions:

What would be a good "flavor" of Linux to use? I am not familiar with command line stuff nor Linux very much, though I did set up an Oracle Virtual Box & installed Ubuntu and played around with it a tiny bit a couple of years ago, but have it reinstalled since I updated to Windows 10. A graphical interface for copying or dragging & dropping files would be best for me if possible.

Should I just give up & burn a CD or DVD rather than keep trying to figure out how to do a usb boot??

If I do get the Toshiba to boot to Ubuntu or Xubuntu, how would I copy/move the folders? Is there an icon to open something like Windows' File Explorer, or would it be a command line thing?

Thanks in advance for any help, advice etc.

---

### Post by sudodus on 2016-02-04
Welcome to the Ubuntu Forums :-)

The Toshiba with Vista should work with a 32-bit operating system (start from a Lubuntu or Xubuntu desktop i386 iso file). The computer with Windows 10 might run in UEFI mode. That computer should work with a 64-bit operating system (start from any Ubuntu flavour desktop amd64 iso file). It makes it easier to help if you give us more details about the computers:

- Brand name and model number (there are many different Toshiba Satellites)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

-o-

I suggest that you start trying with the ***versions*** 14.04.1 LTS, 14.04.2, 14.04.3 or 15.10 (a lower version number might work better with an older computer and a higher version number might work better with a newer computer because of the drivers for graphics and wifi).

Have you checked that the download was good? You can use ***md5sum*** in linux or md5summer in Windows to check that it matches the listed value from this link:

[help.ubuntu.com/community/UbuntuHashes](help.ubuntu.com/community/UbuntuHashes)

If there are boot problems you can try [mkusb](https://help.ubuntu.com/community/mkusb) in linux and [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) in Windows.

See also the following link (and links from it) for more details:

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by oldfred on 2016-02-04
I am currently using my Toshiba laptop from the end of 2006. I purchased it just before Vista as XP, but it said it was Vista ready. Know that I knew it was barely Vista capable. It has 1.5GB of RAM and whatever Intel video was, but is Core2 Duo.

It has 64bit 12.04LTS running Ubuntu, but not Unity. I use something called fallback/flashback/gnome-panel which is much lighter weight than Unity and runs reasonably well. 
Most of us would suggest Lubuntu or Xubuntu if an old system. And I have not had any issues booting from USB ports.

Live installer in live mode has Nautilus or a file browser similar to Windows for file management.
But if Windows is corrupted, it may not open it or may only open in read-only mode. You would need Windows repair console to run Windows repairs, if not able to mount it with Ubuntu.

---

### Post by launchpadnet.justj on 2016-02-04
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Thank you!

>  The Toshiba with Vista should work with a 32-bit operating system (start from a Lubuntu or Xubuntu desktop i386 iso file). 

I had downloaded & tried to run the torrent version of Xubuntu:

 [xubuntu-14.04.3-desktop-i386.iso]("http://cdimage.ubuntu.com/xubuntu/releases/14.04.3/release/xubuntu-14.04.3-desktop-i386.iso")          05-Aug-2015 05:37  936M  Desktop image for 32-bit PC (i386) computers (standard download)

I could not get either computer to boot to it, however.

> The computer with Windows 10 might run in UEFI mode. That computer should work with a 64-bit operating system (start from any Ubuntu flavour desktop amd64 iso file). 

The main reason I was trying it with the Win 10 laptop was to see if the usb boot drive would work, since it wouldn't work with the Toshiba Vista laptop. If I understand it correctly, if the usb drive was set up correctly the 64 bit Win 10 machine would work as well, even with the i386 32 bit Xubuntu operating system?


> It makes it easier to help if you give us more details about the computers:

- Toshiba Satellite Model PSLB0U-067033
- Intel Pentium Dual CPU T2390 @ 1.86 GHz
- RAM 3072 MB
- System Bios version 1.4
- Windows Vista sticker on it
No info available on the graphics chip/card or wifi chip/card for graphics or wifi

- Acer Aspire M5-581T
- Intel Core i5-3317U 1.7 GHz
- Bios V2.11 (this may have been taken down when I switched from EUFI to Legacy Bios to try and get it to boot to the usb drive - it seemed to hang up, however, so I changed it back & I never tried it in the Legacy bios mode).
- Windows 10
- not sure about the chips/card 

> -o-

I suggest that you start trying with the ***versions*** 14.04.1 LTS, 14.04.2, **[COLOR=#ff0000]14.04.3[/COLOR]** or 15.10 (a lower version number might work better with an older computer and a higher version number might work better with a newer computer because of the drivers for graphics and wifi).

Have you checked that the download was good? You can use ***md5sum*** in linux or md5summer in Windows to check that it matches the listed value from this link:

[help.ubuntu.com/community/UbuntuHashes]("http://help.ubuntu.com/community/UbuntuHashes")

I wasn't quite sure how to verify with md5summer, but I did use it to create an md5sum & I checked it visually against the one posted on the website and it seemed to match up.

> If there are boot problems you can try [mkusb]("https://help.ubuntu.com/community/mkusb") in linux and [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows.

I tried unetbootin, but it apparently didn't recognize my pendrive as the only option for the target drive was "D:", but the pendrive was "J:", so I used the Universal USB installer. I just now tried the YUMI, but it didn't work either on my Win 10 laptop - with Xubuntu 32 bit.

I'll try Win32 Disk Imager next if you think that might work.

> See also the following link (and links from it) for more details:

[Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

OK, I scanned it, but will read it more carefully now before trying again.

Thank you for your help!

---

### Post by oldfred on 2016-02-04
The Windows 10 machine needs 64 bit to be able to boot in UEFI mode. And Windows will be in UEFI boot mode, so you would want Ubuntu in UEFI boot mode.
Acer requires some extra settings beside the normal UEFI secure boot off, UEFI fast boot off, and Windows fast start up off. Acer after install requires a UEFI Admin password and setting "trust" on grub/ubuntu efi boot files. And some models require newest UEFI from Acer.

Your Toshiba should boot from flash drive, since mine is even older and works from flash drive.
Do you have newest BIOS from Toshiba installed? From f12 or BIOS I see a USB/hard drive device for booting. It must be correctly configured and plugged in when starting to boot.

---

### Post by launchpadnet.justj on 2016-02-04
> **oldfred said:**
> I am currently using my Toshiba laptop from the end of 2006. I purchased it just before Vista as XP, but it said it was Vista ready. Know that I knew it was barely Vista capable. It has 1.5GB of RAM and whatever Intel video was, but is Core2 Duo.

It has 64bit 12.04LTS running Ubuntu, but not Unity. I use something called fallback/flashback/gnome-panel which is much lighter weight than Unity and runs reasonably well. 
Most of us would suggest Lubuntu or Xubuntu if an old system. And I have not had any issues booting from USB ports.

Thanks. Here I was thinking that "an old system" was Windows 95 or older. Guess that shows my age, though. ;)

>  Live installer in live mode has Nautilus or a file browser similar to Windows for file management.

Cool. That's in Xubuntu too?

Btw, I'm not familiar with Unity. What exactly is that?

>  But if Windows is corrupted, it may not open it or may only open in read-only mode. You would need Windows repair console to run Windows repairs, if not able to mount it with Ubuntu.

I'm a bit confused. I thought Windows would not be needed if one is booting from a usb drive. I thought it booted to X/ubuntu before Windows ever woke up, so to speak. I was thinking that maybe my brother-in-law's laptop wouldn't boot up was because Windows was corrupted, or that part of the HD was corrupted, or whatever.

My hope was that maybe I could boot it to Xubuntu, copy the files from the hard drive that can still be salvaged and then maybe format or replace the hard drive & try again. But if the hardware is slow or underpowered, maybe that isn't a reasonable option either?

Thank you for the reply.

---

### Post by yancek on 2016-02-04
>  	 I'm a bit confused. I thought Windows would not be needed if one is booting from a usb drive. 

Correct.  What was meant is that if your vista system is corrupted or if it is hibernated, Ubuntu or Linux will not mount the partition(s) with windows on it.  You would need to run chkdsk from windows.  If you have a windows vista installation CD, you should have a repair option to do that.

Not sure why you can't get the usb to boot as you should be able to with a computer that had vista on it.  Unetbootin and pendrivelinux usually work pretty well.

---

### Post by sudodus on 2016-02-05
I suggest that you try **xubuntu-14.04.3-desktop-amd64.iso** in the computer with Windows 10 and UEFI, and that you keeping trying with the 32-bit version (i386) in the Tosshiba. You can *probably* also run the 64-bit version in that computer with a Pentium Dual CPU T2390.

[Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) is a *very* reliable tool.

For the Toshiba: Look at the tips in the following paragraph (in the link a gave you in a previous post)

[Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

For the computer with Windows 10 and UEFI I recommend that you follow carefully *oldfred's* advice.

---

### Post by oldfred on 2016-02-05
Unity is the newer gui/desktop environment that Ubuntu uses as a default. 
But Xubuntu, Lubuntu, fallback/flashback, gnome-panel, gnome and others are different gui. Some are icons, some are menus and they look different. But the underlying operating system is Linux. And with Ubuntu flavors it is all the same version of Linux.

Desktop environment is the gui plus supporting base desktop applications like a file browser.
But then a distribution like Ubuntu, Kubuntu, Lubuntu etc is one desktop environment plus many other applications like Internet browser, word processor, spreadsheet etc.

[http://unity.ubuntu.com/about/](http://unity.ubuntu.com/about/)
[http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/](http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/)

And besides the gui/desktop, each comes with different sets of desktop applications and different general applications. Or a lighter weight gui uses lighter weight applications by default.
 Comparison of desktop environments - differences in software
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

---

### Post by launchpadnet.justj on 2016-02-05
Thanks for all of the explanations, recommendations & links everyone. I'm slowly but surely learning.
 
One thing I learned is that one generic Linux version on a usb stick won't be a one size fits all solution. I didn't realize I'd need a 64 bit version to run on my laptop, for instance.

I also found a cheap usb key my son (away at college) had made using Yubi that had 32 bit versions on it, Xubuntu 14.4, Lubuntu & Slack. It wouldn't boot on my laptop, but to my joy it did boot on my brother-in-law's Toshiba. At least it booted to Yubi, but after I selected Xubuntu it hung up, or was loading verrrry slowly.

I eventually gave up, & was going to see if maybe I could add an older version of Xubuntu for the older computer. But since I at least knew that it would boot to the usb drive I decided to try again, this time using Lubuntu. Amazingly, to me anyway, it did boot to Lubuntu. It also mounted (?) the hard drive on the Toshiba which was another great relief. I attached an external usb hard drive & it could see those files as well. Yay.

I'm also fortunately that Lubuntu is apparently a desktop gui version so I didn't need to know Linux command line. After playing around with it a bit I figured out how to view the files & structure on those drives & to use the file structure tree in Lubuntu.

It took a fairly long time to calculate how much was on the Toshiba HD... ~ 184.8 GB, but it did so. There was enough room on the external usb HD so I selected all of the folders & tried to drag it onto a folder I made on the external drive... but it didn't do anything that I could tell. I waited awhile & then thought maybe I should just try one of the more critical folders to copy, but it wouldn't deselect the files that had been selected, nor do anything else that I tried. I couldn't tell if it was in the process of copying the files, or was just hung up. I tried things like trying to get the drop-down menu for File to give me some options, but nothing moved.

A little later it went into a DOS lookiing command line / text only mode.

First line: [1483.328171] Kernel panic - not syncing: Attempted to kill init! exitcode = 0x00000007

It listed another 22 lines starting with other numbers, all lines starting with:
[1483.32xxxx] The 'x'es all being assorted numbers.

The last line is:
[1483.329399] drm_kms_helper: panic occurred, switching back to text console

The lite on the external usb drive is blinking fairly rapidly. Does that mean it may still be writing data/info to it in the background?

Should I hit the power key to reboot it? Or wait?

Thanks for any additional help/recommendations.

---

### Post by oldfred on 2016-02-05
Best never to press power switch, especially if in the middle of something. That can corrupt file system and then you would need chkdsk.

You may have just selected too much at one time, or NTFS does have some issue and it hung when it hit that issue on drive.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by launchpadnet.justj on 2016-02-05
> **oldfred said:**
> Best never to press power switch, especially if in the middle of something. That can corrupt file system and then you would need chkdsk.

You may have just selected too much at one time, or NTFS does have some issue and it hung when it hit that issue on drive.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Thanks for the reply. I may have missed it earlier, not noticing that there's now a "page 2" for the thread. Sorry about that.

I tried the above & a few variations, some by mistake. I thought that perhaps you might have misspelled R-E-I-S-U-B since the mnemonics both seemed to indicate a spelling of R-S-E-I-U-B. Not sure if the order makes a difference. I tried it both ways, and also with & without the Ctrl key. Nothing seemed to work, unfortunately. Didn't seem to budge.

Fwiw, here's a screenshot of the error codes:

[ATTACH=CONFIG]267131[/ATTACH]

---

### Post by oldfred on 2016-02-05
Pretty sure order is not critical other than starting with R and ending with B.

Do not now enough of details of a kernel crash to know what that is saying.

In hindsight, better to copy some data, not all at once.

---

### Post by launchpadnet.justj on 2016-02-05
> **oldfred said:**
> Pretty sure order is not critical other than starting with R and ending with B.

Yeah, that was the impression I got from [the one link]("http://blog.kember.net/articles/reisub-the-gentle-linux-restart/") you gave me. Hope so.

> Do not now enough of details of a kernel crash to know what that is saying.

In hindsight, better to copy some data, not all at once.

Yeah, I'm kicking myself for trying that now. I almost started doing the couple of folders that I knew were most important to them, or alternatively even just the large Documents & Settings folder.

But, since it's too late now, and I can't seem to get it to do a "soft shutdown" or whatever it is called... any recommendations on how to proceed? Wait a few hours to see if it may finish writing to the external usb HD? or maybe eventually "hear" the request to shut down? ... or disconnect the usb HD (it's still flashing fairly rapidly)? or hit the power button for a "hard shutdown"?

---

### Post by oldfred on 2016-02-05
Some copy functions to USB flash drives thru USB2 ports can be very slow, especially with large amounts of data. The Linux NTFS driver had to be independently developed and may not be as optimal as native Windows driver.

But if kernel has crashed I do not think there is much you can do.

Copying 184GB seems like a very large copy. And even from one internal drive to another internal drive would take a while. My older SATA hard drive is about 70.46 MB/sec or 3/4 hour. But USB ports are slower. The theoretical maximum data rate in USB 2.0 is 480 Mbit/s (60 MB/s) per controller, but expect a lot less.

---

### Post by launchpadnet.justj on 2016-02-05
> **oldfred said:**
> Some copy functions to USB flash drives thru USB2 ports can be very slow, especially with large amounts of data. The Linux NTFS driver had to be independently developed and may not be as optimal as native Windows driver.

But if kernel has crashed I do not think there is much you can do.

Copying 184GB seems like a very large copy. And even from one internal drive to another internal drive would take a while. My older SATA hard drive is about 70.46 MB/sec or 3/4 hour. But USB ports are slower. The theoretical maximum data rate in USB 2.0 is 480 Mbit/s (60 MB/s) per controller, but expect a lot less.

OK, thanks. I guess I'll just wait a few hours just in case. If nothing changes, I guess I'll just have to cross my fingers & power it down.

Thanks again to you & everyone else for all your help. At least I've learned some things and with luck, maybe this will eventually work out ok.

---

### Post by launchpadnet.justj on 2016-02-05
I used the power button to turn it off. Fortunately, it booted right back up & seems to be operating fine.

I was able to drag & drop a small file (257.7 MB) to my external drive with no error messages.

It's copying a larger one now, but it's going very slowly. I can certainly live with that, though.

So far I am as pleased as punch. Lubuntu saved the day! -- as long as Windows can read the files & it didn't corrupt my external drive ;)

Thanks again for everyone's help and input. It is much appreciated!

{Edit: My external drive still works fine & Windows can read the data that was transferred. Thanks too, from my sister-in-law for saving pictures and documents... especially ones she needs now to do her taxes.}

---

