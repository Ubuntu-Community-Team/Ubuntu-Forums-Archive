---
title: "Which Laptop for EASY Dual-Booting of ANY Linux Distro and Win7?"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by Phugoid on 2013-03-26
Hello :).

So, I just got a full refund on a HP Pavilion g6 2213sa laptop that I bought a few weeks ago. It came with Windows 8 and this horrible new UEFI/EFI bull and it just would not behave when I wanted to install Linux of any kind.

So, now I'm on the hunt for a new laptop, and I want to be extremely sure before I buy that, this time, the laptop I get will be just as easy to Dual boot as all the other laptops I've owned previously.

Obviously in places like PC World I can't trust any of the salesmen there to give me the correct answer, and obviously they would never actually demonstrate to me that Linux and Windows can behave and co-exist nicely on their systems. So I guess the only place I can trust an opinion of what laptops are suitable for dual booting is here in Linux forums.

Anyway, I'm an Engineering doctoral student so I do a lot of simulation/programming work, and I'm also a bit of a musician and have a home studio - so that's the things I'll mainly be using the computer for, as well as the usual browsing/e-mail/etc. So for that reason I need a computer with a lot of RAM (say min 6GB), a quality powerhouse CPU (say minimum of an i5 or equivalent) and a decent sized hard-drive (min 500GB).

It needs to have wireless (standard), some USB ports (at least one 3.0 USB port!), HDMI port, CD optical drive with cd/dvd rewriter capabilities, SD card reader, etc.

A decent graphics card would be nice but not essential, and a decent soundcard would be nice but not essential (I have external audio cards for recording in my home studio, so not a lot of that needs to take place on board the computer, just as long as it has the RAM and processing capabilities to handle multi-track recordings in a digital audio workstation).

My range is £400-600, although willing to go a bit higher to be guaranteed quality.

Any responses welcome and appreciated!

---

### Post by ahallubuntu on 2013-03-26
~

---

### Post by Phugoid on 2013-03-26
> **ahallubuntu said:**
> UEFI is not going away.  You can buy an older laptop without it (with Windows 7) but in the future you're going to have to deal with UEFI to install Linux.  Just about any Windows 7-compatible laptop not designed for Windows 8 should be fine.  I've never had any issues dual boot installing on any older hardware that I can recall.

How much research did you do about installing Linux on that HP?  The Linux Foundation has created a bootloader that is supposed to work, plus the newest versions of Ubuntu should too.  Granted, I haven't tried myself, and HP wouldn't be my choice for a laptop anyway...

I did a lot of research. I spent 3 weeks solid with the thing just trying to get it to dual-boot. I tried it with Mint, OpenSUSE, Fedora and Ubuntu.

I had the most success with Ubuntu because it let me install it and I could access ubuntu by hitting F9 and selecting the grub loader as a boot device, but I had to do that EVERY TIME, and the BIOS that was available on the machine would not let me permanently change the boot device to that.

I'm aware that UEFI is something I'll probably have to accept, but I'd at least like a machine with a nice BIOS with lots of options so that I can decide what to boot, what order to boot it, when to boot it, and have it all work that way that I want, and not the way that somebody who is getting a lot of cash from Microsoft wants.

I don't want Windows 8 anyway, it's rubbish, and it doesn't do anything that I can't get from Windows 7 for the limited amount that I need to use it. 

Anyway, any suggestions about which laptop? Anybody have a laptop that meets my requirements that they can recommend and assure me that it'll behave nicely?

---

### Post by tux-gamer on 2013-03-26
You can try Asus X201E (F201E), the bios still have 2 choice, so if you don't want to use UEFI yo can switch to PO.
I use this laptop, triple boot: Kubuntu 12.10, OpenSUSE 12.3 and Windows 8.
I use PO in Bios with grub version 1.
ofcourse you can still using windows 7 with this laptop.

---

### Post by Phugoid on 2013-03-27
> **tux-gamer said:**
> You can try Asus X201E (F201E), the bios still have 2 choice, so if you don't want to use UEFI yo can switch to PO.
I use this laptop, triple boot: Kubuntu 12.10, OpenSUSE 12.3 and Windows 8.
I use PO in Bios with grub version 1.
ofcourse you can still using windows 7 with this laptop.

Hmm... doesn't really match up to the specs I need.

---

