---
title: "Trying to install to Compact Flash card"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by tackle on 2010-02-08
Hi everyone!

I'm trying to install Ubuntu 9.10 to a Compact Flash card. It's not going very well.

I have a 4GB USB drive that I want to install from. I can boot from this USB drive and get into either Ubuntu itself or the installation program only. Either way, I've tried to install it.
My Sandisk Extreme IV 4GB 45MB/s compact flash card is detected in my BIOS and shows up during the installation as well. Whenever I try to finalize and start the installation it gets to 15% and then gives an error on how it can't mount the file system.

I've tried every file system available. 
Funny thing is, I can use gparted to format the card to ext2. It then shows up on the desktop as a drive. If I go into that drive, there's a folder called lost+found. If I try to enter that folder it complains about permissions.

Is there any special trick to installing onto a compact flash card? I've tried with every file system available, with and without a swap file partition as well. I have quite scarce experience with Ubuntu and Linux in general so this is incredibly hard. But I wont give up that easily!

Second thought:
If I can't get this working, would it be just as OK to run it as a "live" distro on the CF card?

The motherboard is an Intel D945GSEJT. Using 1 gig ram.

---

### Post by phillw on 2010-02-08
Hi, and welcome to the Forums.

Assuming you can boot a LiveCD to get into Ubuntu as "Try without altering my computer", then  Selecting System-->Administration-->Create a USB startup disk should happily do all the hard work for you.

Don't allocate all the spare room on your flash card to casper (the persisitant bit) - leave about 10% free - For some reason they can get upset if you allocate it all to casper. I'm sure someone knows why, I just know to leave a bit of free space !!

That method **will** format your flash card, so make sure there's nothing on it that you need **before** you start !!! 

Regards,

Phill.

---

### Post by tackle on 2010-02-09
So this method would be equivalent to using the CF as a Live-CD, right?
And it will be formatted to FAT32?

I don't want to create a USB startup disk; I want to install Ubuntu onto the Compact Flash memory. Are you saying this is the only possible solution? I've read about so many other linux OS's being successfully installed on a CF>IDE, but people having quite some trouble with Ubuntu on IDE drives.

---

### Post by blur xc on 2010-02-09
Just a thought- how are you inserting the CF card?  Is this a dual boot and have you tried it in Windows?  Is it a UDMA card and does your card reader support UDMA cards?  

I use a 4gig transcend 300x udma CF card very often in my UDMA compliant usb internal card reader it it works flawlessly.  The only time it didn't work was back when I was using my old USB card reader that did not support UDMA cards, and it had a lot of issues.  It would transfer a few files and quit.  A few more than quit again.  Back then, I had to use the usb cable that came w/ my camera and transfer files that way, and luckily my camera has a mass storage usb mode so it all went smoothly.

BM

---

### Post by tackle on 2010-02-09
Edit: had some connection problems and thought I lost the above reply

---

