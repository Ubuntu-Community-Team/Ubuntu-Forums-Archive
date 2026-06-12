---
title: "Persistent Gutsy on USB flash drive?"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by kombucha on 2007-08-11
I have begun looking into installing Ubuntu (or, preferably, Kubuntu and Xubuntu) onto a flash drive. I understand that Feisty is bugged such that persistence requires some effort, and I'm wondering if this bug has been fixed by Gutsy Tribe 4? If so, is it rather easy to install Gutsy to a flash drive?

Do you think a 2GB drive would be sufficient for this purpose (perhaps even with KDE and XFCE both installed) or should I spring for a 4GB?

Finally, I'd assume you still need a Linux-friendly filesystem on the flash drive... but I want this flash drive to double as storage for Windows computers. Do I just have to (if I even can) partition the flash drive into, say ext-3 and ntfs? I don't want to have to configure each Windows computer I use it with to read/write to the Linux partition. Any ideas?

Thanks for the advice!

---

### Post by ddrichardson on 2007-08-12
Personally Iwouldn't use Ubuntu on a flash drive, due to the fact that it isn't designed to run from flash memory. Flash has a limited (albeit fairly high) number of write cycles, which with swapping etc will get used up.

I have [Damn Small Linux]("http://www.damnsmalllinux.org/") installed on a 2 Gb flash drive partitioned into a ext2 and a fat32 for Windows files. This has the frugal install option which minimises disk usage and loads the OS into RAM so is very quick and very customizeable. There are other distros that are aimed at USB drives - Mandriva does one (not free) and so does Feather Linux.

I like Ubuntu and use it a lot but its horses for courses.

---

### Post by kombucha on 2007-08-12
Oh, right right right. I read all about that, and I guess I either forgot about it or didn't think it was an issue with Ubuntu since in my mind it was going to be a combination of a Live-CD running in RAM and a persistent OS. I guess that isn't the case, huh. Well, time to start seeking out a new distro - DSL looked pretty good :)

---

### Post by kombucha on 2007-08-12
I have a semi-related question:
Is it a bad idea to install Compiz Fusion on a USB distro? I'm just thinking that it might seriously bog down performance while running off of the USB drive, plus it'll be very screwy switching graphics cards all the time. Any thoughts?

---

### Post by ddrichardson on 2007-08-12
Most USB based distros load everything into RAM so performance mightn't be an issue. But the graphic card switching on multiple machines could be a pain. DSL should be able to do Fusion with some tweaking because Xorg can be installed rather than xvesa.

---

### Post by kombucha on 2007-08-12
A few more questions...

Now, according to [http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB) , the distros we've been discussing thus far  ("Live-CD Derived") aren't persistent by default - you likely need to use a code to save changes. True or false?

And then I find something like this: [http://ubuntuforums.org/showpost.php?p=1062799&postcount=100](http://ubuntuforums.org/showpost.php?p=1062799&postcount=100) or this: [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)
You're saying that's a bad idea, because it'll wear out the drive?

It just seems like if it's running from RAM, how is it automatically going to save my changes to the OS?

I guess I'm just getting more and more confused about this whole process.

Thanks for the help!

---

### Post by ddrichardson on 2007-08-13
DSL has an option to install persistantly to USB.

OS's always run from RAM, infact everything does, the good old fetch/execute cycle. The difference is that DSL creates a RAM drive and stores the OS there. Some live-cd distros do this to free up the CD drive for example.

I read through the post about creating an Ubuntu USB disk - all its doing is making the drive bootable then copying the OS across. There are no modifications being made to the way the system operates to modify it for USB.

It depends on the flash drive but yes it will eventually cause problems, if you don't minimize the amount of times it's accessed. You have to bear in mind these devices were not intended to be the main system secondary storage.

The best solution with Ubuntu would be to make your own LiveCD that mounts a USB disk to store certain settings - /home obviously but maybe, say /var, /etc and /opt for installing additional programs later.

---

### Post by kombucha on 2007-08-13
Heh - that sounds a bit beyond my skill bank.

If anyone knows Slax or Wolvix, can you tell me if their USB options are just as valid as DSL's? I'm liking them a bit more, and they sound like they are meant for persistent-USB usage, but I can't be sure.

[http://www.slax.org/](http://www.slax.org/)

[http://wiki.wolvix.org/USBFlashDriveInstall](http://wiki.wolvix.org/USBFlashDriveInstall)

Thanks always.

---

### Post by ddrichardson on 2007-08-13
Slax is quite good - try [My Slax]("http://myslax.bonsonno.org/download.php") from Windows if you want to create your own version with different support. It has an option to install to USB after creating the new ISO

---

### Post by kombucha on 2007-08-13
I'll try that right now. :)

---

### Post by kombucha on 2007-08-13
Well, MySlax didn't work for me at all (it wouldn't recognize Slax 6R6 or Wolvix 1.1.0) so I went with live-booting Wolvix and using its built-in USB installer.

And, of course, my computer won't boot from USB. Bummer, but I'm about to get my new computer, so it doesn't matter all that much, except I guess I can't configure it until then.

Wolvix recommended using a combination floppy/USB boot method, which I might try just for now, although clearly it's mega-inconvenient.

---

### Post by kombucha on 2007-08-13
Actually... I had assumed a USB drive qualified as "Removable media", not a hard drive. So in fact I did find the option to boot from the drive in my BIOS, but I still couldn't get it to work. I tried installing to the drive twice, one with the "slow boot" toggle enabled which is supposed to cure common problems, and both times my computer just flashes a single white dash without booting (although I didn't wait too long... but it didn't seem to be doing anything.)

I guess I can try DSL tomorrow just for testing purposes - any other suggestions? If my drive was fully recognized in my BIOS, does that mean I should be able to boot from the flash drive?

:)

---

### Post by kombucha on 2007-08-14
Beautiful... Slax worked perfectly with [this guide]("http://www.shorttext.com/215t") and now I'm trying Wolvix manually with [this]("http://wiki.wolvix.org/USBFlashDriveInstall").

Except... is it doing what we want it to do? Not wearing out the USB drive very rapidly?

And I need to nail down persistence... :)

