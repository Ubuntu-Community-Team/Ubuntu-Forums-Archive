---
title: "Missing Characters when running 14.04 live off CD"
date: 2015-07-02
forum: Installation &amp; Upgrades
---

### Post by george117 on 2015-07-02
Hi, I'm trying to do a duel boot install on my windows 8 computer.

I can get Ubuntu to boot off the CD but when running it live there seems to be characters from words missing.
I don't really want to go ahead with the install if it's also going to do that once actually installed plus I can't actually read anything on the installation manager

Computer is running Windows 8.1 64Bit and 2gb Nvida graphics

Any help would be great,

Thanks!

---

### Post by dino99 on 2015-07-02
Looks like a missing font on the cd; Only choose an original image :  [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by coffeecat on 2015-07-02
> **george117 said:**
> I can get Ubuntu to boot off the CD but when running it live there seems to be characters from words missing.
I don't really want to go ahead with the install if it's also going to do that once actually installed plus I can't actually read anything on the installation manager

I think you're right not to go ahead, but that’s quite an unusual symptom. A screenshot would be helpful for others to see what you are describing. When booting up from the live CD, choose Try Ubuntu rather than Install Ubuntu, and while in the live desktop session, use the PrtScrn key to get a screenshot of the whole desktop, or alt-PrtScrn for the active window, or shift-PrtScrn to select the area you want to capture. You can then copy the png file to an external USB to have access to it from whatever system you use to post here. Of course, that won't work if the missing letters make it difficult to do any of that.

What version/release number of Ubuntu are you using?

Did you check the md5sum of the downloaded ISO?  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you check the integrity of the CD/DVD from the CD menu? If you need help with that, please post back.

By the way, a Windows 8 machine is almost certainly a UEFI one, and you need to boot the live CD/DVD in UEFI mode. That's nothing to do with your missing characters problem, but if you need help with that, please post back.

---

### Post by george117 on 2015-07-02
I will get a screenshot of it tonight when I can. Suppose it's quite hard to diagnose with you being to see what I can/cannot see on the screen.
I should probably rephrase. Not all the characters are missing just some. Some words are complete and some aren't. 
I don't think that would be a font issue?
I downloaded 14.04.2
And this is the second time I've burnt it onto a cd with seperate downloads from the Ubuntu site
Yes it is Uefi- I have changed the boot settings so secure boot is disabled and put the cd drive above the hard disk in the boot order. The booting doesn't seem to be a problem.
Could it be a problem with the graphics driver?
As for that md5sum I'm not sure what that is but I will have a look tonight when I'm back with my laptop

---

### Post by george117 on 2015-07-03
I have the attatched image below

[IMG]http://i698.photobucket.com/albums/vv345/georgermz/IMG_0198.jpg[/IMG]

---

### Post by Samanta_Makurat on 2016-04-18
Hello, 
I've got the same problem here. Did you work it out somehow?

---

