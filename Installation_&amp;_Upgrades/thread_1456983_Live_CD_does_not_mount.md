---
title: "Live CD does not mount"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by INH on 2010-04-17
I've tried to install Ubuntu before, back in 08.  Unfortunately, my computer didn't like the standard install process (just froze up whenever I selected any option from the splash screen - maybe because I have an nVIDIA graphics card), so I wasn't able to get it to work.  Anywway, I saw that they had messed with the default nVIDIA drivers in the 10.04 beta, so I decided to try that.  

I made a Live CD and booted from it.  I hit the "Try Ubuntu without any change to your computer" option.  It thought for a little while, then started the bootup sequence.  Then I got an error message that said: 

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

Could anybody tell me what this means?  Should I try using the alternate install, or did I just get a bad disc? (I don't think I did, though, because I redownloaded and burned again and still got the same error.)

---

### Post by aleagi on 2010-05-07
+1 here!!

Same problema, Dell Inspiron 1525 and Ubuntu 10.04 32 bits...

Any help would be appreciated!

TIA!

---

### Post by Fanin on 2010-05-23
I am installing xubuntu on an asus eeepc 900 and am experiencing the exact same problem

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

i used [unetbootin]("http://unetbootin.sourceforge.net/") to make a liveusb drive and this error message pops up every time.

please keep in mind that i am a noob :)
-thanks

---

### Post by Fanin on 2010-05-23
i tried using [_pendrivelinux_]("http://www.pendrivelinux.com/") insted of unebootin and everything went smooth :P

---

### Post by aweber on 2010-08-14
Same problem using LiveCD on Dell Latitude D505. 

MD5 of iso is verified. Boots fine into VirtualBox elsewhere. Same iso on USB boot does not even get this far.

---

### Post by mörgæs on 2010-08-15
Does it boot with 9.10?

---

### Post by seochamp on 2010-08-15
I used the standard graphical installer for Ubuntu 8.10 (Intrepid Ibex). I was able to get the welcome screen and run some of the basic utilities (check disc, check memory) but when I attempted to run Linux from the boot CD or install it, it froze about 5 minutes into the process with a blank screen.

---

### Post by mörgæs on 2010-08-15
Welcome to the forum.

Are you aware that 8.10 is unsupported? 
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by MartyBuntu on 2010-08-15
On a few problematic machines I've had, I used the "alternate install CD".

---

### Post by aweber on 2010-08-17
> **aweber said:**
> Same problem using LiveCD on Dell Latitude D505. 

MD5 of iso is verified. Boots fine into VirtualBox elsewhere. Same iso on USB boot does not even get this far.


On the Latitude D505...

Yes 9.10 booted fine when installed originally (I didn't try booting into it recently)

I tried the Alternate CD and ended up with [http://yfrog.com/mwdsc07912hj]("http://yfrog.com/mwdsc07912hj")  

More screenshots of the errors (which I don't understand):
[http://yfrog.com/j4dsc07913hj]("http://yfrog.com/j4dsc07913hj")
[http://yfrog.com/fvdsc07911dj]("http://yfrog.com/fvdsc07911dj")
[http://yfrog.com/mwdsc07910cj]("http://yfrog.com/mwdsc07910cj")
[http://yfrog.com/mvdsc07909lj]("http://yfrog.com/mvdsc07909lj")


(the "add image" button doesn't work in these forums?)

---

### Post by mörgæs on 2010-08-17
The screen shot indicates a problem on the CD. Have you tried booting and selecting 'test CD for defects'?

If you are going to burn a new CD, it is best to download from here:
[http://cdimage.ubuntu.com/lucid/daily/current/](http://cdimage.ubuntu.com/lucid/daily/current/)

This will give an installation CD with all bug fixes (as of yesterday) applied.

---

### Post by aweber on 2010-08-18
> **mörgæs said:**
> The screen shot indicates a problem on the CD. Have you tried booting and selecting 'test CD for defects'?

If you are going to burn a new CD, it is best to download from here:
[http://cdimage.ubuntu.com/lucid/daily/current/](http://cdimage.ubuntu.com/lucid/daily/current/)

This will give an installation CD with all bug fixes (as of yesterday) applied.

Thanks mörgæs, you got it. The default image, and the image you recommended here both passed md5sum, were burned with Brasero, then failed the 'test CD for defects' test. Sounds like this is a different issue than the original thread, so I'll relocate this or pick it up in another more appropriate thread.

---

### Post by mörgæs on 2010-08-18
You are welcome. 

Brasero has had some problems over time. You could try Gnomebaker in stead, and always burn with slowest speed possible.

---

### Post by ZachreyBC on 2010-10-03
Hi there!

I just had an amazing experience with Ubuntu Live CD and then I ran into a snag. Thank you so much to all the people who make such an amazing performance possible!

My friend has a WinXP laptop (HP Pavillion dv6000) with an apparently failing hard disk (Win XP hangs after scandisk on boot up).

I downloaded Ubuntu LiveCD on my Powerbook G4 with OS X 10.5.8 and confirmed the MD5 hash. Praise the Lord!

I burned it onto an HP CD-R 700 MB CD. Praise the Lord!

I changed the boot sequence on his laptop to boot off the CD first. Praise the Lord!

On power up, it read the CD and briefly said ...LINUX...DEBIAN...   PRAISE the LORD!!!

Then it asked me if I wanted to Try Ubuntu or install ubuntu and I clicked on Try. Praise the LORD!

It loaded up and I had an Ubuntu Desktop! Praise the LORD!

I saw the wireless icon in the upper right and it saw our WAP! PRAISE THE LORD!!

I entered the password and I was on the Internet! PRAISE THE LORD, HALLELUJAH!!!

I ran firefox and checked my email! PRAISE THE LORD!

I accessed all the disk partitions on the crippled disk! PRAISE THE LORD! PRAISE THE LORD!

I put in my USB memory stick and it recognized it! PRAISE THE LORD!

I copied  almost 8GB onto the memory stick! PRAISE THE LORD, HALLELUJAH!

Then I shut it down and booted off the hard disk (Win 98 command prompt) and ran scandisk on the largest partition and it found a bunch of bad blocks towards the end.

Then I rebooted off the LiveCD and got:

(initramfs) can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

What in the world happened? Could the CD been written to somehow? I can still get the Win 98 command prompt on the hard disk.

Thanks in advance!
Zac

---

### Post by mörgæs on 2010-10-03
Hi, welcome to the forum.

I take for granted that you are trying to install Ubuntu on the machine. Though the CD has passed the MD5 test, it is still good to run the 'test the CD for defects' offered in the menu.

If the machine has less than 512 MB memory, I would try installing using the alternate CD:
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

