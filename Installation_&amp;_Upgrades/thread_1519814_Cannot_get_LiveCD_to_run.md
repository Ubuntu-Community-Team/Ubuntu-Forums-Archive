---
title: "Cannot get LiveCD to run"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by neubert500 on 2010-06-28
I have a new HP Pavilion Elite HPE-210f with Win7 installed. 8 gig onboard ram 1T HD AMD PhenomII x4 processor. Whenever I try to boot from the  AMD64  Ubuntu CD it gives 
"BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) Built in shell(ash)
Enter 'help' for a list of built-in commands
(intramfs) unable to find a medium containing a live file system."

What information do I need to provide so someone can make sense of this?

I am an ubuntu user, defiantly not a guru. (though I would like to learn!)

Thanks for any help

---

### Post by Paddy Landau on 2010-06-29
I don't know the answer, but I'm answering because I see that no one else has.

The only things I can think of are:

[LIST=1]
[*]If you downloaded the ISO yourself, did you [check the MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM") to ensure that the download was correct?
[*]If you burned the ISO yourself, did you check that the disk burned correctly?
[*]Your computer's BIOS may be set up incorrectly for booting from a CD. Read your computer's manual for how to check this.
[/LIST]
Good luck.

---

### Post by Rubi1200 on 2010-06-29
> **Paddy Landau said:**
> I don't know the answer, but I'm answering because I see that no one else has.

The only things I can think of are:

[LIST=1]
[*]If you downloaded the ISO yourself, did you [check the MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM") to ensure that the download was correct?
[*]If you burned the ISO yourself, did you check that the disk burned correctly?
[*]Your computer's BIOS may be set up incorrectly for booting from a CD. Read your computer's manual for how to check this.
[/LIST]
Good luck.
+1 for good advice.

If you can tell us what graphics card you have that would help and can I assume you are talking about the 64-bit version of Lucid (10.04)?

---

### Post by Virtua-Touch on 2010-06-29
Also, is your processor a 64-bit proc? I see you have AMD64 disc. Try using an i386.

---

### Post by neubert500 on 2010-06-30
Gentlemen, Thank you so much for your replies.

My video card is a ATI Radeon HD5450.

I did not check the sum on the disk, HOWEVER the very same disk booted up fine on my Compac Presairo F500 (ALSO 64 bit)

The system shows that the processor is an AMD Phenom II x4 945 Processor and shows it to be 64bit. That is why I am trying the 64bit Ubuntu.

I again thank you for your assistance cause I want to get AWAY from Microsoft. (Although Win 7 isn't as bad as I feared).

---

### Post by garyedwardjohnston on 2010-09-09
same problem here

---

### Post by Paddy Landau on 2010-09-10
> **neubert500 said:**
> I did not check the sum on the disk, HOWEVER the very same disk booted up fine on my Compac Presairo F500 (ALSO 64 bit)
That's not a guarantee that the disk is OK. I've had a disk work fine on one machine and not on another, presumably because the bit that was wrong was the specific driver being used on the second computer. When I redid the CD, it all worked fine.

Please do check the MD5 sum before you write to disk.

---

### Post by xllxjustinxllx on 2010-09-10
I also had problems running my 64 bit live cd on two different 64 bit systems.

First i went into the bios and changed my sata mode to ide. That worked for the first system.

Using the same cd i tried to boot using my newer system with a 64 bit amd processor. Nothing. I changed every setting and nothing worked. I eventually downloaded the 32 bit cd and it worked fine.

Given that very few programs are written to take advantage of 64 bit architecture i would just run the 32 bit version. Plus its probably alot more stable.

---

### Post by Paddy Landau on 2010-09-10
> **xllxjustinxllx said:**
> Using the same cd i tried to boot using my newer system with a 64 bit amd processor. Nothing. I changed every setting and nothing worked. I eventually downloaded the 32 bit cd and it worked fine.
That's really interesting, and something to remember. I've been lucky; since moving to 64-bit, I've had no problem whatsoever. It may be worth trying 64-bit again with the next LTS release (I believe it will be version 12.4 in April 2012).

---

### Post by ahmed002 on 2010-09-14
Read this thread for an answer.  You'll have to use a USB drive to boot and install Ubuntu because the DVD/BlueRay HP BDDVDRW CH20L in the HPE-210F does not work with Linux.  I get "ata2: link is slow to respond" and then eventually ata2 is disabled.

[http://ubuntuforums.org/showthread.php?t=1570252&highlight=210f](http://ubuntuforums.org/showthread.php?t=1570252&highlight=210f)

---

### Post by nyteryder79 on 2010-10-31
Ubuntu 10.04 and 10.10 do not currently have support for your HP blu-ray drive.  I had to disable the SATA port in BIOS on my Pavilion Elite and install Ubuntu from a flash drive.  I submitted a bug and hopefully it gets looked at and addressed soon as this machine is a popular on as is this blu-ray drive.  Right now I'm using an external dvd-rw drive I had for my netbook.

---

