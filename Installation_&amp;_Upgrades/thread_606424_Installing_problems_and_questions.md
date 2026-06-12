---
title: "Installing problems and questions"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by ryanster01 on 2007-11-07
i have the live cd 7.10 straight from ubuntu 
I selected the Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
I have two old Dell Latitude Cxp Laptops
pentium 3 inside with windows2000pro on it already
i know both of them have aleast 256mb of ram the harddrives are small i think 10gb on one and 15gb on the other. im doing both at the same time both go to the ubuntu menu, i select start and install, both go to the ubunta loading screen then one goes through a check list of stuff and [ok..] checks every thing then black screen, other goes to a long list of numbers starting at  [ 100.000000] im about at [ 300.00000] then stops both are still on idling so did it freeze or does this take more than 20mins 

any help well be great thanks ryan

---

### Post by John Read on 2007-11-08
Perhaps try Xubuntu. It's supposed to be good in situations where you have older hardware.
cheers, John R.

---

### Post by Herman on 2007-11-08
Hello ryanster01,
With 256 mb of RAM, the Ubuntu Live CDs will run okay but I have found they can be extremely slow or just about freeze when starting to install, at least in the computers I tried them in.

If you want to use the Ubuntu Live CD to install in a computer with 256 mb of RAM or less, you can do it, but the trick to it is to use a [GParted -- LiveCD]("http://gparted.sourceforge.net/") to partition your hard disk with first.  Make sure you make a swap area, perhaps one around 1.0 GB in size. Then install with a Ubuntu LiveCD and it will automatically find that swap area and use it for the extra memory it needs and your installation will be able to proceed normally. (Unless you have some other problems as well).

Another option would be to use the Ubuntu 'Alternate' CD to install with, the alternate CD can be used in computers with less than 127 mb of RAM and installations are possible with it with even as little as 32 mb of RAM.

Ubuntu, Kubuntu and Xubuntu are all available in both the Live CD and the alternate CD.

As John Read said, Xubuntu seems to work little better than Gnome in computers without a lot of RAM.
I have one computer with 127 mb of RAM (at the moment), and I have Xubuntu in it, and I also have IceWm, Fluxbox and Gnome desktops.
I like Xubuntu, and I have also developed a great liking for IceWM lately, so I guess you might say I'm running 'Icebuntu' now, at least in that computer.
Icebuntu is even a little quicker then Xubuntu in low RAM machines, I feel.
Probably you will find that even Gnome (Ubuntu's default desktop), will run with 256 mb of RAM, but it will be just a tad on the slow side, but it will work okay.
After you install Ubuntu or any other *buntu, you can install other desktops later if you want to try them out and see which you like and which performs best. The only disadvantage is you may have a few more updates to download from time to time.

One final tip about installing in older computers (or any computer), is to try to clean the lens in the optical drive if continue to experience erratic behaviour in the installer. This can be caused by a small grain of dust or oily film on the CD/DVD drive lens, and if that can be reached, it can be cleaned with a Qtip dipped in some denatured alchohol. (In some countries called a 'cotton bud' and some 'methylated spirits'). 
The optical drive lens in some laptop CDROM drives slides out with the CD Drawer, so it is easily reached for cleaning, but on the other hand, more exposed to the elements when the drawer is open.
Desktop CD-ROM drives tend to have their lenses built in and difficult for most people to access, so in that case, cleaning a lens could be a tricky job. You might need to take the drive apart and put it back together again, a job requiring considerable skills and tools . In some cases it would be easier to upgrade to a new CD/DVD drive, if you can afford one. Those are relatively cheap these days. 
Since yours are laptops, hopefully they will have optical drive lenses you can easily reach and clean.

As well as that you could have some other problem too, who knows, but those are a couple of ideas for you to start with that might help. Good luck, I hope you succeed. 

Regards, Herman :)

---

### Post by ryanster01 on 2007-11-08
> **John Read said:**
> Perhaps try Xubuntu. It's supposed to be good in situations where you have older hardware.
cheers, John R.

this did work but im still going to try herman advice on some things that he mentioned

thanks again guys

---

