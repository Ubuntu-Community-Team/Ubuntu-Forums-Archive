---
title: "Unable to boot from install CD"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by Ertai87 on 2011-09-05
Hey all!  This is probably going to be something stupid I did, but I'm having problems using the install ISO file.  I downloaded the 11.04 file, 32-bit, burned it as a disk image through Windows (7) Explorer, and it seemed to work, but the CD appears to not be bootable.  I did this using a DVD-RW disc, if this is at all relevant.  What did I do wrong/how do I make my install disc bootable?

The reason I want to have a bootable disc is to use as a reformat disc if I ever get any nasty viruses.  I don't feel like reformatting ATM for a whole host of reasons, but eventually I will need to and when I do I want to do it through my BIOS without having to boot into a corrupt OS to do it.

Thanks.

---

### Post by MAFoElffen on 2011-09-05
> **Ertai87 said:**
> Hey all!  This is probably going to be something stupid I did, but I'm having problems using the install ISO file.  I downloaded the 11.04 file, 32-bit, burned it as a disk image through Windows (7) Explorer, and it seemed to work, but the CD appears to not be bootable.  I did this using a DVD-RW disc, if this is at all relevant.  What did I do wrong/how do I make my install disc bootable?

The reason I want to have a bootable disc is to use as a reformat disc if I ever get any nasty viruses.  I don't feel like reformatting ATM for a whole host of reasons, but eventually I will need to and when I do I want to do it through my BIOS without having to boot into a corrupt OS to do it.

Thanks.
2 things to check:

 - Check the checksum of your download to make sure the download was successful and the ISO is good on your copy of the ISO.

 - When you go to burn the ISO, go into advanced options... and change the burn speed to the lowest available option.  (4x to 8x)

 --> Use a CD disk for this CD Image and do not make it a rewritable image. (You'll have problems booting it if you don't follow this.)

You could use DVD if you usee Linux "dd" to write the image...

As a re-writable image (??)  It is possible, but you would be canceling out what your plan for it is - to battle viruses, right?  Where you would want something external that cannot be altered by something that's intended attack tactic is rewriting and altering data?

What may be a better ISO for your "plan" is:
[Version *11.04* | *Ubuntu* Rescue *Remix*]("http://ubuntu-rescue-remix.org/node/982")

