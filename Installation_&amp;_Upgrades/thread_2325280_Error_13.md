---
title: "Error 13"
date: 2016-05-20
forum: Installation &amp; Upgrades
---

### Post by cobras on 2016-05-20
Greetings Good People,

I just acquired a laptop ([FONT=arial]Toshiba Satellite C55-A5286, 8GB, Intel(R) Core(TM) i3-3120M CPU 2,5GHz, 700GB HD) running Windows 8.

I tried to install Ubuntu (14, I believe) using UNetbootin.  UNetbootin installed fine, but when I boot up and choose it I get the following error and can't go further:

Error 13:  Invalid or unsupported executable format

I've searched this forum and googled around but can't find anything useful.  Any suggestions would be most welcome.
[/FONT]

---

### Post by oldfred on 2016-05-20
Not sure what error 13 is.
I might try a different installer, although Unetbootin is usually the better one. Did you verify download was correct with md5sum?
       [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb
[/URL][https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

Other now older installs, but process should be similar:
 Toshiba C55D-A5163 - Installation of Lubuntu on computer with Windows 8.1 Feb 2015
[http://ubuntuforums.org/showthread.php?t=2267268](http://ubuntuforums.org/showthread.php?t=2267268)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

---

### Post by cobras on 2016-05-21
> **oldfred said:**
> Did you verify download was correct with md5sum?

I was completely unaware of md5sum.  Thanks for that.

I thought the easiest thing to do was uninstall and reinstall a different version.

Now I get as far as choosing a mirror but get the old 'Bad archive mirror' error.  I've google around, but can't figure it out.  Thought it might have something to do with the earlier 'No network interfaces detected', but I'm pretty sure this is just an old, lingering bug.  Am I wrong?

Might help to mention the mirror: us.archive.ubuntu.com

Thanks in advance.

---

### Post by oldfred on 2016-05-21
I just had a similar archive error. 
But I was trying to use zsync and change from the daily to the 16.04. But paths on local mirror were different, so it did not work.
Once I got paths straigtened out then it worked ok.

Just download from 
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) 

And mirrors if elsewhere in USA.
      
 Daily builds
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Update Mirrors:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
Install ISO Mirrors:
[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)
[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

---

### Post by cobras on 2016-05-25
OK, I've marked this thread as solved even though I never really figured out why UNetbootin failed (probably a corrupt download), or why the mirror error.

The good news is that I've got Ubuntu 16.04 installed alongside Windows thanks to a USB stick.  Of course, I now have a whole new set of issues to contend with, but I'll search around or start new threads as I deal with them.

Thank you.

---

