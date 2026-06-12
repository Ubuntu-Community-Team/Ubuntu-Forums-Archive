---
title: "Live USB 10.04.3"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by gentracer on 2011-12-21
I have created Live USB installs using Universal USB Installer 1.8.7.4, unetbootin-linux-565,and usb-creator-gtk (tried) for the Ubuntu 10.04.3 iso - both 64 and 32 bit.  ALL have failed to run with the error 'Unable to find device containing live media...' or something similar.  It appears to start Ubuntu (the splash screen with Ubuntu appears), but then just fails.  

I used usb-creator-gtk to create a live USB for 11.10, but HATE Unity so want to fall back to an earlier version.

I have tried with 'persistent' disk space and without, different sizes, etc.  ALL to no avail!

I'm trying to figure out if 10.04.3 will run efficiently/effectively on a new laptop, Dell Inspiron 17R, before actually installing it on that system.

Can a live USB be created for 10.04.3?

Thanks in advance!

---

### Post by gentracer on 2011-12-21
Update: exact error message is:

Unable to find a medium containing a live file system

df command has the following:

Filesystem    1024-blocks  Used  Available Use%  Mounted on
none             1501172    148   1501024    0%    /dev

---

### Post by xXQuadPolarXx on 2011-12-22
Yeah,

Your not the only one having this problem as I just posted a reply to a similar problem someone else is also having. I would really like to run Live CD with the USB myself as my 2nd PC doesn't have a CD/DVD drive or HDD in it right now & I prefer to use it in live mode so that it can be used by guests for the internet with no worries of them screwing up my Windows PC. If you figure this out please let me know also.

Thanks!

Happy Holidays!

:popcorn:

---

### Post by sikander3786 on 2011-12-22
First of all, make sure that the downloaded image itself isn't corrupt and might be causing the problem. Compare the MD5SUMs as mentioned here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the hashes don't match, you obviously need to download a new image.

Using UNetbootin or the Ubuntu's USB Creator has always worked for me.

BTW, can you browse your newly created USB stick and see what it actually contains?

---

### Post by gentracer on 2011-12-22
I didn't compare checksums, but I downloaded from two different sites myself and then allowed the unetbootin and USB-Installer to do their own downloads.  

I've used two different USBs thinking maybe they were the problem - they are the Cruzers but I removed the U3 stuff, formatted/erased them both and then allowed the USB creator (whichever one was being used) to also erase the disk so I feel pretty good that the U3 stuff isn't causing the problem.

In addition, I had used the 8GB USB previously with a 9.04 install and the 16GB one with the 11.10 install.

I can browse the USB - but haven't gone many levels deep - it looks to have the typical /bin, /usr, /sbin, etc. and the PATH is /bin;/usr/bin;/sbin.

I'm in the process of loading 9.10 and running the Ubuntu USB creator from there to create a 10.04.  I saw this suggestion elsewhere and thought it worth a try.

I've also been trying to find the original 10.04 (not the current 10.04.3) thinking that perhaps the .3 is where the problem is - any thoughts on that?

Thanks!

---

### Post by gentracer on 2011-12-22
Just to report - the 9.10 try didn't work either.  Error message is the same.  In the casper.log file, it also says:

/init:  line 1: can't open /dev/sr0: No medium found
/init:  line 1: can't open /dev/sdb: No medium found

I've tried creating the USB with and without persistent file, same results either way.

---

### Post by sikander3786 on 2011-12-22
Tried with different versions/ISOs, result = Un-successful.

Tried with different USB sticks, result = Un-successful.

I am not left with many options except that you should try using some other computer for creating the USB and see if that helps. If it still doesn't, try booting some other PC with the same USB stick and see if that narrows it down. Otherwise, Weird!

---

### Post by gentracer on 2011-12-22
Yep - that will be my next step, but not optimistic at this point.

---

