---
title: "No valid partition found when trying to install Windows XP"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by AsianInvasion on 2010-02-06
So I just partitioned my 500GB HDD into two parts one with ubuntu and an empty one formatted in NTFS. When I run the setup.exe from the disk inside ubuntu I get the no partition found and then the setup closes. I need help with this!

---

### Post by subodh.rohilla on 2010-02-06
You can't run .exe files properly in ubuntu. Just boot from the xp CD and install it in ntfs partition , this will remove ubuntu from the startup. To recover grub : [http://ubuntuforums.org/showthread.php?t=223031]("http://ubuntuforums.org/showthread.php?t=223031")

---

### Post by AsianInvasion on 2010-02-07
> **subodh.rohilla said:**
> You can't run .exe files properly in ubuntu. Just boot from the xp CD and install it in ntfs partition , this will remove ubuntu from the startup. To recover grub : [http://ubuntuforums.org/showthread.php?t=223031]("http://ubuntuforums.org/showthread.php?t=223031")

The problem is my XP CD doesn't auto run when I put it in my drive and restart the computer it still boots into Ubuntu. While if I put my live CD in it boots into it. Whats going on?

---

### Post by darkod on 2010-02-07
Are you sure the XP CD is good? Have you used it recently? You can't install XP from within ubuntu. If your computer can't boot your XP cd, then I don't know how to do it. Since it can boot the ubuntu cd I guess that means that in BIOS you have CD before HDD set up, and that's the correct way.

---

### Post by AsianInvasion on 2010-02-07
I haven't used the CD before my friend burned it for me so maybe its a bad CD.

---

### Post by darkod on 2010-02-07
> **AsianInvasion said:**
> I haven't used the CD before my friend burned it for me so maybe its a bad CD.

Or he just copied another cd. In that case the boot sector would not have been copied. You can't replicate bootable cds with just copying the files from them. The boot sector is "invisible" and an image has to be made from the original cd, and then the new cd to be created from that image.
That would explain why you can't boot from it, but you can see the files on it.

---

### Post by Mark Phelps on 2010-02-08
> **subodh.rohilla said:**
> You can't run .exe files properly in ubuntu. 

Actually, you CAN run .exe files in Ubuntu -- if you install Wine or one of the similar products.

However, you can't use these products to install MS Windows (or Windows drivers); you can only use them to run some MS Windows apps.

Just wanted to make that clear in case folks start ranting on about using Wine to do this.

---

### Post by LinuXGo on 2010-02-20
Hi, I've yet bumped on this thread similarly to my issue, I once tried to install windows operating system while setting on a Linux operating system. The result is true as you guys pointed out that it can't be done within a Linux environment and its true that my computer can't detect the windows installation disc but it recognized it as a blank CD-R. So, all I have to ask is whats the name of the windows installation disc's image? Is it Microsoft Corporation .img? I apologize if thats a foolish question but I had never recently heard of the image's name.

---

### Post by Mark Phelps on 2010-02-21
> **LinuXGo said:**
> So, all I have to ask is whats the name of the windows installation disc's image? Is it Microsoft Corporation .img? I apologize if thats a foolish question but I had never recently heard of the image's name.

There's no single "img" file that suffices for all Windows OS installations.  It varies by OS (XP, Vista, Seven) and by version (Home, Pro, Business, etc), and by type (Retail, OEM, Enterprise VLK).

---

