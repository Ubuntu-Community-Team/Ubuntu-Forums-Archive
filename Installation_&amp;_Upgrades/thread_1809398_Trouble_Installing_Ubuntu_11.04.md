---
title: "Trouble Installing Ubuntu 11.04"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by Bob Sanchez on 2011-07-21
I'm trying to install Ubuntu 11.04 on a HP Pavilion a1230n desktop. Here are the specs:

Athlon 64 3700+ 2.2 GHz
ATI Radeon XPress 200
Memory Installed	1 GB (2 x 512)
Integrated graphics

The original hard drive broke so I reformatted a notebook hard drive I had laying around and plugged that in. (So I don't have Windows or any other OS on there.)

I downloaded Ubuntu 11.04, verified the download, verified the CD, and used that CD on another computer to make sure it works. When I try to install it on my HP, I get to the page where it says try it, install it, verify disc, etc. but once I press "install," the screen shows a blinking "_" in the top left hand corner and then after a while shows me this.

/sys/devices/pci0000:00/0000:00:14.1/host3/target8:0:1/3:0:1:01block/sr/ (969)
undevd[63]: worker[98]unexpectedly returned with stats0x0100

undevd[63]: worker[98] failed while handling ‘/devices/pci0000:00/0000:00:12.0’

undevd[63] worker [103] unexpectedly returned with status 0x0100

undevd[63]: worker [103] failed while handling ‘/devices/pci0000:00/0000:00:14.1

undevd[63]: worker [68] unexpectedly returned with status 0x0100

undevd[63]: worker [68] failed while hanling ‘/devices/pci0000:00/0000:00:01.0/0000:01:05.0’

undevd[63]: worker [72] unexpectedly returned with status 0x0100

undevd[63]: worker [72] failed while handling ‘/devices/pci0000:00/0000:00:14.4/0000:02:03.0’

undevd[63]: worker [73] unexpectedly returned with status 0x0100

undevd[63]: worker [73] failed while handling ‘/devices/pci0000:00/0000:00:14.4/0000:02:05.0’

I couldn't find much help with google. Any ideas what these errors could mean? 

Help is greatly appreciated.

---

### Post by Volens on 2011-07-21
I'm no expert, so I can't give you that much help, but I'll try.
 
Have you tried just running the live cd?
 
It should work using just the RAM so you can verify that the problem isn't the hard drive ... again.
 
I hate failing hardrives.

---

### Post by Bob Sanchez on 2011-07-21
Thanks for the quick response.

Yeah I have tried the Live CD but it spits out similar errors:(

---

### Post by Volens on 2011-07-21
I'm reluctant to give this suggestion, but try some live CDs for other distros.
 
My laptop sometimes gives me grief when I try openSUSE.
 
Its definitely either:
 
A) Ubuntu's boot procedure fussing about a piece of hardware (in which case another distro's CD **may** work)
 
B) Not just your hardrive broke
 
I hate to say don't use ubuntu and make you go through the process of downloading and burning another .iso, but I've found that sometimes its better to look elsewhere if you can't even get it to boot. As I said, I try out a lot of distros and my laptop tends to be picky with some of them.
 
Thats about as far as my advice can go. Good luck.

---

### Post by Bob Sanchez on 2011-07-21
Ok I'll try some other ones and report back. Any ones in particular you recommend?

---

### Post by Volens on 2011-07-22
Puppy Linux - really small/lightweight, quick download, usually keep it on a bootable usb drive
 
Slitaz - super lightweight, also means its a quick download, I find its lacking sometimes in terms of basic graphics support
 
Crunchbang - slimmed down Debian/Ubuntu distro, uses same package system, uses openbox as a window manager
 
openSUSE - full featurd distro, has a decent KDE version
 
Linux Mint - a Ubuntu based distro with some differences in presentation, this may just give you the same issue because its heavily based on Ubuntu
 
These are just some that I've tried and have liked for one reason or another. I'm sure others will have a thousand more to recommend. I find a lot of it is personal affinity (choice!) to the way things are setup that determine what distro you choose unless you really feel like tweaking a particular distro to your liking.
 
If you haven't been there yet, check out distrowatch.com, it keeps track of almost every distro and provides basic info and links to that distro's site.

---

### Post by Bob Sanchez on 2011-07-22
Ok thanks for the recommendations.

Last night I tried Fedora, openSUSE, Zorin, and then Zorin Lite. 

The only one that successfully loaded to the desktop when I selected to "try it" was Zorin Lite.

I'll probably install this one and see how it goes.

But before that I want to be able to connect to the internet.

When I was using XP I used a Netgear USB adapter. Model number WN121T. Here is the link to the product page. 
[http://support.netgear.com/app/products/model/a_id/2604]("http://support.netgear.com/app/products/model/a_id/2604")

Now I'm trying to see if that model will work with Linux. If I can get that working I'll be more than happy to stick with Zorin Lite.

I'm very thankful for your help so far and if you have any tips on using the Netgear I would greatly appreciate it.

I'll report back if I get it working.

---

### Post by Volens on 2011-07-22
Wireless devices can be a bit of a pain at times. However, I did find a post about your particular model on the forum.
 
[http://ubuntuforums.org/showthread.php?t=537281](http://ubuntuforums.org/showthread.php?t=537281)
 
You need to use ndiswrapper which lets you use windows drivers or something like that.
 
I can't give you much guidance on this though other than keep searching the forums (or google) and that it might be a good idea to make a new thread in the networking section since your issues are starting to move out of the scope of this one.
 
Good Luck
 
Edit: theres also a wiki for this sort of thing
 
Here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

