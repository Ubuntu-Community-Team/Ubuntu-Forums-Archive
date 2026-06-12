---
title: "&quot;Permission Denied&quot; During Installation"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by ChromeFusion44 on 2011-11-19
When I'm just about to finish installing Ubuntu, I get an dialog box with an error saying the following:


PERMISSION DENIED
Check log in C:\doc~\John\Temp~\wuibi "then there was some random numbers" for more information.


By the way, that's not that the exact path.It was something like that though, and I also know that thats not even a real path.I though the Doc~ was Documents and Settings and I thought that Temp~ was Temporary Files or whatever the folder is called.

There is also a warning box that says I dont have enough memory.(NOT MEMORY IN A HARD DRIVE, BUT PHYSICAL MEMORY/RAM)

I'm also running on a Windows XP with Service Pack 3 and I think I have an x86 processor.
My version is also the 32 (or is it 26?) bit.My processor is also fairly small and slow, but it handles many other tasks fine.

Any help out there? :???:

---

### Post by raja.genupula on 2011-11-20
Download the Ubuntu again from its official site and mount it by using daemon tools and Run the Wubi again.

But i wanna suggest you , if you don't mind...please install Ubuntu as a separate Partition , its better in all aspects.

Thank you.

---

### Post by Rubi1200 on 2011-11-21
Hi and welcome to the forums ChromeFusion44 :)

What is the current situation; are you able to boot into Ubuntu?

---

### Post by Bucky Ball on 2011-11-21
Release would be good. 11.10 I'm guessing. And yes, a full installation is better in lots of respects (faster for starters). Wubi is intended to try Ubuntu, *not* as a permanent situation ...

You could try a more stable version, the LTS release 10.04 would be a good start. ;)

---

### Post by ChromeFusion44 on 2011-11-23
First off, sorry I haven't replied.
Ive been pretty busy lately.:neutral:

Anyways, now I kind of get where your going.Wubi is just for trying Ubuntu, not _*permanently. *_
I was going to install it permanently, but I didnt know that Wubi wasn't for that. xD
So, now I'm going to do the download of Ubuntu that isn't Wubi.I'm pretty confident that this will work, but I DO have another question.

Since I'm going to be installing Ubuntu permanently, can I just skip the step where you burn the files and stuff to a CD or USB drive?My USB drive is too small anyway, and I don't have any CD's to burn to.

Thanks for the help,

ChromeFusion44

---

### Post by Bucky Ball on 2011-11-23
No, you need to download the ISO and make a CD or USB from it, boot from that and install onto an empty partition (or free space). I know no way of installing online although I guess it could exist. Never heard of it though ...

BUT, and this is a little trickier, especially for a novice, you can download the minimal install. This will give you the basic packages to get you up and running, then you can just install what ever other packages you want via the internet. :) This give you a sleek, clean install with no fat, only the things you like. I have a partition like this and it is *really* fast install. This should explain everything:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

What size your USB dongle?

PS: For a new comer I would seriously consider 10.04 LTS, the long term support release. Rock solid. 11.10 has been out a month and problemmatic and buggy for now (for many). You can always work your way up or indeed have different releases on different partitions to try them. Always good to have one stable, working install to fall back on though. Good luck!

---

### Post by ChromeFusion44 on 2011-11-23
Hmmm...
Ive checked out the minimal install, and Ive looked at the 11.04 LTS, and I think Im leaning a little more towards the 11.04 LTS release.

Pretty much the only reason I'm getting so confused with this is because Ive never really worked with Ubuntu and Ive never messed around with my BIOS or anything with booting, really.
When it comes to PC, I'm a windows guru though.Thing is, my Windows XP is just too old, and I don't feel like paying to upgrade to Windows 7...
So, when it comes to choosing all the versions and stuff for Ubuntu, I'm pretty dumb. xD

Anyways, I think I'm going to try playing with the BIOS settings for a while, and if all else fails, just switch to the LTS release, and go through  another hour of downloading. :|

Thanks for the help though! :)

Oh yeah, I forgot!
My USB drive's size is 1 gigabyte.LOL, its pretty small.
The Linux pendrive installer thing said to have at least 2 gigs, but no errors occurred, so I thought it was fine.

---

### Post by Bucky Ball on 2011-11-23
Hey, you're missing some things here. The ISO image is less than a gig. It is designed to fit on a CD. It will fit on your dongle no probs, that size would be recommended. You need two gig of something else would be recommended I imagine (on the machine you're installing to and I imagine it refers to hard drive size, not the boot media). Can you point me to the link that saw?

In BIOS, just go to the section called 'Boot' or something like that, change the boot device to CD (or USB), hit f10 to save changes and restart, that's it. Some machines you can just hit F2 at boot and it lets you choose what device you want to boot from without going to the BIOS and changing anything. 

PS: Regular 'Buntu (Xubuntu even smaller) shouldn't take an hour. Minimal install certainly won't take anything like an hour. It is minute with only packages to get you up. You download the rest of 'Buntu (or the bits you want) via the desktop of the minimal install. You can install whatever desktop environment you want with minimal. If your machine low spec I would try Xfce maybe. Or you could just download Xubuntu and try that. I use it and love. 

If you are a Windows guru you will soon get the hang of this (and possibly love it). Just take a 15 degree turn in your thinking and you're there. Just more flexible in every respect and a lot more stable when fixed and tweaked.

10.04 LTS is the current long-term support release, supported until April 2013. ;)

---

### Post by ChromeFusion44 on 2011-11-24
OK, well Ive also talked with some other people using older laptops, and a lot of them just said to burn a CD.
The thing where I hilight the USB and hit F10 to save the changes didn't work.

So, yeah...
I'm just gonna burn a CD and see how it goes.

---

