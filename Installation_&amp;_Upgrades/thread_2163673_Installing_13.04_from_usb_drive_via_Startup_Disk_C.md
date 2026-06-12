---
title: "Installing 13.04 from usb drive via Startup Disk Creator"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2013-07-19
Inherited an unwanted Acer Aspire 5315 laptop: I intend to install 13.04.
Downloaded the iso on my desktop running 12.04.
Set up a blank usb drive with Ubuntu 13.04 using Startup Disk Creator. Plugged it into the laptop and it booted straight to Windows.
Tried again - this time, I invoked F2 to access the boot-up and promoted the usb boot priority to first choice: result - the boot-up went to the usb, caused lots of LED flashing - then booted to Windows.
I went back and repeated the creation of the usb Startup drive, in case I had stuffed something up there.
Tried again - it booted to Windows.

I don't have the facility to burn a CD disk to try that, so would like some advice on what I should try next.
Thanks

---

### Post by sudodus on 2013-07-19
- What are the computer specs? Is the CPU an Intel Celeron 540 / 1.86 GHz? How much RAM is there?. What's the graphics chip/card? It might be better to use a light-weight desktop environment (Lubuntu or Xubuntu instead of standard Ubuntu).

- What is installed in the computer now? Does it work? Do you intend to wipe it or make a dual boot?

-o-

1. Try if the USB drive works (boots properly) in another computer.

If this is is the case you need to check what is possible to do in the BIOS menus.

2. Otherwise try some other tool. Unetbootin and cloning with dd will usually make good boot drives.

You might use gparted to make a fresh partition with the FAT32 file system and add the boot flag for Unetbootin. I am not sure it is necessary nowadays, but it won't hurt.

Cloning with dd needs no preparation of the USB drive (but it will overwrite the whole partition table, so it will make it a dedicated drive).

See these links for more details.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by Buster95 on 2013-07-19
It does use the Celeron Intel Celeron 540 / 1.86 GHz chip, running Vista Basic. It has 2 Gb of RAM. I will have to try to find out the graphics card but I'm sure it's the "vanilla" low-end stuff that goes into this kind of box.

I tried booting while holding down F12. It gave me a blue screen with "boot error'.

I don't think there's enough spare space for dual booting - this machine is as slow as a wet weekend. I tried cleaning up all the girly rubbish that my sister loaded onto the laptop, to recover a bit of space, but even after dumping all the "free" horoscope software and the cute ***** cat pictures, I decided that the best and simplest thing to do was to overwrite the whole thing with Ubuntu 13.04.

Haven't tried the USB on my own desktop yet, but will give it a try. I looked in the bios options, while I was changing the boot sequence, but apart from enabling F12, I couldn't see much to tamper with.

If standard Ubuntu 13.04 clogs it up too much, I'll try a cut down version as you suggest - but first I've got to get the usb to read.

---

### Post by sudodus on 2013-07-19
With a computer of that age, I would suggest Xubuntu 12.04.2 LTS, which is supported until April 2015.

I agree, that you should wipe Vista and make a simple and basic install with the whole HDD for linux (one big root partition and one small swap partition (slightly larger than the RAM, say 2.25 GB).

You might try with some boot option, to get it running. See this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


And I think that the computer is able to boot from USB. If not, one option is to remove the HDD and connect it to another computer, where you install Xubuntu. Install no proprietary drivers! Then the installed system will be portable (will work in other computers, for example your Acer, so put it back, and I think it will run well. At this stage you might install a proprietary driver for the graphics chip or wifi chip. But try first without it.

---

### Post by Boab1993 on 2013-07-19
Try using PLOP boot loader, it allowed me to bypass the windows boot loader and the BIOS boot menu, its just an easy was around.
There should be enough for a dual boot system, even 40 GB is technically enough!
You just need to, as you say, overwrite the old stuff.
As for ubuntu standard, it runs fine, there are lower usage version designed for systems such as yours, take a look into 'xubuntu' and 'lubuntu'

Hope this helps

---

### Post by sudodus on 2013-07-19
Plop can probably do the job, but needs a CD/DVD drive and a way to burn a CD,  or a floppy drive plus a floppy disk. But in this case, it might be as easy to burn a full install CD as it is to burn a Plop CD (to get some CD-Rs and borrow a computer with a CD-RW drive). I don't know if there is a floppy drive on that Acer, but I think is might be too new for that.

---

### Post by Boab1993 on 2013-07-19
Hmm, interesting, i just installed their latest release, all you need to do is go into the windows directory and click on the setup.
Don't know whether i have magic hands or its an update.

---

### Post by sudodus on 2013-07-19
You mean Plop? That's interesting. Please post the web page :-)

Does this mean that Plop is installed onto the hard disk drive or flashed into the BIOS?

---

### Post by Boab1993 on 2013-07-19
[http://www.plop.at/en/bootmanager/download.html](http://www.plop.at/en/bootmanager/download.html)

Just got it off the site sir, test it out, im never without!
I think its installed onto your hard drive and is just given priority over other boot loaders(changes the mapfile maybe?)
Would be good to hear your input

---

### Post by sudodus on 2013-07-19
Thanks :-)

I haven't used Plop like that, but I see in your link that it can also boot from a hard disk drive.

> Start of the boot manager from harddisk, floppy, USB, CD, DVD

And it might be a good alternative in this case.

---

### Post by Boab1993 on 2013-07-19
Its honestly a solution to so many problems!
But yeah if it works, it works, can't complain about that.
Was good talking to you sir, im sure we'll meet again on this forum soon.

Au revoir!

---

### Post by sudodus on 2013-07-19
I'm looking forward to seeing you again, *Boab1993*.

Now we are awaiting a reply from the original poster, *Buster95* ...

---

### Post by Boab1993 on 2013-07-19
Haha he's probably moved on thinking "like what the hell is PLOP, im out"

---

