---
title: "Weird Errors Installing Ubuntu!?"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by crashovaride on 2008-08-23
All,

    This has been stumping me for the last 3 days. I'm tried to install Ubuntu with various operations. Here is what i have tried.

I have tried to resolve any issues with the processor (trying 3 P4 chips)
I have removed SATA CDROM and HD with IDE
I have swapped out 3 different types of AGP cards
I have installed windows successfully.
I have attempted to install Ubuntu 5, 6, 7 and 8, Suse, Solaris, and FC3, and RH8. All Fail.
I have installed windows, however that junk works. 

Here are the errors i face:
       SQUASHFS error: sb_bread failed reading block 0x929b5
       Cannot start X
       * when running vi, apt-get or any other tool i get segment faults!
       When i try minimal graphics mode, it errors.
       I get swap_file bad block/page
 
System Specs:

Asrock P4VM800 - P4 1.3 MHz processor
1.2 GB Ram
SATA CD/DVDR+W | SATA 160 GB hard disk
GeForce FX 5200 128 Graphics Card AGP

Any one have any clues? I might hook up the hard drive to test the hard disk to see if it's failing, however i doubt the hard drive has anything to do with this. It's a liveCD. Also, when i boot up, sometimes it goes to X and it bogs out, or it will hang on a black screen and linger until i BKSP+CTRL+ALT the screen; then i get segment faults, etc. Even when i was running with 1 RAM stick. I will test the hard disk tonight, see if i can get anything working, any suggestions would really help, please!

Thank you.

---

### Post by livestockPimp on 2008-08-23
have all the ram installed and from the ubuntu livecd there is an option for "memtest" run this and let it go for at least 20 mins (preferably an hour or 2) if you have corrupt ram then it could easily be causing issues.

if there are ANY errors replace the offending RAM stick.

---

### Post by crashovaride on 2008-08-23
livestock,

     Your info is definitely pimpin'! They sold me some bad **** i got a whole page of errors on the first 2 minutes! I will look into this and try to get this fixed. Thank you a million times over dude. You have no idea how much crap i went through with this. Seriously, thanks!

Kindest Regards.

---

