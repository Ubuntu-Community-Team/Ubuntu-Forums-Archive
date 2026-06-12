---
title: "Installer Error after Wubi install in windows"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by dmparksa on 2011-12-02
I've tried 9.04 in the past, but that turned out to be a disaster because of a huge bug in the update that I did.  I had to reinstall everything and I didn't want to do it again.  But I've been looking into Ubuntu 11.10 and it looked way better than 9.04 was.  So, I gave wubi a try.  I went through the ISO download, burned it to a dvd, put it back in to the computer, run wubi, and everything went flawlessly in windows.  The problem occurs when I restart the computer.  After the install, I restart the computer and everything goes well until the installer.  It gives a warning that the installer could not run properly.  I don't remember specifically what it said, but after doing it over five times, I still could not get it to work.  I figured that someone might have ran into this problem and decided to post here.
Computer Specs:  HP Pavilion a6242n
Windows Vista
AMD athlon 64 X2 4800+  (I think it's around 2.8 ghz)
3gig ram ddr2
320gb hard drive
Nvidio Geforce 6150SE

[SIZE=3]**TL;DR:  There is an installer error when I first run Ubuntu after wubi install.**[/SIZE]

Thanks!

---

### Post by oldtimer7777 on 2011-12-03
I had this same problem, so I just installed it from a live bootable usb thumb drive/flash drive stick instead.

Here is a guide:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **dmparksa said:**
> I've tried 9.04 in the past, but that turned out to be a disaster because of a huge bug in the update that I did.  I had to reinstall everything and I didn't want to do it again.  But I've been looking into Ubuntu 11.10 and it looked way better than 9.04 was.  So, I gave wubi a try.  I went through the ISO download, burned it to a dvd, put it back in to the computer, run wubi, and everything went flawlessly in windows.  The problem occurs when I restart the computer.  After the install, I restart the computer and everything goes well until the installer.  It gives a warning that the installer could not run properly.  I don't remember specifically what it said, but after doing it over five times, I still could not get it to work.  I figured that someone might have ran into this problem and decided to post here.
Computer Specs:  HP Pavilion a6242n
Windows Vista
AMD athlon 64 X2 4800+  (I think it's around 2.8 ghz)
3gig ram ddr2
320gb hard drive
Nvidio Geforce 6150SE

[SIZE=3]**TL;DR:  There is an installer error when I first run Ubuntu after wubi install.**[/SIZE]

Thanks!

---

### Post by Sam_Scribbler on 2011-12-03
> I had this same problem, so I just installed it from a live bootable usb thumb drive/flash drive stick instead.

Were you using Vista as well? When I tried Wubi in 10.04 last year, I had the exact same problem, too! Is this common? I sort of "fixed" the issue by erasing the disk and installing it from scratch. (Easy way out, I know, but it was a clean Vista boot anyway, so no real loss.)

I also had a similar issue in Mint where the installer would crash when installing from a CD-ROM, but would load perfectly from a USB flash drive. And the CD-ROM was pristine... not a scratch on it.

What causes that?

---

### Post by oldtimer7777 on 2011-12-03
IO failure on the cd-rom/dvd-rom device. Age. Wear. Environment.  

USB Flash Drives booted from the USB port are less likely to cause those kinds of read/write issues. 

> **Sam_Scribbler said:**
> Were you using Vista as well? When I tried Wubi in 10.04 last year, I had the exact same problem, too! Is this common? I sort of "fixed" the issue by erasing the disk and installing it from scratch. (Easy way out, I know, but it was a clean Vista boot anyway, so no real loss.)

I also had a similar issue in Mint where the installer would crash when installing from a CD-ROM, but would load perfectly from a USB flash drive. And the CD-ROM was pristine... not a scratch on it.

What causes that?

---

### Post by bcbc on 2011-12-03
> **dmparksa said:**
> I've tried 9.04 in the past, but that turned out to be a disaster because of a huge bug in the update that I did.  I had to reinstall everything and I didn't want to do it again.  But I've been looking into Ubuntu 11.10 and it looked way better than 9.04 was.  So, I gave wubi a try.  I went through the ISO download, burned it to a dvd, put it back in to the computer, run wubi, and everything went flawlessly in windows.  The problem occurs when I restart the computer.  After the install, I restart the computer and everything goes well until the installer.  It gives a warning that the installer could not run properly.  I don't remember specifically what it said, but after doing it over five times, I still could not get it to work.  I figured that someone might have ran into this problem and decided to post here.
Computer Specs:  HP Pavilion a6242n
Windows Vista
AMD athlon 64 X2 4800+  (I think it's around 2.8 ghz)
3gig ram ddr2
320gb hard drive
Nvidio Geforce 6150SE

[SIZE=3]**TL;DR:  There is an installer error when I first run Ubuntu after wubi install.**[/SIZE]

Thanks!
Write down the error. It's likely important. Did it say "no root file system defined" or something like that?

I notice that you have an nvidia card - these usually require the 'nomodeset' boot option. See this thread for details: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (post #8 describes what's required for a wubi first boot)

---

### Post by dmparksa on 2011-12-03
I already deleted the Wubi from the disk.  The only thing I can think of now is trying it on the internal hard drive.  I've been trying to install it on an external hard drive.  (It worked perfectly when I used 9.04)  I'll also try the USB option.  Just as well, I was running out of CD's and I didn't feel like buying some.  The strange thing is, I even get the installer error when I just boot from live CD.  I can try to boot the CD from a different computer and see if the CD is messed up.

---

### Post by bcbc on 2011-12-03
> **dmparksa said:**
> I already deleted the Wubi from the disk.  The only thing I can think of now is trying it on the internal hard drive.  I've been trying to install it on an external hard drive.  (It worked perfectly when I used 9.04)  I'll also try the USB option.  Just as well, I was running out of CD's and I didn't feel like buying some.  The strange thing is, I even get the installer error when I just boot from live CD.  I can try to boot the CD from a different computer and see if the CD is messed up.
If you get a 'no root filesystem defined' error on a wubi install it's usually due to minor partition table corruption, or some other unsupported feature e.g. raid 0 or 1+0. In some cases a reused drive with leftover GPT data can cause it.

But if you get this on Wubi you will have the same problem on a normal install. To diagnose, boot the live USB, select "Try Ubuntu" and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

---

### Post by dmparksa on 2011-12-03
Alright, I didn't try to reinstall, but I did get it on a flash drive.  Now I have a completely different problem.  I have it on a 4gb flash drive and tried to run wubi from it.  Gives the error; "Internal Error(name of the window): Failed to run Pylauncher"  I already tried the Live USB option and it worked perfectly on it.  What's the problem now?

---

### Post by bcbc on 2011-12-03
You can't run wubi from a USB. It is possible but the partition has to be ~< 850MB. 

The easiest way to install wubi if you have the ISO:
1. place the ISO and wubi.exe (from same release) in the same folder on your hard drive
2. remove the USB and any Ubuntu CD's from your computer
3. Run wubi.

---