...which already has utilities for anti-virus and data recovery built/installed  in.  (and it has a support thread to help users use it and it's rescue utilities when they are needed most!!!)

---

### Post by ajgreeny on 2011-09-05
Although many people say you should never use RW disks for burning iso images, I do it all the time and have never had a problem of any sort, so I doubt that is the problem.

Can you try the disk on another machine, just to boot to it, not install or anything, which will at least tell us if the disk is OK.  It is also worth checking the md5sum of the iso file to make sure it is correct.

See [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") for details of the md5sum and how to check it, if you don't already know.  If that is OK reburn at as slow a speed as possible and try to install again.

---

### Post by Old_Grey_Wolf on 2011-09-05
Edit: :lolflag: MAFoElffen and ajgreeny type faster then I do.

Use the instructions [here]("https://help.ubuntu.com/community/HowToMD5SUM") to check the MD5 checksum of the iso you downloaded. If the MD5 is correct then burn the DVD at the slowest rate possible. If the MD5 is not correct try downloading again using one of the torrents sites offered in the alternate download section of the Ubuntu download site.

---

### Post by Ertai87 on 2011-09-06
Thanks all!

I did burn it as a rewritable image, as I had tried doing it as a write-locked disc before and it messed up, wasting a perfectly good DVD-RW in the process.

I don't have another machine to check on, unfortunately.

I checked the MD5 checksums just now, they are the same.

Is there a recommended burning program I should use to burn the ISO, or is the default one that comes with Windows 7 good enough?

I would try using a CD-R, but I've tried a couple times already and each time I've had problems (one time I got a noncritical install failure during the install and the other time I burned a CD which screwed up my computer, although it was likely the computer and not the CD that was the problem).  I'm afraid that the disc capacity and ISO file size are too close and it might mess up that way.  Thoughts?

---

### Post by ajgreeny on 2011-09-06
> **Ertai87 said:**
> I did burn it as a rewritable image, as I had tried doing it as a write-locked disc before and it messed up, wasting a perfectly good DVD-RW in the process.
Not sure I fully understand what you mean there;  if it was a DVD-RW, you can surely use it again, even if it was finalised in the iso burn you did first time.  Perhaps I don't understand what a "write-locked" disk is, but I presumed you meant finalised.

Either way, I can not really help with burning on windows as I don't have windows any more.  When I last did it was about 5 or 6 years ago, and I used a freeware app CDBurnerXP Pro, still available and in spite of the name, also works on Win7.  Always burn at as slow a speed as possible, and see if thathelps.

---

### Post by Ertai87 on 2011-09-06
Thanks aj, I was able to re-burn the "finalized" DVDRW without problem.

An update: I tried reburning the image to a new DVDRW (the one aj helped me save) but I still can't seem to boot from it.  Has anyone had experiences burning to a DVDRW before?  I don't see why it should be any different from a CDR, but if anyone knows something I don't I don't mind trying it.

At this rate I may end up just formatting with Ubuntu and get it over with; I'll have to do it eventually and once it's done it's done.

Thanks again all, and keep the helpful comments coming!

---

### Post by haqking on 2011-09-06
> **Ertai87 said:**
> Thanks aj, I was able to re-burn the "finalized" DVDRW without problem.

An update: I tried reburning the image to a new DVDRW (the one aj helped me save) but I still can't seem to boot from it.  Has anyone had experiences burning to a DVDRW before?  I don't see why it should be any different from a CDR, but if anyone knows something I don't I don't mind trying it.

At this rate I may end up just formatting with Ubuntu and get it over with; I'll have to do it eventually and once it's done it's done.

Thanks again all, and keep the helpful comments coming!


Are you burning the image or just making a DATA disc by placing the .iso onto it ? When using windows explorer it usually makes a Data Disc byt just burning the file to it instead a bit copy as an image

Common mistake

---

### Post by ajgreeny on 2011-09-06
> **haqking said:**
> Are you burning the image or just making a DATA disc by placing the .iso onto it ? When using windows explorer it usually makes a Data Disc byt just burning the file to it instead a bit copy as an image

Common mistake
@ haqking:  A very good point, but as the OP said he burned an image I assumed he was doing it right.

@OP:  have a look at the DVD in your windows file manager.  Does it contain just one file, **ubuntu-11.04-desktop-i386.iso** (or the 64 bit version) or does it have a number of folders and files on it?  If it is just the one iso file, you need to do it again but choose burn as an image from your burning software.

---

### Post by haqking on 2011-09-06
> **ajgreeny said:**
> @ haqking:  A very good point, but as the OP said he burned an image I assumed he was doing it right.

@OP:  have a look at the DVD in your windows file manager.  Does it contain just one file, **ubuntu-11.04-desktop-i386.iso** (or the 64 bit version) or does it have a number of folders and files on it?  If it is just the one iso file, you need to do it again but choose burn as an image from your burning software.


Yeah i saw he said that, but ive seen it so many times before only 2 weeks later to find out it was a data disc after all....LOL

@OP as ajgreeny says above check the CD/DVD contents for file structure, if a single file then it needs to be redone as an image.

---

### Post by Ertai87 on 2011-09-07
@haqking/ajgreeny: The first 2 times I did it I just burned the ISO to the disc.  Then I realized I was doing it wrong and made a disc image.  I now have 2 different DVDs both with the contents of the ISO (not the ISO itself) on them, and I can't boot from either one.

---

### Post by haqking on 2011-09-07
> **Ertai87 said:**
> @haqking/ajgreeny: The first 2 times I did it I just burned the ISO to the disc.  Then I realized I was doing it wrong and made a disc image.  I now have 2 different DVDs both with the contents of the ISO (not the ISO itself) on them, and I can't boot from either one.

ha thought so ;-)

anyways when you say cant boot to it, what is the error you get when you try ?

I assume your BIOS is set to boot from CD/DVD ?

and it if all else fails make a [USB bootable flash drive ]("https://help.ubuntu.com/community/Installation/FromUSBStick")

and buy yourself a different batch of CD/DVD's maybe ;-)

---

### Post by nipunshakya on 2011-09-08
> **Ertai87 said:**
> Thanks all!
Is there a recommended burning program I should use to burn the ISO, or is the default one that comes with Windows 7 good enough?


I would recommend you to use ImgBurn, a very user friendly and easy to use image burner that goes flawless with windows 7. you can download it from following link:
[www.imgburn.com/index.php?act=download]("http://www.imgburn.com/index.php?act=download") . . . its totally free :)
 and also make sure that you have a good image of your download...be sure that your image has a list of files enlisted in it rather than just iso. . . check it using zip utility. . . Goodluck.


