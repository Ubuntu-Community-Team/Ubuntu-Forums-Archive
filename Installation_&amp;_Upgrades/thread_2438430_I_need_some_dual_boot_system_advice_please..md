---
title: "I need some dual boot system advice please."
date: 2020-03-12
forum: Installation &amp; Upgrades
---

### Post by koollaydtac on 2020-03-12
I need some dual boot system advice please. My wife got this laptop from her daughter as a gift that was originally set up with Windows 10 on it. Well she didn't have hard drive space at all because the hard drive for it was only 30 gbs. So I backed up her entire drive and installed a clean copy of Ubuntu 18.04 LTS on it which is what I am using myself. Well recently months later she told me she wanted Windows 10 back so she could grab up some flash updates and everything before it's phased entirely out so she has them for her Facebook games and whatever else. 

So my question is this. Is it possible to set up her laptop as a dual boot system like how I set mine up since her external hard drive is a 1 tb drive? I was thinking it'd be better for her copy of Windows 10 to be there anyway. If this is possible to do can someone please tell me how so I make sure I don't mess it up again? I am thinking I can image the OS partition on the external drive and just run the Grub install, but I want to double check before I actually do anything. Any help would be greatly appreciated. Thanks in advance. :)

---

### Post by oldfred on 2020-03-12
Windows does not install to external drives. It is licensed to only one system, so portable drives are not allowed.
If internal drive is only 30GB is this a very lightweight system?

Even Windows in 30GB is not much room.

I would backup everything. And reinstall to external drive & restore from backups.
Then you can install Windows to internal drive.
Just be sure to install in same boot mode, probably UEFI as all new Windows systems are UEFI by default.
But when you install, it is how you boot install media UEFI or BIOS on how it installs.

With Ubuntu on external drive better to have an ESP - efi system partition on external drive.
Ubuntu's Ubiquity only installs grub to internal drive's ESP. But you can use Boot-Repair or manually reinstall grub to external drive. Otherwise if you disconnect external drive, grub on internal drive will have to have external drive connected.

---

### Post by koollaydtac on 2020-03-12
> **oldfred said:**
> Windows does not install to external drives. It is licensed to only one system, so portable drives are not allowed.
If internal drive is only 30GB is this a very lightweight system?

Even Windows in 30GB is not much room.

It's one of those Notebooks so ya I'd say it's a very lightweight system mate. And your right 30 GB is just not much room at all. That's exactly what I am saying. I still can't imagine what possessed them to even remotely think it was a good idea to put a 30 GB OS on a 30 GB hard drive mate. They obviously didn't pass math class in High School. lol :D 

I also want to be clear. I am not talking about installing Windows to make it portable. I am talking about restoring the back up copy of Windows that was backed up with the partitions of the original hard drive except restoring to the external hard drive that is 1 TB and use it like you would an internal drive on the same computer it's licensed to. That's basically what I'd want to set up and was trying to find out if it could even be done that way mate. :)

This is the laptop I am working with. I believe it's the same exact one she has if I am not mistaken. 

[https://www.walmart.com/ip/HP-Stream-14-cb013wm-14-HD-Display-Intel-N3060-4GB-RAM-32GB-SDD-Windows-10-Home-S-Mode-Purple/196147287?athcpid=196147287&athpgid=athenaItemPage&athcgid=null&athznid=PWVUB&athieid=v0&athstid=CS004&athguid=0af033ad-d1c-170d04ea40bea9&athancid=null&athena=true](https://www.walmart.com/ip/HP-Stream-14-cb013wm-14-HD-Display-Intel-N3060-4GB-RAM-32GB-SDD-Windows-10-Home-S-Mode-Purple/196147287?athcpid=196147287&athpgid=athenaItemPage&athcgid=null&athznid=PWVUB&athieid=v0&athstid=CS004&athguid=0af033ad-d1c-170d04ea40bea9&athancid=null&athena=true)

> **oldfred said:**
> I would backup everything. And reinstall to external drive & restore from backups.
Then you can install Windows to internal drive.
Just be sure to install in same boot mode, probably UEFI as all new Windows systems are UEFI by default.
But when you install, it is how you boot install media UEFI or BIOS on how it installs.

With Ubuntu on external drive better to have an ESP - efi system partition on external drive.
Ubuntu's Ubiquity only installs grub to internal drive's ESP. But you can use Boot-Repair or manually reinstall grub to external drive. Otherwise if you disconnect external drive, grub on internal drive will have to have external drive connected.

The problem is if I restore Windows to the main drive she'll be back to square one and have no hard drive space again. I was basically wondering if I could treat the external drive as if it were an internal one and grub give her the option to swap between either. So just so I am clear your saying you don't think that will work? Thanks for the help mate. I appreciate it. :)

---

### Post by ubfan1 on 2020-03-12
You could put grub and Ubuntu on the external drive, put that drive first in boot order, and let grub choose Ubuntu or Windows.  That will work, but may be slow depending upon the connection to the external disk (USB2, USB3, eSATA, etc)

---

### Post by oldfred on 2020-03-12
I think only if you have an eSATA  connection or SATA connection will Windows let you install to a drive.
USB ports are not allowed for Windows installs.

---

### Post by TheFu on 2020-03-12
Can the internal drive not be upgraded?  Saw a 480GB SSD deal yesterday for $50.  Not all cheap systems allow internal disk upgrades, but many do.  I've upgraded two chromebooks from 16G for 128GB SSDs and my current laptop was up/down-graded from a 1TB spinning disk to a 512GB SSD.

---

### Post by u666sa on 2020-03-13
30gb is old tech. Old laptop then? Windows 10 is questinable. 

My advice is
A. Either new hd 700gb
B. Buy another used laptop


I don’t have a wife, thanks god. But I have two laptops, performance thinkpad w520 which I dedicate to windows 10 and old acer which tripple boots xp, 7 and linux.

---

### Post by him610 on 2020-03-13
Microsoft, together with several manufacturers, marketed these 30GB laptops with Win10 at a low price to compete with Chromebooks a couple of years ago. Just a few months ago, I read the small 30GB HDDs were not large enough to accommodate some Win10 updates. Go figure. How's that for engineering!
Personally, I think dual-booting on such a constrained laptop is ill advised.

---

### Post by silentstone on 2020-03-13
Clarify, are you moving the external hard drive into the laptop? 

Do you have any install media for Windows 10?

---

