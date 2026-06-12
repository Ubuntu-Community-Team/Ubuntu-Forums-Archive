---
title: "Ubuntu wont  boot"
date: 2005-02-06
forum: Installation &amp; Upgrades
---

### Post by dueyfinster on 2005-02-06
I am running Win WP SP2 and have a Dell Dimension 8300. I try to boot from the CD I burned when I downloaded Ubuntu, but my PC keeps skipping over it and loading Windows. I have changed the boot preference order so that my CD Drive is No.1, but it makes no difference. Any Ideas?

Thanks!

---

### Post by Gary Powers on 2005-02-06
That's happend to me several times and it has always been a bad recording.  .ISO files are recorded differently I believe.

Trying downloading a trial version of NERO and using it to burn your CD.  Or maybe just slowing down the record speed of whatever program you are using.

BTW, Ubuntu is worth the effort.

Gary

---

### Post by ulefr01 on 2005-02-06
[QUOTE=dueyfinster]I am running Win WP SP2 and have a Dell Dimension 8300. I try to boot from the CD I burned when I downloaded Ubuntu, but my PC keeps skipping over it and loading Windows. I have changed the boot preference order so that my CD Drive is No.1, but it makes no difference. Any Ideas?

Thanks![/QUOTE]

Maybe your burned CD is not made correctly so that your Cd is not bootable !

Please check with md5sum of the downloaded Ubuntu iso file and verify with what should be reported.

If it is not the same ; please do the download again and check md5sum again before you burn the Cd

---

### Post by tcscushing on 2005-02-06
[http://www.ubuntulinux.org/wiki/BurningIsoHowto](http://www.ubuntulinux.org/wiki/BurningIsoHowto)

For Microsoft Windows XP-SP2 computers, with highspeed download, you can get the .iso files (5 to 6 hundred megabytes) from: [http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/) 

Most people will want to start with the ".ISO" file for "i386" "Live". The file will be at least 500MB. 

After downloading the ".ISO" file to your desktop, in WXP, make sure your file explorer settings allow you to see file extensions, so that you can verify that the file has an ".ISO" extension (if not, rename the last 3 letters of the file to "ISO"). For making a CD image, DO NOT try to "extract" any of the files contained within the .ISO image. 

Then, as of Feb 2005, you should be able to go to this free website, and download this utility: [http://isorecorder.alexfeinman.com/Beta.htm](http://isorecorder.alexfeinman.com/Beta.htm) 

After installing this utility, Windows XP will be able to control the CD burner by just right-clicking on the ISO file, and the first menu option is "Copy image to CD". The only adjustment to be made is to run the settings down to 8x (for a more reliable burn). 

Next, try something that you KNOW will work, FIRST. So get your MSWIN install-CD (98 or ME or WXP) and discover whether or not your CD will boot. (That is, try a "factory" CD first, as it is easy to make buggy CD-Rs, due to drive or driver or media problems). 

Now, put the Ubuntu Live CD into the drive, and reboot. If you get a desktop, be patient, as this thing is not using your hard drive, and takes time to access menu choices. Also, for you WXP-heads like me, you get out of Ubuntu by clicking on the desktop's second menu item near the top of the screen, and at the bottom of the menu it says you can "log out". 

You will find Spreadsheets, Word Processing, Games, and much more, all preinstalled on the demo CD! 

Just a word about booting from CD. Make sure that this CD drive is the only one with a CD loaded into it, and remove any diskettes. Also, just before the OS announces that it is booting, (like maybe when it is counting memory), try hitting the ESC key a couple of times, in hopes that you'll get a "boot device menu" or maybe the motherboard will prompt you with "Hit any key to boot from CD:". Then really-quick hit the "any" key. (If your keyboard has no "any" key, then hit a SPACE or ENTER key!) 

If you need to get into the BIOS, first don't be afraid of it. The only way to close any door that you can't re-open is to turn off the power during a BIOS upgrade, or to do a BIOS upgrade with a corrupted file. Otherwise, while you are warned that a false step can render the system non-bootable, just remember that you can usually go back into the BIOS and reverse any settings that you made. Make good notes. In the worst case, you may have to "clear" the BIOS back to it's defaults, by removing the battery or jumpering the Motherboard to clear the settings. (But use common sense. Don't experiment on the company's payroll computer the day before payday.) 

Many computers require that you tap the DEL or the F10 key, to get into BIOS. Some want you to hit the F1 or F2. In the old days, we had to hit a ctl-alt-esc or F1 or F2. But if the OS announces that it is booting, and it is the wrong OS, then it's too late, and you may as well reboot immediately, to try again to get into the BIOS. 

The standard boot order that most computers are set up with is, first-CD, second-floppy, third-HD. The motherboard, more specifically the BIOS, will decide whether there are more choices, or other available devices to boot from. For example, a LAN-boot would require a bootable disk image to be available on a server, and an ethernet card set up to know how to invoke that image upon boot. Likewise, it is here that you would instruct the computer to boot from an external USB device, if you have enabled "legacy USB" support. 

If you don't see the Internet over your LAN/Ethernet, try removing power from your modem or Router, count 3 and power back on, just before you power up the computer (helps coax it to properly answer the DHCP request). In the menu at the top of the page, hit the little "world" icon to see if you can get a web page.

---

### Post by Sye d'Burns on 2005-02-06
[QUOTE=tcscushing]After downloading the file to your desktop, in WXP, make sure your file explorer settings allow you to see file extensions, so that you can verify that the file has an ".ISO" extension (if not, rename the last 3 letters of the file to "ISO").  For making a CD image, DO NOT try to "extract" any of the files contained within the .ISO image.[/QUOTE]

Wow, that was one hell of a howto. If what tcscushing said didn't work for you I'd suggest a sledge hammer.  :lol: 

Seriously though, make sure when you're burning the disc that you ae **NOT** burning it as a data disc. You need to burn it as an image for it to boot correctly.

---

### Post by dueyfinster on 2005-02-06
Thanks I got it working! I love the desktop!  The mouse was hard to use but after readjusting it worked perfectly.

 I have already downloaded it for install, and  have tryed to install it, but it looks for drivers for my cd drives, on a floppy (but I dont have a floppy disk drive on my pc). It will not let me continue until I resolve this problem. Any Ideas?

and WOW that was some How To! Thank you very much. Much Appreiciated!

---

