---
title: "Ubuntu-XP Dual Installation I/O Error"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by Nu11nV01D on 2010-08-26
Hey everybody how's it going? I'm new to Ubuntu and really higher level computing as a whole. I know a thing or two but not a whole lot more than the average young person. Ubuntu was supposed to be a blastoff point. Problem is I can't get it to install.
 
I followed the directions on the Ubuntu site: I used IfraRecorder to burn the Ubuntu 10.04.1 onto a disc and then rebooted from that disc. I'm running windows XP Service Pack 3.
 
Anyway, it gives me a brief, dark screen with like a crowd of little men and then a happy single man in a circle down at the bottom(?)
 
then it takes me to a black command input line screen and says this:
 
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands
 
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/Output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
 
I tried typing help but it just gave me a bunch of commands I didn't know about. I shut down the computer and took the disc out and XP boots up just fine....
 
I'd really like Ubuntu to work but I can't even get to the install screen at this point.
 
Any help would be appreciated
 
P.S.- I tried a search and didn't find anything, but I could've done it wrong.

---

### Post by tommcd on 2010-08-26
You need to rule out a bad CD first.
First, check the md5sum of the Ubuntu iso file you downloaded to make sure it is good. See "*md5sum on Windows*" here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
It is good that you used Infra Recorder to burn the CD. You should always burn an iso image CD at the slowest possible speed to prevent errors while burning the CD.
Try burning another CD at the slowest possible speed, then boot up the CD and run the option: "*Check CD for Defects*" as it says here:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)
If this reports no errors, then the CD is good and can be used to install Ubuntu.

Also, what graphics card does your computer have?

And welcome to the Ubuntu forums!

---

### Post by Nu11nV01D on 2010-08-26
I will give that a shot, definitely. I have blank CDs to spare so I'll verify using your links. I remember burning the image (or whatever the term is) at the *highest* possible speed simply because that was default. I'll do it the slowest. Unfortunately, however, I can't do that right at the moment. I'll keep you updated.
 
And I have a NVIDIA GeForce 8600 GTS
 
Thanks for the welcome!

---

### Post by Nu11nV01D on 2010-08-27
UPDATE:
 
First I made a new Ubuntu CD using  the *slowest* speed possible. At least, I think I did.
 
Didn't understand the first link you gave. Tried typing in those commands when it went to that black screen, didn't do anything. Couldn't cd the directory or something like that.
 
Tried to check if the CD was valid and here's where it gets tricky. I waited for my computer to boot up and held any key. I was then greeted by a lovely ubuntu screen asking if I'd like to install, or run without installing, or check CD validity. I hit check CD validity.
 
It went to ubuntu screen with loading dots filling up under the word "Ubuntu" then it paused, and went to my original error screen.
 
So close! :mad::cry:

---

### Post by tommcd on 2010-08-27
> **Nu11nV01D said:**
> 
 And I have a NVIDIA GeForce 8600 GTS
My desktop has a Nvidia 8600GT. It works fine on Ubuntu. I always install Ubuntu from the text based alternate install CD, so I can't verify how well the live CD runs with my 8600GT. I don't think your graphics card is the problem here though.

> **Nu11nV01D said:**
> 
First I made a new Ubuntu CD using  the *slowest* speed possible. At least, I think I did.
Just select the slowest speed that Infra Recorder offers you.
 > **Nu11nV01D said:**
> 
Didn't understand the first link you gave. Tried typing in those commands when it went to that black screen, didn't do anything. Couldn't cd the directory or something like that.
The "*md5sum on Windows*" in the link I gave is for checking the md5sum of the Ubuntu iso image file that you downloaded. It is not for checking the CD that you burned that image to. Checking the md5sum of the Ubuntu iso you downloaded will verify that the iso image file is valid and not corrupted.  
> **Nu11nV01D said:**
> 
Tried to check if the CD was valid and here's where it gets tricky. I waited for my computer to boot up and held any key. I was then greeted by a lovely ubuntu screen asking if I'd like to install, or run without installing, or check CD validity. I hit check CD validity.
It went to ubuntu screen with loading dots filling up under the word "Ubuntu" then it paused, and went to my original error screen.