### Post by kurt18947 on 2013-03-27
Historically, Thinkpads have been pretty good for linux.  Most hardware "just worked".  I have 2 but they're both Vista/Win7 vintage with conventional BIOSs.  I imagine anything with the capability you need is going to have UEFI and Secure Boot.  Unless you could find a NOS (new old stock) Win7 machine with adequate specs.  Keep an eye on Ebay for a manufactuer refurb with manufacturer's warranty?  .  I suspect/hope the UEFI will become standardized over the next few months and Secure Boot is being challenged in the EU by a Spanish group.  I think now is not a great time to be buying a new laptop but sometimes we just can't be choosy.

---

### Post by Phugoid on 2013-03-27
> **kurt18947 said:**
> Historically, Thinkpads have been pretty good for linux.  Most hardware "just worked".  I have 2 but they're both Vista/Win7 vintage with conventional BIOSs.  I imagine anything with the capability you need is going to have UEFI and Secure Boot.  Unless you could find a NOS (new old stock) Win7 machine with adequate specs.  Keep an eye on Ebay for a manufactuer refurb with manufacturer's warranty?  .  I suspect/hope the UEFI will become standardized over the next few months and Secure Boot is being challenged in the EU by a Spanish group.  I think now is not a great time to be buying a new laptop but sometimes we just can't be choosy.

You're right - it's not a great time to be buying a laptop, I really don't know what to do. I don't know what machines will be up to the job and which won't, and I'd hate to buy something **** and then find out that it gets corrected due to the EU Commission's decision or something.

---

### Post by darkod on 2013-03-27
I guess it's out of the question, but I have to ask: Is a desktop out of the question? You can only hand pick components for a home made desktop, otherwise you are at the mercy of manufacturers which have only Microsoft in their mind.
When I was upgrading my desktop few months back I made sure to read the chosen board manual to make sure it allows to disable UEFI boot. I went with Gigabyte F2A85X-D3H and I'm very happy with it.

A desktop would allow you to install windows and ubuntu in legacy mode and dual boot the good old way.

If you insist on a laptop, I'm afraid you're stuck. UEFI and Secure Boot were only made to make dual booting more difficult, at least for the next few years. I don't think anyone can guarantee you anything unless they happen to use a machine that enters in your specs and price range.

---

### Post by Phugoid on 2013-03-27
> **darkod said:**
> I guess it's out of the question, but I have to ask: Is a desktop out of the question? You can only hand pick components for a home made desktop, otherwise you are at the mercy of manufacturers which have only Microsoft in their mind.
When I was upgrading my desktop few months back I made sure to read the chosen board manual to make sure it allows to disable UEFI boot. I went with Gigabyte F2A85X-D3H and I'm very happy with it.

A desktop would allow you to install windows and ubuntu in legacy mode and dual boot the good old way.

If you insist on a laptop, I'm afraid you're stuck. UEFI and Secure Boot were only made to make dual booting more difficult, at least for the next few years. I don't think anyone can guarantee you anything unless they happen to use a machine that enters in your specs and price range.

I have toyed with the idea of a desktop, but I think it would be inconvenient. I want to use the same machine for my home studio, my work and also for travelling (occasional business trips), so a Laptop really is the ideal solution for me. I did consider buying a desktop for the home studio (that's where I'll be using most of my high-end processing and where I require Windows mostly), and buying an older netbook/laptop just with Linux on it for trips, working, etc. But I'd prefer a laptop.

It'd be easy if they just listed this information about disabling UEFI in the specs :(.

---

### Post by darkod on 2013-03-27
> **Phugoid said:**
> 
It'd be easy if they just listed this information about disabling UEFI in the specs :(.

The problem is not whether they list it or not. Look at HP bios for example. It's very limited, in a way not even a proper bios. It can't match the full bios you get with a motherboard. Dell does the same, other brands too.

And another thing: Your windows will come preinstalled, and they choose how to install it. You don't even get the win8 dvd which could help you reinstall it in legacy mode once you disable uefi. For example, you get your new laptop and disable uefi (lets say the option is there). Then what? Windows can't boot because it was installed in uefi.

Not sure if you can use the restore partition but make it restore in legacy mode, since that partition returns the machine to factory state, and the factory state was uefi mode.

Welcome to having no choice and control for your 600 pounds spent. :)

---

