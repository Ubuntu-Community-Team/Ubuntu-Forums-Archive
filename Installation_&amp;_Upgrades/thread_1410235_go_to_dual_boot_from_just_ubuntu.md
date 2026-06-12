---
title: "go to dual boot from just ubuntu"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by jakerman3 on 2010-02-18
Hi I have an acer aspire one and I installed ubuntu netbook remix from xp. I did the entire system instead of dual boot and it works great. Now however i need to run some windows apps, so I tried installing windows again, but the install disk says there isnt a harddrive in the computer. I did the most logical thing i thought of and ran gparted and formatted the harddrive for NTFS, it still didnt detect the harddrive so i tried unformatted and fat32 to no avail. gparted stopped working so i took the harddrive out and plugged it into my desktop and ran gparted again. it still didnt work so i ended up just reinstalling ubuntu and left 80gb of the 160gb harddrive unformatted in hopes of maybe a post dualboot install. There is nothing important on my computer so i dont mind reformatting it or anything. Any help would be appreciated, thanks

---

### Post by Mark Phelps on 2010-02-18
> **jakerman3 said:**
> Hi I have an acer aspire one and I installed ubuntu netbook remix from xp. I did the entire system instead of dual boot and it works great. Now however i need to run some windows apps, so I tried installing windows again, but the install disk says there isnt a harddrive in the computer. I did the most logical thing i thought of and ran gparted and formatted the harddrive for NTFS, it still didnt detect the harddrive so i tried unformatted and fat32 to no avail.
You didn't mention what version of XP you had running or what version you had on CD, but laptops (this is a laptop, right?) quite often have SATA drives, and drivers for those didn't show up in XP until SP1.  So, if you have a SATA drive, and an original XP CD, it won't see the hard drive until you load the SATA drivers.

>  gparted stopped working so i took the harddrive out and plugged it into my desktop and ran gparted again. it still didnt work ...
Saying "didn't work" is not useful for diagnosing problems.  We need to know what specifically happened.

> so i ended up just reinstalling ubuntu and left 80gb of the 160gb harddrive unformatted in hopes of maybe a post dualboot install. There is nothing important on my computer so i dont mind reformatting it or anything. Any help would be appreciated, thanks

Think you'll have to sort out the driver issue before you can do anything regarding an XP reinstall.  Until it can "see" the drive, there's not much you can do.

---

### Post by jakerman3 on 2010-02-18
I have and external disk drive, i used the xp install disk from my desktop, im sure its atleast sp2, and my disk drive in my desktop uses sata so it should work. I was running gparted off of usb and it would freeze when shutting down then it wouldnt startup every time. I think it was a unetbootin problem so i just burned it to a disk and it worked much better.

---

### Post by oldfred on 2010-02-18
When you formated the NTFS partition did you make sure it was a primary, Win will only install to a primary partition.

---

### Post by Hukei on 2010-02-18
This is basically easy fix if you know how to use the right software, I'll just point you to the software and things to do, try doing some research on that, shouldn't be too hard.

-Try first searching for the drivers at the acer.com page for your specific model of the acer aspire one (the specific model should be under the laptop in a white sticker or something similar). You will surely find something there that will point you to the right drivers for your hard disk drive.

-After finding the drivers, download them and since your Windows XP Install Disc surely do not have any of these you have to inject them into the CD by copying all the Windows XP CD contents into an empty folder in your computer and using nlite ([http://www.nliteos.com/](http://www.nliteos.com/)) to inject them and create an iso (in other words, a cd image).

-Burn the iso into a cd and put it into your computer.

-Boot it up. It should show now your hard disk drive at the installation of the Windows XP.

I'm sorry I can't put much more detail into this since I'm running low on time, I gotta do some stuff. Feel free to pm me or just write something under this post. I'll try to reply tomorrow.

---

### Post by JPWhite on 2010-02-18
Adding to what the other Posters said, after you have got XP to recognize your HDD using the advice given so far, delete all partitions and install XP.

Then install Ubuntu. XP will re-write the master boot record wiping out Grub, so it is best to install Ubuntu last.

Another option if you don't need maximum performance from XP, is to install VirtualBox and install a virtual XP image and run it when you need to. That way you will avoid the HDD driver issues, it will just install. Of course it will be a little slow and will require a decent computer with plenty of ram to run Ubuntu and XP at the same time. Even better run XP with VirtualBox from an external HDD and it won't 'pollute' your hard drive ;)

---

