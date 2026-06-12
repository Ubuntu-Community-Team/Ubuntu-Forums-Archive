---
title: "What's next for .img file for 9.04 beta"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mikeh22 on 2009-04-06
I just downloaded 
ubuntu-9.04-beta-netbook-remix-i386.img
because I want to run it from a USB flash drive on a netbook. 
I can't find any documentation on what to do next. 
The download page 
[http://cdimage.ubuntu.com/releases/9.04/beta/](http://cdimage.ubuntu.com/releases/9.04/beta/)
says nothing. 
I searched the forums and came up empty. 
Where is the doc on this? 
Thanks.

---

### Post by kanikilu on 2009-04-06
These instructions say they are for Jaunty daily, but should apply to the beta (just don't follow the download instructions since you've obviously already done that).

[https://wiki.ubuntu.com/UNR#UNR%20Jaunty%20Daily%20Image%20Installation](https://wiki.ubuntu.com/UNR#UNR%20Jaunty%20Daily%20Image%20Installation)

---

### Post by mikeh22 on 2009-04-07
Thanks for the link. I'm starting from Windows and too concerned with security to install a program I never heard of from a website I never heard of. If that's the only way to make a bootable USB flash drive from an .img file, then I'm out. And the instructions are incomplete too.

---

### Post by nquinnathome1 on 2009-04-07
I understand your security concerns, but I have used the flashnul program myself, and the program is just fine; I'm sure if there was anything dodgy about it the maintainers of the Ubuntu Wiki would not have posted it. In terms of instructions; what's not complete? It tells you everything you need to get a USB-bootable made.

---

### Post by mikeh22 on 2009-04-07
Thanks for that. I'm new to the forums and thus don't have a feel for how trustworthy the information is. What I find incomplete about the instructions for dealing with an IMG file is: 

The concept behind the flashnul program. What does it do and why does this need doing? 

Are all the files wiped out on the USB flash drive? 

What file system(s) can the USB flash drive have? Not have? 

Can other files exist on the flash drive after its been made bootable.

---

### Post by Therion on 2009-04-07
> **mikeh22 said:**
> What I find incomplete about the instructions for dealing with an IMG file is: ...  The concept behind the flashnul program. What does it do and why does this need doing? 
Well, not too sound harsh but those instructions are for *using the application*, they're not supposed to be a detailed thesis on the applications genesis or its *raison d'etre*. 
What does it do?  It makes a USB "jump drive" a bootable device suitable for installing an Operating System.


> **mikeh22 said:**
> Are all the files wiped out on the USB flash drive?
99% sure the answer is "yes" and I would operate on that assumption until it's proven otherwise.  


> **mikeh22 said:**
> What file system(s) can the USB flash drive have? Not have? 
I'm not sure I understand this question.  
.iso 9660 is pretty much THE standard for OS installations... Is that what you're asking? 


> **mikeh22 said:**
> Can other files exist on the flash drive after its been made bootable.
The drive will have been formatted as a bootable .iso so if you want to store additional data to it you'll need to partition it.

---

### Post by coffeecat on 2009-04-07
**mikeh22**, I think this is what you want:

[https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/ImageWriting](https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/ImageWriting)

You can either use the dd command as they suggest or the Image Writer miniapp which is just a GUI frontend to dd.

Be careful with the installer. There's a bug in it. When I used it to install to my EeePC it said it had to unmount the EeePC internal drive (which came up as sda), which is fair enough. Then it said it wanted to unmount sdb (which is itself). I thought that was unwise. :-k At this point I clicked on 'Go Back' and all was well.

Your mileage, of course, may vary.

**Edit:** Oh, and Jaunty nbr runs very well on my Eee, thank you. :)

---

### Post by mikeh22 on 2009-04-07
@Therion: not harsh at all, I appreciate the assistance. 

As to the file system issue, I recall reading about utilities that made USB flash drives bootable that had file system restrictions. I forget the details, but it required a specific file system (perhaps FAT16 or FAT32) on the flash drive. Thus if the flash drive was NTFS or EXT3, it wouldn't work. That was what I meant by the question.

---

### Post by mikeh22 on 2009-04-07
@coffeecat: Thanks for this, it's just what I was looking for, except for the OS. It assumes your starting from Linux. I'm starting from Windows.

---

### Post by Therion on 2009-04-07
> **mikeh22 said:**
> @Therion: not harsh at all, I appreciate the assistance.
Okay, cool.  Sometimes I come across as... Well, let's just say if I am, you'll know it. ;)

> **mikeh22 said:**
> As to the file system issue, I recall reading about utilities that made USB flash drives bootable that had file system restrictions. I forget the details, but it required a specific file system (perhaps FAT16 or FAT32) on the flash drive. Thus if the flash drive was NTFS or EXT3, it wouldn't work. That was what I meant by the question.
Gotcha.  Never read that myself so I'm not sure what the issue(s) would be. I'm no expert either, though, so...  I dunno.

---

### Post by coffeecat on 2009-04-07
> **mikeh22 said:**
> @coffeecat: Thanks for this, it's just what I was looking for, except for the OS. It assumes your starting from Linux. I'm starting from Windows.

Not a biggish problem. Have a you got a live desktop Ubuntu CD you can run on a desktop or laptop machine? Simply boot from that and use the terminal dd command. Or if you want to use the GUI Image Writer, it's only a couple of hundred kb. So long as you've managed to get an internet connection with the live CD, simply install it using the Synaptic package manager. It'll only get installed to RAM, of course, not written to the HD, and will be lost as soon as you shut down, but as it's going to be a single use application that won't matter much.

---