### Post by oldfred on 2013-03-27
Some have gotten UEFI to work, but it varies greatly by Vendor and model. The high end models are often UltraBooks that add in complications of RAID with Intel SRT and dual Video or needing bumblebee. This is not really a Linux issue, but vendors not supporting anything but Windows. And it is so much change that the reverse-engineering required to implement all the new drivers and configurations to work well in Linux is very time consumming. It will be a year or two before Linux really catches up with all the changes.

If you really want a high end system, I also recommend a Desktop and build it your self. You may not save much money, but get better components.

I find my laptop not very ergonomic and have issues when using it for longer periods when I travel. And I set it up identically to desktop and just use rsync to copy all data to it when I leave and copy all data back when I return. Some use a new fangled thing called the cloud to do the same, but I do not fully trust clouds.

---

### Post by Phugoid on 2013-03-27
> **darkod said:**
> The problem is not whether they list it or not. Look at HP bios for example. It's very limited, in a way not even a proper bios. It can't match the full bios you get with a motherboard. Dell does the same, other brands too.

And another thing: Your windows will come preinstalled, and they choose how to install it. You don't even get the win8 dvd which could help you reinstall it in legacy mode once you disable uefi. For example, you get your new laptop and disable uefi (lets say the option is there). Then what? Windows can't boot because it was installed in uefi.

Not sure if you can use the restore partition but make it restore in legacy mode, since that partition returns the machine to factory state, and the factory state was uefi mode.

Welcome to having no choice and control for your 600 pounds spent. :)

Indeed - like I said, it was a HP I just did battle with for 3 weeks before returning it. It came with Win 8 installed in UEFI mode, and I actually went to the bother of buying a Win 8 DVD to clean install it the way I wanted - only to find that Win 8 doesn't install at all in legacy mode and that if I want to have Win 8 and Linux, then they must both be in UEFI mode - which then enters me into the problems of dual booting in UEFI mode with an EXTREMELY limited BIOS menu that wouldn't give me any flexibility at all.

Most likely I'll have to do the same when I get a new Win 7 machine - i.e. pay for the machine and the licence that comes with it, and then go out and buy a new Win 7 CD just so I can do a clean install in BIOS mode.

Why are there no hardware peeps out there willing to provide a solution for us open-sourcers? Why can't you just buy a laptop without an OS, get full details on what you're buying before you buy it, and then acquire the OS that you want and configure it how you want? Surely there's money to be made by making hardware for this market? Okay, maybe not as much money as if you sell your soul to Microsoft and have them pump billions through your pipelines, but at least there'd be no competition and you'd have a guaranteed consumer-base!

The computing market really is going to the dogs.

---

### Post by Redalien0304 on 2013-03-27
Have Looked at System76 laptops with Ubuntu Preinstalled. No Windows 7 but you easilly add that if want to?
[https://www.system76.com/laptops/](https://www.system76.com/laptops/)

---

### Post by oldfred on 2013-03-27
Most Windows 7 systems were in BIOS/MBR mode even with those that had UEFI capable BIOS. Only a few of the last one's made had Windows 7 in UEFI mode. And because those did not have secure boot often installed without much effort. Again we saw a few UltraBook Windows 7 systems with UEFI and those had all the other RAID & Video issues except the secure boot issues.

I liked the one poster who said he buys a moderately high end system, but without SSD. Removes hard drive with Windows and installs new SSD with Ubuntu. Only puts original hard drive back in when he decides to sell system.

---

### Post by darkod on 2013-03-27
Yeah, but swapping the disk still doesn't solve the issue that you have to buy a new win7 license to install it. On top of one license already paid, since most laptops don't ship OS free.

And I don't agree with the desktop cost, high end components will not be more expensive (maybe even cheaper) compared to high end laptop. Of course, the laptop has the mobility, you pay for that. EDIT: I double checked, Fred said you might not save much money, not that the desktop will cost you much more. I read it wrong in a hurry the first time. :)

But your desktop CPU will have so much more processing power, not to mention easy future upgrades, etc. But now we are starting a new thread. :)

---

### Post by Phugoid on 2013-03-27
> **oldfred said:**
> Most Windows 7 systems were in BIOS/MBR mode even with those that had UEFI capable BIOS. Only a few of the last one's made had Windows 7 in UEFI mode. And because those did not have secure boot often installed without much effort. Again we saw a few UltraBook Windows 7 systems with UEFI and those had all the other RAID & Video issues except the secure boot issues.

