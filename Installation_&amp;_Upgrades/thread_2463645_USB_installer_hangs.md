---
title: "USB installer hangs"
date: 2021-06-15
forum: Installation &amp; Upgrades
---

### Post by Slownis on 2021-06-15
I'm attempting to revive a 10 year old mini ITX motherboard and make a small form factor ubuntu server.  I'm not sure my disc burner works anymore and I don't have any blank disk media, so I'd like to install ubuntu using a USB drive.

I have created a USB Ubuntu server installer using ubuntu's startup disk creater on my ubuntu laptop running 21.10, as well as in windows 10 with Rufus using various options (grub, dos, dd, etc).

It works and boots into the installer when I use it in a 5 year old compaq laptop.

When I try it in the ZOTAC motherboard, it will attempt to boot from the USB, but immediately hangs after the words 'ISOLINUX 6.04 20191223 EHDD Copyright (C) 1994-2015 H. Peter Anvin et al' are displayed at the top of the monitor.  I get a flashing cursor underneath and nothing else.

Motherboard: Zotac H55itx-c-e  [https://www.zotacusa.com/downloads/man/pa146.pdf](https://www.zotacusa.com/downloads/man/pa146.pdf)
CPU:  Intel Core i7 875 K
video card:  [https://www.newegg.com/sapphire-radeon-hd-5570-100293l/p/N82E16814102874](https://www.newegg.com/sapphire-radeon-hd-5570-100293l/p/N82E16814102874)

---

### Post by GhX6GZMB on 2021-06-15
Are you sure it's hanging and not just having a slow USB interface? I've had installations using up to 10 min. at that point.

---

### Post by sudodus on 2021-06-15
The specs indicate that The ZOTAC mobo should work with 64-bit systems, but maybe you will have better luck with a 32-bit system. At least you can try that. There are current Debian 32-bit systems (but all the current Ubuntu systems are 64-bit).

See also this link: [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by MAFoElffen on 2021-06-15
> **sudodus said:**
> The specs indicate that The ZOTAC mobo...
The USB on that board is USB 3.0... Processors supported were i3 through 17, 1st Generation... Verified to run Linux (then) but...

On an 11 year old board, ensure your BIOS and Chipsets have the latest firmware updates. It looks like Zotac had some... [https://www.zotac.com/mu/files/download/mainboards?driver_type=All&mainboards_series=All&mainboards_os=All&sku=H55itx-c-e&page=3](https://www.zotac.com/mu/files/download/mainboards?driver_type=All&mainboards_series=All&mainboards_os=All&sku=H55itx-c-e&page=3) 

It says it was tested on Linux... but that was before any 3.x kernels. It doesn't seem to have any special chipsets that were out of the ordinary, but they did have some updates to their firmware.

---

### Post by Slownis on 2021-06-16
Yes, I'm sure.

---

### Post by Slownis on 2021-06-16
this board has been sitting in my closet for several years.  In order to upgrade firmware I'll have to jump through many hoops, like installing windows.  Anything easier I can try first?

---

### Post by guiverc on 2021-06-16
Are you sure you're waiting long enough?

For example 21.04 & *impish* ISOs can take longer than 10 minutes to boot on some devices...

Refer [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342)

Nothing is shown for that time (8-12 minutes on most) except a blinking cursor..  (11 mins 17 secs is listed on report 1929029).

The same media boots normally on most boxes though... it's firmware specific.

---

### Post by MAFoElffen on 2021-06-16
> **Slownis said:**
> this board has been sitting in my closet for several years.  In order to upgrade firmware I'll have to jump through many hoops, like installing windows.  Anything easier I can try first?
What you do to make this motherboard to do anything is personal and up to you. Anything you do with it.

Zotac has many flavors of Windows, Dos and Linux BIOS update installers there on their site. That in itself is impressive to me. That they even tested and certified that board to run Linux impresses me. That is so much more than most motherboard manufacturers. Especially when you take into consideration that they did that "11 years ago", when Linux was not as popular in marketing hardware!  I think it's going to be well  worth your while to upgrade the BIOS first, to save yourself lot's of time and head aches , trying to chase potential problems down, that could be resolved by just doing that first. 

Especially with that being a common issue with older hardware and modern kernels, when a modern flavor of Linux does not want to boot, right off. You could do that from a persistent, USB LiveCD Image created with Rufus. Where you could also do, testing from, to see if you can run the version you want, and what you have to do to run that, before installing that. The same could be said for creating an old Live Boot image on anther USB key, for DOS, or even Windows XP or newer. There are many rescue disks images that will boot, then would allow you to do that. A good self-booting USB Linux LiveCD persistent image is an invaluable tool. (Even for diagnosing and fixing Windows machines.)

As for testing with a persistent Linux LiveCD image, read the first 3 posts of my Graphics Resolution sticky in my signature line. Besides being about graphics, it has a lot about diagnosing general Linux boot problems. If you booted temporarily into a text console, with a splash quiet  kernel boot option (included), just that process is going to tell you allot about what is going to happen and if you can run a modern kernel on your hardware. Then do the same with safe graphics. Then do the same with a full graphics layer desktop. All that is going to tell you if you need any special options for your acpi, and or graphics.

I'm not really saying that you "require" any of that. But right now you say you can't boot any standard image on that board. Which hardware wise, it should. I don't see anything on that board, that is hitting me in the face, that I see would prevent that. Everything there, seems fairly standard.

Up through 4 years ago, I volunteered for years to a non-profit computer recycler. That board would have been a premium candidate to get resurrected as a higher end system for resale (to them), running Linux. So, yes, it should work well. A first Gen iCore, is not a screamer by todays Gaming System standards. But it was when it came out 11 years ago. I do remember they had ACPI issues and were very, very picky about the memory you used with them. If I had been triaging this board, and assessing the system build, firmware updates where the first thing we did. Recently, seeing people with problems booting or running modern Linux distro's, this seems to be a common issue (again), that most people today, don't even think about. 

Just saying it is an idea. It may not be "your" specific problem. But it couldn't hurt, and it checks that off your list. Right?

*** You didn't mention any graphics option that you are using on that board, which it say's had no integrated GPU, so that is still something no one has asked you yet... right? I could be wrong. I just don't remember, and honestly, didn't notice. That is the next to work through. What you are using for video also affects having challenges to booting (sometimes).

---

### Post by Slownis on 2021-06-16
> **guiverc said:**
> Are you sure you're waiting long enough?

For example 21.04 & *impish* ISOs can take longer than 10 minutes to boot on some devices...

Refer [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342)

Nothing is shown for that time (8-12 minutes on most) except a blinking cursor..  (11 mins 17 secs is listed on report 1929029).

The same media boots normally on most boxes though... it's firmware specific.

I let it sit overnight.  Still hung.

---

### Post by Slownis on 2021-06-16
> **MAFoElffen said:**
> 

*** You didn't mention any graphics option that you are using on that board, which it say's had no integrated GPU, so that is still something no one has asked you yet... right? I could be wrong. I just don't remember, and honestly, didn't notice. That is the next to work through. What you are using for video also affects having challenges to booting (sometimes).

You are correct, my processor has no integrated graphics.  My graphics card is linked in the original post **[FONT=&amp]SAPPHIRE Radeon HD 5570 1GB DDR3 PCI Express 2.1 x16 Low Profile Ready Video Card 100293L [/FONT]**.  I'm connecting it to an older viewsonic monitor via D-SUB.  I also have a D-SUB to HDMI converter I could try if you think that could help and connect it to a newer monitor.

Just to be clear, I'm attempting to install UBUNTU server, not UBUNTU desktop - seems the installer is text based so I feel like (maybe erroneously) that graphics shouldn't be an issue.

---

### Post by Slownis on 2021-06-16
Memory and CPU are the top of the line tested options from Samsung / Intel according to this link on the ZOTAC support page:  [http://downloads.zotac.com/mediadrivers/mb/cpu/a146.txt](http://downloads.zotac.com/mediadrivers/mb/cpu/a146.txt)

At the time I originally built this PC as set top box, I wanted top of the line and spent way too much.  The thing booted win 7 in seconds, and had NO lag.  Still should be viable even by today's standards.  I had another MSI system I was using for a server that is a couple years newer, but it seems to have gone bad.  I wanted to try this out before purchasing something new.

I'll look into updating firmware.  I may very well be on the latest firmware already - I tend to recall updating it at least once.  A lot of love went into this machine at the time.

---

### Post by ActionParsnip on 2021-06-16
Did you MD5 test the ISO you downloaded or use Torrents? How did you make the USB stick? What steps / applications / commands did you use?

---

### Post by MAFoElffen on 2021-06-16
On video, a different display/monitor is not going to make any difference. 

No, AMD GPU is good and usually Linux friendly as that goes. If in question, I would try a nomodeset boot option and see if it makes a difference.

@ActionParnsip's post, he already booted this same USB successfully to a 5 year old Laptop... So I suspect that the image may be good good.

BUT, what he did not say, was if that laptop was UEFI (which was well around 5 years ago) or if it was set to Legacy Boot... Which this specific 11 year old board is NOT UEFI. Wqs the key made for MBR or UEFI?

Next, looking back, I see that when this board was new, that this board successfully ran vanilla Ubuntu 10.04 LTS and OSX Snow Leopard 10.4, so I suspect it just needs a few tweaks. 11 years ago, there was some chipset hardware advances that made things a bit challenging. And they weren't always "standardized. But the kernel in Ubuntu LTS 10.04 was before 11.04, where KMS came into the kernel, and things got a bit specific about booting options and hardware. Most of those things have been added to the kernel now.

*** I suspect that ensuring the USB key is MBR boot and add "nomodeset acpi=off" to the kernel boot line to see if that works. If that works, then kept using the nomodeset option, just until you get the video driver installed after reboot.

---

### Post by Slownis on 2021-06-17
I attached an old win10 drive from my dead system and it booted without me having to install.  I got the bios updated and that seems to have done the trick.  I can now get to the Ubuntu server installation.  Thanks guys.

---

### Post by MAFoElffen on 2021-06-17
Good to know that the BIOS upgrade got you going on a current Kernel. Good Luck.

Remember to mark this thread as Solved in the Thread Tools link at the Top Right of the thread so others can find your solution.

---