I think a bad CD is most likely the problem here. If you can't even run the "*check CD for defects*" option without it giving you errors, then the CD is likely bad.

Check the md5sum of the iso image you downloaded according to the first link in my last post. Verify that the iso image is good.

Assuming that the iso image is good, then you need to burn a valid CD. Be sure to burn the CD at the slowest possible speed. If you still have problems, perhaps try different CD media. Or try burning the CD on a different computer if you can.
Also use a CDR, not a CDRW.

Write back if you need more help.

---

### Post by Nu11nV01D on 2010-08-27
Alright, I'm an idiot. I didn't scroll down to the Windows part. I downloaded the hash verification software and right clicked the file I downloaded from the Ubuntu site and used Send To to send it to the verification program. It gave me a hash, and the hash didn't match any on the site.
 
so, apparently, its not a good file. Do I re-download it? Find it from elsewhere?

---

### Post by Nu11nV01D on 2010-08-27
Alright!!!

So I re-downloaded the file from the Ubuntu website, checked the hash and it found a match!

So I wrote the image at the slowest speed, stuck it in the drive, rebooted and here I am! I'm currently on Ubuntu, browsing the web and making things happen!

Thanks for the assistance. It appears I can mark this thread as solved. I'm a bit afraid to make the leap to actual install, though. As of now I'm running off the disk. It seems like my drive is working pretty hard.

Any tips on how I should make the partition? The Ubuntu site just tells me to use the built-in installer but... I dunno.

---

### Post by tommcd on 2010-08-28
> **Nu11nV01D said:**
> 
So I wrote the image at the slowest speed, stuck it in the drive, rebooted and here I am! I'm currently on Ubuntu, browsing the web and making things happen!
So be sure to run the option: "*check CD for defects*" if you have not already to be sure the CD you burned is good.
> **Nu11nV01D said:**
> 
 It seems like my drive is working pretty hard.
Ubuntu will run slower from the live CD than it will from the hard drive. CDROM drive access is a lot slower than hard drive access. How much memory your computer has also determines how much of the live CD can be loaded into memory at one time.
> **Nu11nV01D said:**
> 
Any tips on how I should make the partition? The Ubuntu site just tells me to use the built-in installer but... I dunno.
Here are some good guides to getting started with Ubuntu:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by tommcd on 2010-08-29
> **Nu11nV01D said:**
> 
Any tips on how I should make the partition? The Ubuntu site just tells me to use the built-in installer but... I dunno.
Ideally, you should choose manual partitioning. If XP occupies the whole hard drive on 1 big partition, as it usually does, then just use the Ubuntu partitioning program to shrink XP to whatever size you want. Then create 3 partitions for Ubuntu:
1. root: 10-20GB depending on how much space you have. You could go with as little as 6-8GB if you choose not to allocate a lot of space for Ubuntu.

2. swap: The swap partition is analogous to virtual memory in XP. 1GB is fine for swap. If you want to be able to suspend to memory, then make swap at least equal to the amount of memory you have.

3. home: The rest of the hard drive. The home partition is where you will put all your personal files (music, video , text, etc). Think of the home partition as the "My Documents" folder in XP.
All the Ubuntu partitions can be logical partitions using the ext4 file system.

A separate home partition is preferred because when you reinstall Ubuntu, all your personal data is safe on a separate home partition. You just reinstall Ubuntu to the root partition, and your home partition and all your files are safe. See this on creating a separate home partition when you install Ubuntu:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
I hope I have not confused you too much here. Write back if you need more help.
If you only want to try out Ubuntu, you could select guided partitioning and just create a root and swap partition for Ubuntu.

---