Regards,WinuxUser

---

### Post by Ertai87 on 2011-09-08
> **haqking said:**
> ha thought so ;-)

anyways when you say cant boot to it, what is the error you get when you try ?

I assume your BIOS is set to boot from CD/DVD ?

and it if all else fails make a [USB bootable flash drive ]("https://help.ubuntu.com/community/Installation/FromUSBStick")

and buy yourself a different batch of CD/DVD's maybe ;-)

I don't get an error.  My boot loader (if it can be called that) hangs for a bit and I can hear my CD drive going, but then after a minute or so it just boots up Windows like normal.

And yes, I've checked my BIOS settings and it does check boot from CD/DVD first, and I've also gone into my boot loader manually and told it to boot from CD/DVD manually.  Neither solution works.

I'd like to try a bootable flash drive, but that doesn't solve the problem if I get a virus; the virus can (theoretically?) populate itself to the USB drive when I go to format, no?  I don't know much about booting from a USB drive so I'm guessing it's a worse idea security-wise than using a CDR/DVDR.

---

### Post by nipunshakya on 2011-09-08
> **Ertai87 said:**
> I don't get an error.  My boot loader (if it can be called that) hangs for a bit and I can hear my CD drive going, but then after a minute or so it just boots up Windows like normal.

And yes, I've checked my BIOS settings and it does check boot from CD/DVD first, and I've also gone into my boot loader manually and told it to boot from CD/DVD manually.  Neither solution works.

I'd like to try a bootable flash drive, but that doesn't solve the problem if I get a virus; the virus can (theoretically?) populate itself to the USB drive when I go to format, no?  I don't know much about booting from a USB drive so I'm guessing it's a worse idea security-wise than using a CDR/DVDR.

I guess your write on the DVD isn't proper...it may be corrupt...otherwise there might not be any other reason for you not to boot from the CD drive (if you have set it to primary one in BIOS). . . when i first tried to install ubuntu 11.04 from a CD, it would just load and load and load till forever...i dumped the CD , made a fresh download and then used the ImgBurn to burn again and had my ubuntu installed....

---

### Post by Ertai87 on 2011-09-11
Tried installing and using InfraRecorder (as recommended on the install page) to reburn the CD at minimum speed.  Still unable to boot from CD.  I think I might just format with Ubuntu now anyway, especially since my main complaint was that Ubuntu doesn't natively support my wireless card but I can't use wireless these days anyway (no networks).

---

### Post by Ertai87 on 2011-09-11
My DVD drive started messing up, so I decided that I didn't want to wait until something even worse happened, just in case.  I ran WUBI and now I have Ubuntu loaded on my laptop.  Hopefully it works better than the 'Doze.

---

