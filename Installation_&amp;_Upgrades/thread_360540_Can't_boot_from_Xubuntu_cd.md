---
title: "Can't boot from Xubuntu cd"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by fedra88 on 2007-02-13
I would like to install Xubuntu 6.10 on an old pc (pentium MMX 166 Mhz, 128 MB RAM, 10X Pioneer CD-ROM drive), but the cd doesn't boot, although I've set the bios in the right way (try boot first from cd drive, etc...). Mind that other bootable cds (e.g. old Windows versions) don't cause any matters, and the Xubuntu cd boots on my main pc. Should I upgrade the bios, burn the cd in a different way...?

---

### Post by lhtown on 2007-02-13
Does it try to boot from the CD and then fail, or just skip checking the CD and go directly to the hard drive?

I would suggest using the alternate CD and checking its data integrity to make sure you got a good download and burn.

The file you download MUST be burned as an image and not as a regular file.

---

### Post by fedra88 on 2007-02-13
I think it tries to read the cd (the green led on the drive blinks) and it takes a few to boot from the hd, but... no certainty about it, because my bios doesn't give any message like "booting from..."

I'm sure I burned the cd in the right way (it worked on other computers).

Thank you very much for your advice, but... er... I just don't know what is the "alternate cd" you say... is it different from the iso I downloaded? why?

---

### Post by Rabbit_Alex on 2007-02-13
I did a search on the Ubuntu main website (ubuntulinux.org) and I found this info about the alternate CD.

```
Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM. 
```

The place you downloaded the Ubuntu image from should also have the alternate image available.  Good luck ):P

---

### Post by maxamillion on 2007-02-13
[www.xubuntu.org/get](www.xubuntu.org/get) <---might help

---

### Post by lhtown on 2007-02-13
There are two versions of Xubuntu disks. You can use the regular CD that you can run as a live CD (boot from CD into a full working environment from which you can install the operating system to your hard drive) and the alternate CD that is mainly for lower memory computers.

At 128 mb of memory, your computer should, I think, theoretically be able to run the live CD, although it really should have more memory.

The alternate CD takes less memory, but the tradeoff is that it won't run as a live CD. However, reports are that it installs more reliably on finicky machines.

If it doesn't work for you, post back and let us know what happens.

---

### Post by lichmeister on 2007-02-13
how hard would it be to mount the iso on another computer and install remotely through a network? im having the same problem [on an equally ancient laptop] but suspect the old cd drive may be giving off a death-rattle at the moment :(

---

### Post by fedra88 on 2007-02-14
Done as you said (Xubuntu alternate cd downloaded, checked and burned); that is what happens now:
1. a "booting from CD drive..." message appears on screen, drive led blinks, can hear the cd spinning up, and...
2. then, after less than 2 seconds... it boots from hard disk :-k 

gettin' a bit frustrated...

---

### Post by lhtown on 2007-02-14
It sounds like maybe your computer doesn't like the brand of CD media you are using. I am guessing you are using a cd-rw.

You might try a single use CD as they tend to be much more reliable across a range of equipment. Also, you could try another brand of rewritable CDs.

I have a Gateway Profile 4 that is a bit picky about some disk media. It drove me nuts until someone explained what was going on.

I hope you get it to work.

---

### Post by fedra88 on 2007-02-15
Unfortunately, I can't use cd-rw at all:-( , cause that drive doesn't even recognise them. (then I'm wasting a lot of cds...)
However, windows (NT4!!) can read the contents of the cds... maybe the drive can't read just the very first files, the ones needed to boot...?

And what about lichmeister's idea? sounds good for me...

---

### Post by fedra88 on 2007-02-24
A little upgrade about my situation...
First try:
In order to avoid reading errors, I replaced my old Pioneer CD drive with a BenQ DVD Unit.
A very little step ahead: after the message "Booting from CD-ROM..." it shoes for less than a second something like "1. FD        system type -(00)" - don't know what does it mean.
Then it boots from hard disk. Again.

Second try:
I mounted the hard disk on another pc, and regularly installed Xubuntu on it. Finally it works, now i've only to bring back my old 3GB HD to my older PC....but... surprise! now it DOESN'T EVEN TURN ON ANYMORE!! it seems that the motherboard is not powered, although drives and leds on the case are. Nothing on screen, no BIOS beep. Connections seem to be ok.

I'm near to throw it out the window. should i?

---

### Post by Vinicio on 2007-07-23
hello, I'm a newbie to the Linux world.

I downloaded and burned as an iso cd XUBUNTU, since I wanted to install it on my old PIII 550 MHz with 256 RAM. I experienced a problem similar to that of Fedra, i.e. even though I insert the cd in the cd-drive, it boots Windows ME anyway. I tried the Live cd on another laptop and the very first menu came up, but then, on choosing the "Start or install" option, I had some problems.

I will be donwloading the alternate version in a few minutes, meanwhile, I would like to know another thing: how can I uninstall Windows ME?  I am not interested in dual booting, moreover since I inserted the cd in the disk drive, W ME freezes once the desktop is loaded (!!!), thus  not allowing me to click on anything. I'd like then to remove the entire OS and only use Xubuntu. Can you help me?

---

