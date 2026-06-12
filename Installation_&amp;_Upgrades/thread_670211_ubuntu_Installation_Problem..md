---
title: "ubuntu Installation Problem."
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by push_harder on 2008-01-17
Hi, i'm new to Linux, i'm not a dedicated Windows loyalist.
I downloaded an ISO of ubuntu 32bit and i burned the image onto a CD at a slow speed.

I insert the CD and reboot, the boot menu of ubuntu shows up and askes me what i'd like to do.

I chose the first one which seemed the most obvious choice.
Then the CD kicks in at full speed and takes about 10 minutes of nothing but a cream screan and a mouse pointer which lags before i see a nice looking background and two icons.

One icon is Examples and the other is Install.
I sound like a newb here, and i am.
But i just thought i'd ask what to do from here on, before i go and make a mistake.

I currently have windows server 2000 on the laptop running 3.06Ghz P4 with HT and 512M RAM

Also looking to completly remove the old OS and just run ubuntu with Beryl.

Why Beryl? because it looks cool with the Cube view.

Any help will be greatly appreciated.

Cheers, Matt

---

### Post by c0met on 2008-01-17
Hi Matt,

It shouldn't take 10 mins to get to the installation window. I hope that that is not a sign of potential problems. In view that problems might happen, I suggest that you put Ubuntu onto a partition of your hard drive and test it out before you decide to remove your previous operating system. 

If you don't have your hard drive partitioned, the Ubuntu Live CD has a Partition Editor under [COLOR="Purple"]**System >> Adminstration**[/COLOR] (on the top tool bar). Before you do any partitioning, though, you need to defrag your Windows drive.

---

### Post by erginemr on 2008-01-17
Hello Matt & Welcome to Ubuntu,

To begin with, you should read the following graphical installation guide thoroughly:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by erginemr on 2008-01-17
And my humble avdices to you meanwhile are:

- Be extra careful not to overwrite to your Vista partition. It is very easy to be duped by the Ubuntu installer letting it decide on how to partition the hard drives, wiping Windows altogether, resulting in the end with a Linux only system. And there are quite a few sad stories in the forum on this subject. Once you get past the partitioning part, the rest of the installation is piece of cake.

- Before the actual installation, make sure that all your major and peripheral hardware are recognized in Ubuntu Live CD.

- Avoid making radical decisions at this stage. Do not wipe your Windows, let Ubuntu installer work in dual boot mode. Dual boot for some time, all the while learning the ins and outs of your shiny Linux system. Many things can happen, Linux might not work with some of your essential hardware, you might not like it (although I am sure you will love it) and maight want to go back to Windows, you may want to play Windows only games or run Windows only commercial software. So, I would suggest you to have patience and dual boot for some time.

EDIT:

- Due to the Free Software philosophy of Ubuntu Linux, you will not have Flash web pages, mp3 and DVD movie playback support out 
of the box. Do not bother this. It is very easy to add them later on. There are easy to follow guides on the net. Or ask here and we shall do our best to guide you on this.

- Make sure that your network/internet works from within Live CD. Ubuntu without Internet is like a tree without leaves.

- Linux goes along well with NVIDIA cards but is known to have some issues with ATI graphics cards. So, if you have an ATI card, make sure that it will work (Google and Ubuntu Forum search is your friend). Otherwise, you will not be able to use those fancy desktop effects.

---

### Post by push_harder on 2008-01-17
Thanks guys, great to have such a quick reply!
Just to let you know, i just realised i only have 256M RAM, i take it this is too little?

I could install on my other laptop running vista with 512M RAM, 1.73Ghz Celeron.

Would this be okay?

The other laptop i tried it on is a Toshiba A60, Anchant machine.
I'll give it a crack on the Acer

---

### Post by push_harder on 2008-01-17
I use WiFi on the Acer, the device is a Broadcom 802.11b/g
And seeing as it's Acer, seeing as their so commercialised, will it be hard to find drivers for Extensa 5220?

After posting this, i'll have a look around for drivers.

Cheers guys for the help

Matt (16 year old newbie to the wonderful looking linux)

---

### Post by erginemr on 2008-01-17
> I could install on my other laptop running vista with 512M RAM, 1.73Ghz Celeron.
Sure thing. You are good to go.

For your low end systems, you may consider installing Xubuntu:
[http://www.xubuntu.com/tour](http://www.xubuntu.com/tour)

which performs much better with less memory.

Have Fun!

---

### Post by push_harder on 2008-01-18
All done, i'm typeing from ubuntu right now.
But i'm useing the wired connection due to Broadcom not being greatly supported due to legal reasons.

I did find a few tutorials, but they have failed.
Well, i'm finding ubuntu very fun to use.

Cheers, Matt

---

### Post by push_harder on 2008-01-18
Finally got WiFi working.

But Beryl doesn't want to work.
I've searched endlessly about the issue and found one site that explains why.
Just about a bug issue that can be fixed, but it doesn't say how.

It's an intel Graphics chipset.

Any help would be greatly appreciated.

cheers

---

