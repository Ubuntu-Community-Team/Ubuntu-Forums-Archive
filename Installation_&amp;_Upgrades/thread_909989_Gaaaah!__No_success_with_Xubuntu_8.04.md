---
title: "Gaaaah!  No success with Xubuntu 8.04"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by aardvarkash10 on 2008-09-04
Compaq Armada 1750 with 10GB HDD, 128mb RAM, CD-ROM etc

I've been trying a series of "lite" Linux distro's - all the received wisdom says these are now easy to deal with and self load etc...

Dammit - not for me!

Yeah yeah, ran into the BIOS on your Harddrive thing that the Armada has.  By then I had already reformatted the HDD for VectorLinux (which I now can't seem to remove btw - suggestions?)

I'd earlier installed 7.x Ubuntu on a desktop and all went well, but on this lappie, the CD (three different ones now, all burnt on different machines, but all from the same .iso file) cause the CD-ROM drive to rattle up big time then the installer claims it can't find a series of files - "corrupt" etc.  Yes, I did a hash check on the .iso and all good.

So, no doubt a heap of different faults - hands up for a clean install solution please?

CHeers!

---

### Post by mp035 on 2008-09-04
Sounds like unbalanced CD's, sometimes batches of CD's aren't weighted well and vibrate in drives (laptops are especially succeptable to this problem because of the small size of the dampeners on the mech)

Have you considered installing from a usb flash drive?

---

### Post by aardvarkash10 on 2008-09-04
lol!  Yeah, I would do except... the non-operational USB was one of the reasons for giving Linux a go on this machine!!!  Next please...

---

### Post by Zill on 2008-09-04
You are unlikely to be able to run Xubuntu from your hdd with only 128MB of RAM...
> To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.
[http://www.xubuntu.org/get]("http://www.xubuntu.org/get")

I suggest you upgrade your RAM or try a smaller distro such as [DSL]("http://www.damnsmalllinux.org/").

---

### Post by zxscooby on 2008-09-04
I've ran Xubuntu quite well with 128mb of ram, never used it for anything but web browsing tho. 
 You will never get the live cd to install with that much ram The alternate install
cd is the only way to go.

---

### Post by Bucky Ball on 2008-09-04
Yup. Alternate install if you can get that working. You could try a more lightweight distro or start from scratch by installing a base system and just add the packages you absolutely need.

[http://ubuntuforums.org/showthread.php?t=869659](http://ubuntuforums.org/showthread.php?t=869659)

:)

---

### Post by aeb1 on 2008-09-04
> **aardvarkash10 said:**
> Compaq Armada 1750 with 10GB HDD, 128mb RAM, CD-ROM etc

I've been trying a series of "lite" Linux distro's - all the received wisdom says these are now easy to deal with and self load etc...

Dammit - not for me!

Yeah yeah, ran into the BIOS on your Harddrive thing that the Armada has.  By then I had already reformatted the HDD for VectorLinux (which I now can't seem to remove btw - suggestions?)

I'd earlier installed 7.x Ubuntu on a desktop and all went well, but on this lappie, the CD (three different ones now, all burnt on different machines, but all from the same .iso file) cause the CD-ROM drive to rattle up big time then the installer claims it can't find a series of files - "corrupt" etc.  Yes, I did a hash check on the .iso and all good.

So, no doubt a heap of different faults - hands up for a clean install solution please?

CHeers!

I'm in the middle of finishing up an 8.04 install on an Armada 1750.

I run 320MB of ram and a PIII MMC-2 module to get 500Mhz. Anything faster hoses up the outside ports.

Having said that, I am able to made a clean install by loading 8.04 SERVER bare bones, then using apt-get to install the xbuntu desktop graphics, then leverage up to KDE 3. KDE4 ( in the 8.10 prototype )  DOES NOT WORK YET!!!

I still have to manually install the sound and fan fixes...

---

### Post by aardvarkash10 on 2008-09-05
yeah sorry all - I worked out already that the alt distro was the only one to work with...  still the same issues...  thx for the 1750 love aeb - my problem being you are operating about a couple of lightyears beyond my level...  I need basic, and i'm not talking the old style programming language.  Keep it coming guys...

---

### Post by Crafty Kisses on 2008-09-05
Try the alternate CD for Xubuntu if that doesn't work try Damn Small Linux.

---

### Post by Drout on 2008-09-06
"claims it can't find a series of files - "corrupt" etc."

I think it's a bug. I've found a workaround. (I have an Armada 1750 with 64MB ram)
Xubuntu alternate should install with 64 MB ram, but no success :( the same weird messages all the time.

The problem is the memory. You should enable swap during the installation. Somehow it's missing from the installation steps.
Here is how:
Create a swap partition **before **starting the installation. I suggest around 256 MB (170MB doesn't seems to be enough for me).
Start installation, and when it fails:
(on terminal 2 - press Alt+F2)
swapoff -a
mkswap -c /dev/sdx (substitute x, the partition you've created before)
swapon /dev/sdx

go back to the setup screen (Alt+F1) and press retry. The installation will continue

It should be filed as a bug I think.

(I still don't have a successful installation as setup fails when installing kernel-generic. Right now I'm stuck at this point)

---

### Post by Bucky Ball on 2008-09-06
Drout, as we say here, you really would be trying to push s**t uphill with a pointy stick with those specs. Did you check the integrity of you install disk before using? It could be the iso itself is not good.

Having said that, keep us informed. A bug? Hmm. I tried installing from Xubuntu alternate cd with *256mb*. No luck. Added a gig and voila. No problem. Try DSL perhaps or add more RAM and see if you get the same 'bug'. 

As posted by aeb1:

 > I am able to made a clean install by loading 8.04 SERVER bare bones, then using apt-get to install the xbuntu desktop graphicsAn option but with 64mb ... good luck. :)

---

### Post by Drout on 2008-09-06
> **Bucky Ball said:**
> Did you check the integrity of you install disk before using? It could be the iso itself is not good.


Of course. It's ok. I've been running circles writing the same iso (md5 checked) to several media, with different speeds (4x/12x) with different burners. It's not media problem, if I select the same options it fails at the same point. If I select another option (for example another country) then it fails at another point.
But with swap added it's no longer problem. Except the locale setting (at 75%), it takes more than an hour...

From [here]("http://www.xubuntu.org/get"):
> The Alternate Install CD only requires you to have 64 MB RAM.

---

### Post by Bucky Ball on 2008-09-06
> **Drout said:**
>  I've been running circles writing the same iso (md5 checked) to several media, with different speeds (4x/12x) with different burners. It's not media problem

How about integrity of your original download of the iso (not the media). Something may have screwed up with that which is why no matter how many times you burn the media, you are getting the same error in the same place.

You could try downloading again or even better and more reliably, torrent it. :)

---

### Post by Drout on 2008-09-07
> **Bucky Ball said:**
> How about integrity of your original download of the iso (not the media). Something may have screwed up with that which is why no matter how many times you burn the media, you are getting the same error in the same place.

You could try downloading again or even better and more reliably, torrent it. :)

[COLOR="Red"][FONT="Arial Black"][SIZE="5"]md5 checked[/SIZE][/FONT][/COLOR]

---

### Post by LDRoamer on 2008-10-02
I am not sure if this helps but I have Ubuntu 8.04 running on an Aramada 1750. However it is a distribution upgrade of an earlier version of Ubuntu. I didn't install it from scratch. It seems to work fine except no sound. The ES1869 sound card in this machine which did work in Ubuntu at one time has not worked in any Ubuntu version for the last couple of years so its no surprise. 

My machine has 320MB ram and a 60 gig hard disk. Processor is whatever came with it (a 366 PII I think).

---

### Post by zijoud on 2008-11-11
I'm having issues with my 1750 Armada. 64MB, PII processor, 6GB HD. I was trying to install the alternate cd of Xubuntu and every time it got to "setting up the partitioner" it would freeze at 50%. When I escaped out of the window i could see errors saying parts of it couldn't be setup cause the destination was read only. So I formatted the c: partition in dos, there's also the HP Partition for the bios software which is still fine and working.

After I rebooted, the compaq screen would show, then after that my screen would start like "page-flipping" is the closest effect. From what I could tell, it was trying to access the hard drive instead of the CD. So I went into the BIOS and made sure it would boot to CD first. Rebooted, same page-flipping thing. I waited long enough and eventually it says the disk is either empty or cannot be read. Sounds like it's still trying to access the hard drive eventhough i have a bootable CD in the drive that i've been using the whole time. And has worked previous to the format.

So I go back into the BIOS and see that multiboot is not on, BIOS settings aren't being saved. I don't know how to fix this. I've done everything short of taking out the cmos battery. The Fn+F11 didn't do anything. I've tried taking the battery and floppy out and running just on AC. i don't know what else to do =/

---

