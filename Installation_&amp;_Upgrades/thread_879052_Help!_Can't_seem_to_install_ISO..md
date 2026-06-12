---
title: "Help! Can't seem to install ISO."
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by Everglades on 2008-08-03
This is my first post. I downloaded the most recent version of Ubuntu and changed my computer Bios so that the CD would be the 
1st boot drive.  During the boot process I can hear the drive spin up, but nothing happens. Eventually windows xp appears instead of Ubuntu. 

My system is an old IBM thinkpad I series purchased in 1999 originally with windows ME. Iv'e upgraded to XP but because I only have a 4 gigabyte disc drive and 160MB RAM I thought Ubuntu might be a more efficient OS.  

Any suggestions? I downloaded the alternate 386 version and tried that but got the same results.

---

### Post by Pumalite on 2008-08-03
Burn a new CD after doing md5sum, at 4x or less. Do not use CD-RW. Burn as an 'image' not 'data'
Follow this:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by xen-uno on 2008-08-03
Do you have a factory OS disk (W98, W2K, XP, etc) handy? Throw one of those in and see if it'll boot off it. If it doesn't, then it's a hardware or BIOS problem. If it does, then something is wrong with your Ubuntu disks. You did burn the iso with an image burner, ie ImgBurn?

---

### Post by Everglades on 2008-08-03
Thanks: I burned the initial cd as data using Nero.  Can I use Nero and burn an image or do I need to download the additional software you suggested?

---

### Post by xen-uno on 2008-08-03
I have Nero 6.6 and it'll burn images just fine (burn as data is where you went wrong apparently) ... but the most foolproof method is to use ImgBurn ( [http://www.imgburn.com/](http://www.imgburn.com/) ). Make sure you check the Verify box. Though Ubuntu has really good burning apps, IB is one I'd really like to see a native port of (IrfanView too).

---

### Post by Pumalite on 2008-08-03
When you install ImgBurn (made by the legendary maker of DVD Decrypter) go to Mode>ISO>Burn. You can choose 1x as speed of burn

---

### Post by Everglades on 2008-08-03
Does it matter whether I use the first download vs. the alternate 386 download?  I'm not sure I understand the difference in the two.

---

### Post by coffeecat on 2008-08-03
You can use Nero if it supports burning an image. If not, download the free burning software in the link above. You can tell if you burnt the CD as data - if you look at it in a Windows explorer window there will be one whopping great big file called ubuntu*.iso. When you've got it right there should be a few folders and half a dozen files visible.

But..... I don't think 160Mb is enough. If that's the live CD you're trying to burn, it simply won't run - the live CD needs much more RAM to run than a hard disc install. Even if you install from the alternate CD, Ubuntu will run very slowly, if at all, in 160MB. The Gnome desktop is quite memory hungry.

Have a think about [Xubuntu]("http://www.xubuntu.com/"). It needs less memory than Ubuntu. From that website:

> 
**Minimum system requirements**

 To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only requires you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").
 To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.**Edit:** Whoops! Didn't even read the quote I gave you properly. :oops: You're going to have problems with Xubuntu with only 160Mb RAM it seems.

---

### Post by lisati on 2008-08-03
> **Everglades said:**
> Does it matter whether I use the first download vs. the alternate 386 download?  I'm not sure I understand the difference in the two.
It can make a difference which image you download. The "desktop" cd (also known as a "live CD") gives you a chance to try out *Ubuntu before actually installing it, and the "alternate" has a text-based installer that doesn't allow for a test-drive.

Looking at the system specs that I've noticed in this thread, 160Mb of RAM might be a little low for the "Live CD" version.......

---

### Post by xen-uno on 2008-08-03
A (4) GB HD won't allow much either as you'll definitely need a swap partition. Your short on both RAM & HD space.

---

### Post by Everglades on 2008-08-03
Thanks for you help.  I just tried an image cd that I burned and it booted from it.  Now whether I'll get much further seems to be questionable given my system constraints.  I'm puzzled because I thought one of the benefits of Linux was that it was not a system hog.  If it uses the same amount (or more) resources than XP, then purhaps this has been an excersize of futility.  Oh well, I had nothing better to do this Sunday than try.

---

### Post by xen-uno on 2008-08-03
It's not really ... at least compared to Vista. My XP x64 sys partition (without swap file and applications stored elsewhere) uses 5.5 GB of disk space. Ubuntu x64 uses 12.9 GB of space including applications. As far as RAM goes, 160 MB would cause alot of disk paging even with W2k/XP. My XP install is typically using ~ 500 MB of RAM right after bootup ... ditto for Ubuntu (currently @ 830 with FireFox, Thunderbird, Pidgin, and Amorak running). I don't think the Ubuntu's swap file has ever budged off 0 bytes used.

---

### Post by Pumalite on 2008-08-03
If you have 256 MB of RAM or less I'd go for XUbuntu Alternate CD

---

### Post by Everglades on 2008-08-03
Oh well. Ubunto install alternate cd froze up whle trying to install software.  I'm downloading xubuntu now and will give that a shot.  Thanks to the link for xubuntu.

---