---

### Post by kombucha on 2007-08-14
Wolvix is decent but its persistence is very much lacking... I have to redo my xorg.conf, resolution, network settings, etc. every time it loads. That's no good.

But if syslinux is essentially just loading these as live CDs, why wouldn't loading the Ubuntu live CD be the same?

:)

---

### Post by Stretch 4x4 on 2007-08-14
Hi

I'm not really sure why there are not better solutions for usb distros yet. One solution to the ubuntu option may be to get a small hard drive based usb drive or maybe even a hard drive based mp3 player, although you need to be careful of magnetic things they are less likely to wear out based on the number of read writes. I did get ubuntu working for a bit on an external hard drive. I had three partitions, a 700mb fat for the iso contents, a ext2 partition for the persistance and another fat one for windows and storing general things. One problem I had was the screen resolution was not always picked up properly when I changed computers, apart from that I got quite close, it was mostly just a lack of time which has stopped me doing it properly.

If you have any success let us know because it is a great idea.

---

### Post by kombucha on 2007-08-14
That sounds like a really interesting idea, something to keep in mind. But I literally bought this flash drive yesterday mostly for this purpose, and I mean to make the most fun of it :D

Anyways, my prayers have been answered.

After bailing on Wolvix, I decided to look at my options in-depth one more time and try a new one. So I decided on Puppy Linux.



This distro is BRILLIANT.

First off, it is easily the most friendly, understandable distro I've seen. The installation process speaks in such simple, clear English and really makes sure you know what's going on each step of the way. It tells you why choices are default, why some are recommended... it's simply wonderful.

Next, it loads and runs faster than any distro I've tried, whether from the CD or USB. Now, it runs fast because it's loaded to RAM, but it boots faster than even my freshly-installed HD-based Xubuntu. I don't understand it.

Then, there are absolutely loads of programs pre-installed, ones that most people have never heard of and will never use... but for the ones aimed at the general population, there are generic names and gorgeous icons assigned to each. SeaMonkey (the default browser) is simply a nice, blue-icey globe on the desktop that says "Browse". And so forth.

There's no login to worry about... it takes you straight to the desktop from when you turn your computer on. And on the first run, it actually found all of my available resolutions, unlike 99% of other distros.

Also, the focus is 100% on persistence. There is a big "SAVE" button right on the desktop which commits changes (ALL CHANGES) to RAM, or you can have it do it automatically, or at shutdown. No tricky configuration or anything... I just booted up the live CD, used the universal installer for my flash drive, and it was already persistent.

Finally, adding programs is remarkably simple. Puppy has its own package system like most others... you can use the manager to browse available programs, download and single-click install, or with some larger sets (like OpenOffice) you just save a single file to /mnt/home and it'll load every time Puppy starts, including desktop icons and configuration settings.

Truly, I'm more blown away by this distro than any other I've encountered. It does start off a bit ugly, but I've seen some amazing screenshots, so clearly that is remediable.

Anyone looking for a solid flash or Live-CD distro, I can easily say this is leagues and leagues above the rest, really everything I could have asked for. :)

Thanks for all the help! Hopefully others can benefit as well.

---

### Post by The Gladiator on 2007-08-15
Before going ahead with Puppy please have a look to MCNLive ( [http://www.mcnlive.org](http://www.mcnlive.org) ). It's based on Mandriva, focused to run from an USB pen, it has a fantastic support (forum) and it's FREE. 

Waiting for something similar based on Ubuntu

---

