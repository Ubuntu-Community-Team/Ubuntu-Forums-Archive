---
title: "Unable To Find A Medium Containing A Live File System"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by tk421awol on 2014-04-05
When I try to run or install Ubuntu from liveUSB, I get the menu option for tr or install, then purple screen, then ubuntu loading, then the error screen: Busybox blah blah "(initramfs) Unable to find a medium containing a live file system."

I'm using an Lenove Thinkbook Twist.  I'm trying to dual boot ubuntu alongside the preinstalled windows 8.  I tried livebooting and installing next to windows, no joy.  I updated to 8.1, still no joy.  I've read every thread I can find here and other forums.  I've tried the offered solutions, and all the steps that worked for others, and I'm losing hope.

I'm using a USB created with pendrivelinux Universal USB Installer. I'm using the iso from ubuntu desktop download page 12.04 LTS.  I checked the md5 checksum and it matches up.  I turned off fast boot. I tried ACHI and compatibility mode (there is no IDE option. I tried using unetbootin and other iso files.  I"ve also tried nearly every variation of BIOS boot device order, and I've tried leaving the bot order alone and interupting the boot screen and choosing a one time boot device.

The only thing I can't change is using USB3.0 ports.  This laptop doesn't have 2.0 ports.

Any ideas or suggestions? Thanks.  TK.

---

### Post by egeezer on 2014-04-05
CAUTION: this suggestion is a guess, I don't know if it will work.  On another distro (MX-14) my LiveCD would not boot, with the notification "no linuxfs detected".  To fix it, I added "load=all" (without the quotation marks) to the boot line and it worked.  

Remember, it MIGHT work on Ubuntu, and it might NOT.  But it does sound familiar.

---

### Post by sudodus on 2014-04-05
I would try another tool to create the USB boot drive, for example ***Unetbootin***, that I know works also with UEFI.

See this link with general information, tips and links about booting from USB

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by tk421awol on 2014-04-06
sudodus:
See paragraph three, sentence six "I tried using unetbootin and other iso files"
I'm sorry if I wasn't clear.  I was trying to say I also tried unetbootin and the ubuntu provided tool after pendrivelinux, and I tried different iso files of each (after doing the checksum).

At this point, I know I have a good thumbdrive with a good linux iso file on it, but I can't boot from the drive, I can't install for dual boot, heck I can't even replace my current OS and go to pure linux box. Whiskey Tango Foxtrot, over.

---

### Post by sudodus on 2014-04-07
Sorry that I overlooked that you have already tried Unetbootin.

Have you tested the pendrive in another computer? You can borrow a computer from a friend or colleague for a few minutes and check that your pendrive can boot it.

***You need a 64-bit desktop version of Ubuntu to boot a system with Windows 8 (and UEFI)***. Most new and middle age computers can run 64-bit Ubuntu, while old computers need a 32-bit version. I think the alternate iso file is *not* made to boot in UEFI mode.

So if you downloaded a 32-bit iso file or an alternate iso file you'll have no luck trying to boot a system with Windows 8 (and UEFI), even if the pendrive is a good boot drive.

-o-

There might also be a problem with hybrid graphics or hybrid SSD-HDD drive, that can be hard to manage with linux, but I don't see any of those at this web page

[http://shop.lenovo.com/us/en/laptops/thinkpad/twist-series/s230u/](http://shop.lenovo.com/us/en/laptops/thinkpad/twist-series/s230u/)

(Is that web page describing your computer?)

---

### Post by tk421awol on 2014-06-17
I'm trying again.  It's been two months, and I can't handle this windows nonsense anymore.

Yes, the laptop is a lenovo thinkpad twist, s230u.  Yes, I pulled a 64 bit image.  I'm trying again with the 14.04 desktop iso from ubuntu's page. checksum matches, and like last time I've tried multiple images on multiple drives created using multiple programs to load the iso and a bootable image.

I've since learned that in addition to quick boot and fast boot, intel SRT must be turned off (which I've done).  I've also set the USB in UEFI to ignore 3.0 and act only as 2.0

Unfortunately, nothing has changed.  Now it's BusyBox v1.21.1, but still initramfs unable to find....

NOTE: The laptop does have a 24GB SDD along with the HDD.

---

### Post by sudodus on 2014-06-17
It could be a problem if there is some kind of built-in RAID arrangement with the two drives. One way to get started might be to install Ubuntu into a third drive, which is independent of the two built-in drives. This is possible with a fast USB 3 pendrive (or a USB 3 HDD). See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Portable installed system booting from UEFI & BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

---

### Post by tk421awol on 2014-06-18
sudodus:

Thanks for sticking with me.  OK, so the 24G SSD is in fact being used for caching.  Expresscache is installed and apparently what's being used.

A few questions:
(1) Do you think I can skip some of these issues by simply choosing to go full linux and choosing install instead of try without installing? (I haven't tried it yet because I need get 100% everything is backed up) Besides triple checking that everything is backed up, I am ready to wipe this thing completely, no half measures or dual booting.

(2) If not, I've got a 32GB USB3.0 thumbdrive I can format and try to install ubuntu on it.  If I get that working, how much of a chore do you think it would be (for a rookie) to get ubuntu up and running on the laptop afterwards? I'm not interested in running my OS from a thumbdrive long term, obviously.

---

### Post by sudodus on 2014-06-19
I have no experience of Expresscache. [I]It would be best if you can get advice from someone who knows about it.
[/I]
1. With a full backup, you should be able to make some experiments. Can you find out where Expresscache is stored (in UEFI/BIOS or in the operating system (Windows))?

2. If Ubuntu works from USB, you know it works with the computer. Then the question is, if Ubuntu can live with Expresscache, or you can remove it.

---

### Post by tk421awol on 2014-06-19
Solution found, problem solved.  I uninstalled expresscache, and more importantly found out I was using bios 1.65 from lenovo. I updated to 1.67 and tried again.  Voila, "try it without install" worked fine. I installed 14.04 entirely on the SDD and then used GPartEd to unmount and wipe the HDD.

My only issues now are nonfunctional wireless (I guessing a driver issue that should be solved quickly) and figuring out how and what to move to the HDD.  

Thanks for all the help.

---

### Post by sudodus on 2014-06-20
Congratulations and thanks for sharing your solution :KS

Maybe you can find tips at the Ubuntu [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") forum. Start a new thread there, if you need more help to get the wireless working.

---

