---
title: "install issues with old laptop"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by daveb1 on 2008-09-25
Hi All,

I've been struggling for days now trying to install Ubuntu or Xubuntu on an old laptop I have, the intention is to end up with edubuntu installed and let the kids loose.

The laptop is a Sony PCG-F403, 128Meg Ram, Pentium 3 450MHz and a 6 Gig HDD. I believe this is about the minimum specs for an install, but maybe I'm wrong and I've just wasted 3 days!?

Anyway, it currently has a copy of Win98, which I've stripped back to bare minimums.

So far I've tried the following (all with Hardy 804.1)...

1. Ubuntu live CD. Boots from CD, I see the logo, then after a while I get the Heron wallpaper, but then nothing else happens except the CD drive whirs a lot. Tried this several times, once left going for 28 hours before I gave up.

2. Ubuntu, Install from CD... same as above but I only left it for around 6 hours.

3. Xubuntu, exactly the same as 1 and 2 above.

4. Started Win98 then ran Xubuntu CD. Chose the install as an application option. It gets a certain way through, then stalls whilst creating image saying it can't access the CD, retry/cancel. Won't go any further.

5. Tried minimum install CD per instructions [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems") but can't find a specific "Install a command-line system." option. I get options like safe mode and OEM install but not a CLI option.

6. Booted from the minimal install image and got a cli option. It starts loading linux, I can choose keyboard etc, but then it tries to detect a network. The laptop doesn't have an ethernet port, and I was going to use a netgear USB dongle, but of course it hasn't loaded the USB drivers at this point so the network detection fails and it's game over again.

I've tried the Xubuntu CD in a new Dell laptop I have and it ran fine in Live CD mode (non install) so there's nothing wrong with the CD or image.

So am I flogging a dead horse, or have I missed something obvious? I'm an expert with Windows, but newbie with Linux so plain English would be appreciated :)

Thanks

Dave

---

### Post by zvacet on 2008-09-25
As you can see from the link you posted that you need **alternate CD** for install.

---

### Post by oilchangeguy on 2008-09-25
read this from [www.ubuntu.com](www.ubuntu.com) system requirements for xubuntu:
System Requirements 
Xubuntu is available for PC, 64-Bit PC. 

CDs require 128MB RAM to run, or **192MB RAM to install**. Desktop install requires at least 1.5GB of free space on your hard disk.

Minimum system requirements
To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

**Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.**

---

### Post by daveb1 on 2008-09-25
@zvacet - OK, firstly I thought I HAD downloaded an alternate CD to Ubuntu, namely Xubuntu. I also tried the minimal image, the 10 meg one in case that's what was meant.

It was only by fluke that when I went back to the main download page yet again I clicked the Page Down button by mistake and saw the little tickbox to choose the ACTUAL alternate CD. The way my browser was set up, the bottom of the page I could see on my screen was the big green Start Download button.

As a newbie, I think it should be a bit clearer as to what you should do... perhaps the tickbox could be moved above the download button, it would have saved me several days of mucking about!

@oilchangeguy - Thanks for the clarification. Now I've sussed what the alternate CD actually means, it's all got a lot clearer!

---

### Post by oilchangeguy on 2008-09-25
unless you can get more ram for your computer, you'll need to try something like puppy linux, or damn small linux. always locate the system requirements BEFORE you start something. that way there won't be any surprises.

---

### Post by daveb1 on 2008-09-25
Actually, I'm no better off...

Taken from the first para of [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) 

"Installing Ubuntu on any system requires at least 32 MB of memory: : The text-based installer included with the alternate (install) CDs needs that much space to run reliably"

So is it 32Meg or 192 Meg to install from the ubuntu-8.04.1-alternate-i386 CD? Or maybe we're talking about completely different things?

I'm just burning the alternate CD now, so I guess in about 5 minutes I'll find out one way or another...

---

### Post by snowpine on 2008-09-25
> **daveb1 said:**
> Actually, I'm no better off...

Taken from the first para of [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) 

"Installing Ubuntu on any system requires at least 32 MB of memory: : The text-based installer included with the alternate (install) CDs needs that much space to run reliably"

So is it 32Meg or 192 Meg to install from the ubuntu-8.04.1-alternate-i386 CD? Or maybe we're talking about completely different things?

I'm just burning the alternate CD now, so I guess in about 5 minutes I'll find out one way or another...

Hi Dave, ubuntu-8.04.1-alternate-i386 requires 256mb of ram. The link you posted that specifies 32mb minimum must be very outdated. With 128mb of ram I would recommend something like Puppy, SliTaz, DSL, or Fluxbuntu. If you want to use any of the mainstream 'Buntus, you are going to need more ram I'm afraid (I would personally recommend 256mb for Xubuntu and 512mb for Ubuntu; I've never tried Edubuntu). Always a good idea to check the system specs before installing new software. Windows 98 is 10 years old, which is a really long time in the computer industry. :)

---

### Post by robert shearer on 2008-09-25
Have to agree with other posters, your memory is too low to run a desktop with the mainstream 'buntus.The best you could do is a command line  system and that is what some of the "minimum install" specs refer to.Typing in commands and no GUI.

The Puppy linux options should work well on your hardware and I have run both these...
[http://www.puppylinux.org/downloads/puplets/macpup-dingo](http://www.puppylinux.org/downloads/puplets/macpup-dingo)
[http://www.puppylinux.org/](http://www.puppylinux.org/)

on lesser hardware with snappy performance.

---

### Post by daveb1 on 2008-09-26
Thanks all for the replies...

> **snowpine said:**
> Always a good idea to check the system specs before installing new software.

The trouble is, I DID check the system specs, which ended up being contradictory!

From the official Ubuntu documentation page [https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems"), which leads to an updated article on the blueprints.launchpad.net site here [https://blueprints.launchpad.net/ubuntu/+spec/low-memory-install]("https://blueprints.launchpad.net/ubuntu/+spec/low-memory-install")

To be fair, I think I checked them as far as a newbie would be expected to; if the official documentation pages state "Depending on the hardware requirements, you can expect a sparse Ubuntu system to boot to a graphical desktop on anywhere from 19 MB to 54 MB", surely I'm not wrong to assume that 128Meg of RAM will probably work (and be good enough for my kids to use).

That said, I've been in the game long enough to know that real world is different from what the specs say SHOULD happen, so I bow down to your superior knowledge and I've ordered 256Meg of memory.

I've also downloaded puppy as well to have a play, but I'm really hoping I can get Edubuntu going at some point for the kids.

Cheers

---

### Post by robert shearer on 2008-09-26
Yes. I have to agree.
 Having viewed the links you gave it is confusing as to how much memory is needed.
There is no qualitative caveat applied  and it should advise that IF such a system did install then performance would be woefull with apps taking forever to open and lockups being frequent.

On the up side I am glad you are playing with Puppy.As it can be run as a live cd then it is a great opportunity to use while the extra memory you ordered arrives.

Once the Ram is installed, and assuming you still have the Ubuntu install you persevered with, then it should be automatically recognised and the full Ubuntu desktop will run.

---

### Post by daveb1 on 2008-09-29
WEll, a quick update, just in case some other confused person stumbles over this thread...

Firstly, I had to give up with Puppy as I couldn't get any of my wireless dongles to work. Shame as it looked nicely laid out.

I downloaded Xubuntu Alternate CD and ran it using the CLI option. Everything worked fine although it did take nearly 3 hours to finish. I now have a working Xubuntu laptop with wireless internet access.

I then tried installing Edubuntu over the top using the Edubuntu ISO image, but it kept saying some of the files were out of date and wouldn't proceed any further.

Finally I tried installing from the Internet by running ```
sudo apt-get install edbuntu-desktop
```.
This took a further 2 hours, but again seemed to complete successfully. However once I rebooted the dwesktop looked the same... there were some additional apps in the menu, but it wasn't quite what I expected.

I'm going to wait for the extra memory to arrive, and then have another go, so I'll try and report back after that.

Cheers

---

### Post by paceman on 2009-02-23
Hi, 
I stumbled across this thread as I'm considering using my aged Sony F403. 
Could you tell me if you ever got Ubuntu (or variant thereof) running successfully, and how much Ram you ended up needing?
It's only ever going to be used for basic web browsing (Wi-Fi), but needs to have a GUI - so if you found something more suitable for older hardware I'd be pleased to hear about it.

TIA

Jason

---