I liked the one poster who said he buys a moderately high end system, but without SSD. Removes hard drive with Windows and installs new SSD with Ubuntu. Only puts original hard drive back in when he decides to sell system.

So you're fairly confident that MOST (not all) Laptops that ship with Win 7 will not have it installed in UEFI mode and will not pose any major issues in dual-booting?

---

### Post by Phugoid on 2013-03-27
> **alien0304 said:**
> Have Looked at System76 laptops with Ubuntu Preinstalled. No Windows 7 but you easilly add that if want to?
[https://www.system76.com/laptops/](https://www.system76.com/laptops/)

Those systems look PERFECT... although I'm in the UK and have some reservations about getting such a fragile and expensive piece of equipment shipped such a long way!

Plus they have the option to configure it with a UK keyboard, but not with a UK power plug :|.

---

### Post by Redalien0304 on 2013-03-27
True i understand that getting it  over UK. They might have UK plug as an Accessories option? Id e-mail system76 & ask yer Questions away. they have always answered my questions the same day. I am Considering buying a laptop from system76 in the future for myself. of course im in the US.

---

### Post by oldfred on 2013-03-27
If you can find a Windows 7 system, you should be able to get discounts as all new systems are Windows 8. I would avoid the UltraBooks, as they are the high end systems, but have the RAID & Video issues. 

Many want the dual video for power savings with Intel internal video and performance with nVidia. Many have installed bumblebee, but I have no experience with that.

---

### Post by darkod on 2013-03-27
> **Phugoid said:**
> Those systems look PERFECT... although I'm in the UK and have some reservations about getting such a fragile and expensive piece of equipment shipped such a long way!

Plus they have the option to configure it with a UK keyboard, but not with a UK power plug :|.

Don't forget that they might charge you customs and VAT, the product is coming from outside the EU. Not sure if the USA shop can sell it to you tax-free though, that might compensate for any charges paid in the UK.

---

### Post by Phugoid on 2013-03-27
> **alien0304 said:**
> True i understand that getting it  over UK. They might have UK plug as an Accessories option? Id e-mail system76 & ask yer Questions away. they have always answered my questions the same day. I am Considering buying a laptop from system76 in the future for myself. of course im in the US.

They responded already and said:

A) Don't don't provide a UK plug, but they any power lead with a Mickey-Mouse shaped end will fit into the Brick end of their adaptor, so that's not a problem!
B) They use a traditional BIOS, not UEFI
C) They see no reason why I couldn't install Windows 7 on the system in dual-boot and they provide instructions to do so.

Sounds perfect for what I'm after, and the laptops are relatively cheap for a very good specification!

I might just buy one - of course, will need to investigate the Customs/VAT issues in hopes that they don't significantly up the price. I do hate tax...

---

### Post by Phugoid on 2013-03-27
Coming out quite expensive though... talking close to £1,000 once you factor in VAT + Customs... considering that my original budget was somewhere between £400 and £600... not sure if I'm ready to spend quite so much!

---

### Post by Redalien0304 on 2013-03-27
Ouch man  
1000 British Pound Sterling equals
1512.70 US Dollar

---

### Post by tux-gamer on 2013-03-28
> **Phugoid said:**
> Hmm... doesn't really match up to the specs I need.

ow, you can try look in Asus Website, there is alot of them pre installed with Ubuntu, and still offer alternatif boot if not compatible with UEFI/EFI.

---

### Post by Phugoid on 2013-03-28
Okay, I went for it and bought one.

Got a Pangolin Performance with an i7, 8GB RAM and 500GB HD. Cost me $1,000 with postage which is about £650, but then I'll have to pay VAT at 20% once it gets here, most likely, so probably looking at £800 - £850 in total. It's double the budget I originally planned for my Laptop, but all the reviews for these laptops have been nothing but praise - apart from some quibbles about the battery life, but I tend to run the best of batteries into the ground anyway!

So it seems to be worth the money, plus it's far better specs than I was getting in the £400-500 range, and I'm just delighted that it's configured for Linux and will dual boot Windows without this EFI/UEFI nonsense. 

It'll at least last me a good few years, and in the mean-time, the vendors can stabilise and sort out this UEFI nonsense and get it agreeing with Ubuntu. And hopefully Microsoft will also be sued for millions in the meantime... twats!.

---

