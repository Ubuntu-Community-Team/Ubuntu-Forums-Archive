---
title: "Ubuntu variant for VAIO VGN AR250G with 512MB RAM"
date: 2013-10-12
forum: Installation &amp; Upgrades
---

### Post by benny74402 on 2013-10-12
I'm currently booting up frugally some small linux distributions at this laptop, mainly Puppies. I want to know really two things:
1) What Ubuntu Studio contains in the case it can run at this laptop?;
2) Can I use the same method for booting up the Ubuntu variant I finally choose?

I'm  using grub4dos as a boot loader. My HDD is partitioned in three different  partitions: sda1, sda2 & sda5 with a swap partition already there. Have plenty of room at sda1 partition (intended target for Ubuntu).

Even though I might burn a cd with the selected iso file that's not the intended way for using Ubuntu.

The reason I'm asking about Ubuntu Studio is because I've Puppy Studio & I like some of the software included there & think it's based on Ubuntu Studio (an old version of it), so the latest stable release might be even better.

As an extra, I would like to know if, once the selected release is installed and running well, if there's the possibility of adding say some apps from Edubuntu (or one with scientific/mathematic apps) to the one I would be running without too much diffuculty?

Thanks in advance for any tip/info as to where to move to from here!

---

### Post by TheFu on 2013-10-13
No idea about that laptop. What CPU?

The main things that make "stock" ubuntu work poorly on older hardware are 2 things. They've gone to a PAE kernel and the default GUI is bloated.  If you install XFCE, LXDE and/or a pure Window Manager, then you can control the GUI runtime bloat. Apps don't care about the GUI much.

Disk storage usually doesn't matter to tte OS - 10-20G is plenty. It is just "data" that needs lots-o-storage.

You can run any apps you like on any distro. It is just a repository/PPA and dependency question. Heavy apps, usually with big, complex GUIs will run a little slower, but they should run. Don't think I'd attempt video editing. I've never loaded any "studio" or "Ed" variant.  Can't imagine that the same apps aren't available on any other debian-based distro.

Puppy is a fine distro, until you realize that running everything as root is a terrible security practice. Dangerous.

---

### Post by heir4c on 2013-10-13
First you can upgrade the RAM. Look for it on second hand sites. A little bit more memory will work better. Than  you can install the "normal" Ubuntu.

But if you can't upgrade now, use Lubuntu 12.04 (or later version). (or try Xubuntu)
You can try it out with a Live-cd/usb and than you open the UbuntuSoftwareCenter and see al the programs you can install. Look there for the programs you have (and like) on Puppy. If there all in the repository than you install Lubuntu on your Laptop.

---

### Post by mörgæs on 2013-10-13
> **heir4c said:**
> 
But if you can't upgrade now, use Lubuntu 12.04 (or later version).

Lubuntu 12.04 has only a few weeks left of support, so it's not worth the effort. Go for 13.10, which is a fairly stable release in spite of being in beta.

---

### Post by benny74402 on 2013-10-18
Thanks to all of you guys for replying!

**TheFu**:  The VAIO has a sticker stating "intel Centrino Duo"; the System  Information tool that comes with this Puppy states Processor >  Name=Intel(R) Core(TM)2 CPU - T7200 @ 2.00 GHz. > Family, model,  stepping = 6, 15, 6 (Pentium III/Pentium III Xeon/Celeron) > Vendor =  Intel.

**heir4c**: Why do you specify those Ubuntu  flavors in your post? Do you have information that Ubuntu (the other  flavors) won't behave well with 512 MB of RAM?

				 					[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=939075") 				 				 					 						 	[**[B]mörgæs**[/B]]("http://ubuntuforums.org/member.php?u=939075") 	 : I still have my original doubts about how to go for running an Ubuntu  OS here at this laptop. Can I use the same method as I'm using with the  puppies with Ubuntu (currently using grub4dos and about 7 OSs, mainly  puppies, all frugal installations - most of them with persistency?

Thanks again guys for your great labor/collaboration with this project!

---

### Post by mörgæs on 2013-10-18
Just try a live boot and see how it works. After that we can take a look at how to install.
No matter which distro you choose some extra memory will make a big difference, as has been posted above.

---

### Post by heir4c on 2013-10-18
The normal Ubuntu versions are to heavy for 512MB RAM. (In the past they run on 512MB, I have very old desktops here (Pentium 4). But now with unity it will work but it will be very slow. (More QT stuff like in KDE/Kubuntu) Asking more of RAM and Graphics. So simple is that. For Ubuntu Studio you need more RAM (I think, try it out and you know). So, if you want specific Ubuntu Studio, buy some more memory. 

Or try a other Linux-dstro or Ubuntu version if you can't upgrade now.
I have a Acer Aspire 3651 (Celeron M and ATI Xpress 200M) and Ubuntu work fine with 1GB but before I have only 512MB and that slowed very down the working of Ubuntu. 
So Lubuntu and Xubuntu work better on that. Or you can try Zorin (Ubuntu based) Zorin works even better on this Acer than on my (secondhand) E35M1-M motherboard with APU E-350 and 4GB RAM. (Strange, I know).
Or use the EDE desktop: [http://equinox-project.org/](http://equinox-project.org/)  Download the EDE distro based on Ubuntu 12.04: [http://www.remastersys.com/downloads/rem-ede-final-1.iso](http://www.remastersys.com/downloads/rem-ede-final-1.iso)

---

