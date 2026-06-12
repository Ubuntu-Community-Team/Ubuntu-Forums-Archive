---
title: "Need help lubuntu will not boot after install"
date: 2016-05-05
forum: Installation &amp; Upgrades
---

### Post by clay6 on 2016-05-05
I just installed lubuntu 16.04lts on a dell dimensions 2400: pentium 4 2.53ghz, 512mb ram, 80gb hard drive, and it is not getting past it just hangs on the first boot text but(see below). i have also tried xubuntu and ubuntu which i can actually click and get into the try xubuntu/ubuntu without installing but when i click install on xubuntu the same thing happens but it gets to the boot logo then hangs on a black screen with no text any ideas?
[COLOR=#000000][FONT=Ubuntu Mono]/dev/sda1: clean, 121563/920272 files, 701079/3680256 blocks
[/FONT][/COLOR]

---

### Post by clay6 on 2016-05-05
forgot to post what im using on usb: 32Bit live Usb using unetbootin

---

### Post by ajgreeny on 2016-05-06
Possibly a problem with the graphics card; do you know what graphics the machine has?

Did the live system run OK or did you go straight to installing?

---

### Post by clay6 on 2016-05-06
Thanks for the reply

---

### Post by clay6 on 2016-05-06
Hey thanks for the reply integrated graphics 845gv chipset but i set it to 128mb of vram (its shared). Whenever i boot into trying it for free on xubuntu to it works but the install gets stuck at the thing i mentioned above. Lubuntu is a different story lubutntu wont even let me try it let alone try to install it.

---

### Post by ajgreeny on 2016-05-06
Yes, it is the graphic card problem that I suspected.

Have a read through the two threads at
[http://ubuntuforums.org/showthread.php?t=2321734&p=13482015#post13482015](http://ubuntuforums.org/showthread.php?t=2321734&p=13482015#post13482015) and
[http://ubuntuforums.org/showthread.php?t=2322941&p=13481986#post13481986](http://ubuntuforums.org/showthread.php?t=2322941&p=13481986#post13481986)
which explain the problem and may give you a few options. It seems to be a Lubuntu problem only, not Xubuntu, but it is possible that you may be able to start Lubuntu by using the nomodeset boot option as shown in one of those two threads, and then installing the apparently missing xserver-xorg-video-intel' and 'xserver-xorg-video-intel-dbg packages.

I have not tried this personally yet but intend to when I have the time to mess around installing and configuring the new system.

---

### Post by clay6 on 2016-05-06
I wouldnt know how to install the missing drivers but i also have the same problem with xubuntu after install it hangs on that boot screen but with a bunch of text and numbers which im thinking is it trying to read from hard disk and finding files but not booting them. Sorry i took so long to reply i Cut my thumb wide open and had to go to the walk in clinic

---

### Post by Eventvwr on 2016-05-14
> **clay6 said:**
> I wouldnt know how to install the missing drivers but i also have the same problem with xubuntu after install it hangs on that boot screen but with a bunch of text and numbers which im thinking is it trying to read from hard disk and finding files but not booting them. Sorry i took so long to reply i Cut my thumb wide open and had to go to the walk in clinic

This thread seems to be the same issue but with a bit more information --> [http://ubuntuforums.org/showthread.php?t=2322111](http://ubuntuforums.org/showthread.php?t=2322111)

I hope your thumb is okay

---

### Post by clay6 on 2016-06-01
its fine thanks but i finally got it to work i just installed 15.10 instead just to be easier

---

### Post by mörgæs on 2016-06-01
Good, when it's running out of support in July there are several options for installing 16.04.

---

