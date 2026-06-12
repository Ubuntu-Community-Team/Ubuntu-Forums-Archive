---
title: "Dell Inspiron 15 3558 laptop failed installation."
date: 2017-01-15
forum: Installation &amp; Upgrades
---

### Post by YMS_1975 on 2017-01-15
Hey guys,

I'm trying to install Ubuntu 16.10 on my sons Dell Inspiron 15 3558 laptop. I just can't get it to install. Instead I get a bunch of error messages as I try different boot options such as possible corrupt media (and yes, I've tried different medias), or that it can't read/find a file. The problem is, I can't recreate the error messages because I've tried so many different BIOS options (and each one seems to create a whole new set of problems), otherwise I'd post them up for you. I apologize for the picture quality, because the laptop currently does not have an OS on it, so I can't take screenshots.

If I press F12, I enter the Dell's BIOS/Boot menu. This is what I see : 
[http://s38.photobucket.com/user/yms2/media/20170115_130126_zpst0bhyvei.jpg.html](http://s38.photobucket.com/user/yms2/media/20170115_130126_zpst0bhyvei.jpg.html)

If I go to **BIOS Setup**, this is what I see : 

[http://s38.photobucket.com/user/yms2/media/20170115_125227_zps22nnec04.jpg.html](http://s38.photobucket.com/user/yms2/media/20170115_125227_zps22nnec04.jpg.html)

If I scroll down to **Change Boot Mode Settings** (Under the **General, Boot Sequence** heading, this is what I see : 
[http://s38.photobucket.com/user/yms2/media/Mobile%20Uploads/20170115_122546_zps15xit5um.jpg.html](http://s38.photobucket.com/user/yms2/media/Mobile%20Uploads/20170115_122546_zps15xit5um.jpg.html)

If I put my Ubuntu 16.10 DVD in the tray & boot it up, it'll read the DVD but it won't install it.

I'm sure I'm missing some critical information to provide you guys, but if you let me know what you need to help me, I'll be more than happy to provide that info. if I can find it. Can somebody please point me in the right direction? I really want to get Ubuntu on this laptop.  :confused:

---

### Post by oldfred on 2017-01-15
If Windows is UEFI, you should boot & install Ubuntu in UEFI mode.
You have to boot installer in UEFI mode to install in UEFI mode.
While some have issues with flash drive install, that usually is quicker, but DVD should work.

So turn off all legacy settings and make sure you only have UEFI on.

Best to use Windows to shrink the main Windows NTFS partition and immediately reboot so it can run chkdsk.
Make sure Windows fast start up or always on hibernation is off.
Fully backup Windows. My Dell SFF system wanted a Windows back, a Dell Backup & I did a full image backup with Macrium Reflect.

Lots more details and many links on UEFI in link below in my signature.
Most important of those links:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by YMS_1975 on 2017-01-15
> **oldfred said:**
> If Windows is UEFI, you should boot & install Ubuntu in UEFI mode.
You have to boot installer in UEFI mode to install in UEFI mode.
While some have issues with flash drive install, that usually is quicker, but DVD should work.

So turn off all legacy settings and make sure you only have UEFI on.

Best to use Windows to shrink the main Windows NTFS partition and immediately reboot so it can run chkdsk.
Make sure Windows fast start up or always on hibernation is off.
Fully backup Windows. My Dell SFF system wanted a Windows back, a Dell Backup & I did a full image backup with Macrium Reflect.

Lots more details and many links on UEFI in link below in my signature.
Most important of those links:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Well,

I don't have Windows on it, so backup is not an issue.
I verified that everything is set UEFI and now I have the following error messages : 

[IMG][[IMG]http://i38.photobucket.com/albums/e141/yms2/20170115_141547_zpsyg9uaggf.jpg[/IMG]](http://s38.photobucket.com/user/yms2/media/20170115_141547_zpsyg9uaggf.jpg.html)[/IMG]

[IMG][[IMG]http://i38.photobucket.com/albums/e141/yms2/20170115_142655_zpso9uj09f2.jpg[/IMG]](http://s38.photobucket.com/user/yms2/media/20170115_142655_zpso9uj09f2.jpg.html)[/IMG]

---

### Post by ubfan1 on 2017-01-15
Did you hashcheck the downloaded ISO file?

---

### Post by YMS_1975 on 2017-01-15
> **ubfan1 said:**
> Did you hashcheck the downloaded ISO file?

To be honest, I don't even know what that means let alone how to do it. On my personal desktop, I've always just plopped in the DVD, rebooted my desktop and the installer would launch.

If it helps, I downloaded the ISO file directly from the Ubuntu.com website.

---

### Post by oldfred on 2017-01-15
Check that download was correct:
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

Is that from DVD or flash drive?
Seems like some error on reading device.

What video card/chip?

---

### Post by RobGoss on 2017-01-15
Hello and welcome, You should post the specs for this machine that you're trying to install Ubuntu on this will help everyone give you the best possible answer to your problem

What program are you using to burn the Ubuntu ISO file to that **DVD**?

Have you tried installing the** ISO** file on a **USB **thumb drive and booting from that?

Are you able to run the live **desktop environment **and does it preform well? 

Sometimes depending how old the machine is hardware plays a key roll on how things work, in your case I have no idea how old this machine is so I would just be guessing

The newer computers are a bit more complex do to the fact we now have to deal with **UEFI** mode and jumping threw hoops to get Linux installed but none the less possable

The more information you can provide about your system the better it will help others to direct you in the right direction 

The Low graphic mode sounds like a driver issue, not saying you cannot install Ubuntu on that machine you'll be surprise what you can accomplish with Linux it just takes a bit of reading, you can read up on that problem here [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

---

### Post by YMS_1975 on 2017-01-15
OK....

I didn't check the hash on the original ISO file; I just burned it straight to DVD using Power ISO. So...I've re-downloaded the ISO file. But before I paste the results of what the MD5checksum program results are, I just want to point out another nugget of info. I excluded. I downloaded Linux Mint in a bid to see if that would work, and I had the exact same results.

Anyways, I used a Windows app called **MD5 & SHA Checksum Utility 2.1** to test the re-downloaded ISO file. Here are the results : 

MD5 : 3F50877C05121F7FD8544BEF2D722824
SHA-1 : AEE0709D07D43494D7AA13457B4E255B0A12D1CF
SHA-256 : 4405C37D61B5CAC6C89EAF379C035058ED7DB8594ABD209337276C7C4556787E
SHA-512 : 8518086C1AF5A536C6E2362ED750BECBA87365F32F70D98D15776695C91C4B47766A6215450CEF99FA2C7896C943A46AA4BBFA9F81B5B6C3B10AA1AF058031AC

As for whether or not I tried a USB thumb drive, I did not (as I don't have one right now).

As for the specs on the laptop, here's a direct link to the laptop in question : [http://www.pcmag.com/review/346462/dell-inspiron-15-3000-series-3558](http://www.pcmag.com/review/346462/dell-inspiron-15-3000-series-3558) or [ftp://ftp.dell.com/Manuals/all-products-infodev/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-3558-laptop/inspiron-15-3558-laptop_reference%20guide_en-us.pdf](ftp://ftp.dell.com/Manuals/all-products-infodev/esuprt_laptop/esuprt_inspiron_laptop/inspiron-15-3558-laptop/inspiron-15-3558-laptop_reference%20guide_en-us.pdf). It's brand new actually; we just purchased it from Best Buy like three weeks ago.

---

### Post by oldfred on 2017-01-15
A lot of Dells use Intel SRT which is seen as RAID.
You may need to check if drive in UEFI is RAID or AHCI, should be AHCI, but that may interfere with Windows which then needs AHCI driver which if it does not have, you need to install first. One more reason for several flash drives to back up system. Microcenter has a store near me in Illinois & I regular buy a new one. (Or I try not to go to store too often as at checkout I see price has fallen or USB3 almost same as USB2 or larger size available, or I always get a new flash drive.)
 [https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/) 



       Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)
Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)

---

### Post by YMS_1975 on 2017-01-15
Hey guys,

So....I think the problem was with the hash because after I redownloaded Ubuntu, I ran the hash checker and matched it with the hash on the Ubuntu website (or wherever I found it) and they matched.
So, I tried to reinstall it and wouldn't ya know it? 

IT WORKED! I never would have thought of the hash as this never happened to me before, and up until today I never even knew about MD5 Checksum. So....at least I learned something new.  Thank you so much guys! :P

---

### Post by RobGoss on 2017-01-16
Glad you managed to get it all sorted out if you resolve your issue you can mark this thread as solved. You can do this by using the Thread tool tab at the top of this post

Thank you

---

