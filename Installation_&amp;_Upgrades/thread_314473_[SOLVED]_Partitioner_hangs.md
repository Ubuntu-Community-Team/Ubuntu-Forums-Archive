---
title: "[SOLVED] Partitioner hangs"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by tipp98 on 2006-12-07
Hello all, I don't know where to start so bare with me. I have a Toshiba Satellite 4100XDVD(PII400MHz w/ 192MB RAM) that initially had win98 on it. Windows was crashing frequently and I've been wanting to start using Linux on all non-gaming PC's so I downloaded Ubuntu 6.10. The CD worked great on my old desktop PC but the installer would not start on my 4100XDVD. I flashed the DVD drive firmware but nothing. Then, I did some searching and found that I should be using the alternate install CD so I downloaded the ubuntu-6.06.1-alternate-i386.iso. The disk check fails, but it installed fine on my desktop(looks like two or three bad packages). I would download again but all I have is dialup. 

The installer loads fine untill I get to writing the partitions, where it freezes every time. I ran the IBM disk manager test and it found bad cylinders. It prompted me to do an erase disk to fix the errors so I did and the test no longer returns any errors. Still, the partitioner freezes. I've tried several different BIOS updates/rollbacks without effect. I run memtest86 and BAM!, gobs of error on tests 5,6,7,8(I ran this earlier but ignorantly dismissed the errors as strenuous testing, and not necesarily bad RAM). It looks like the laptop has 64MB of onboard RAM and a 128MB stick. I took out the stick and ran memtest again. Still getting bad blocks, I said "what the hey" and tried loading up the installer, which would not even start. I then put the stick back in and ran a test on the 64M-192M range and it made four passes without failing on any test.

Any suggestions or should I just pull out the ram and give it to somebody who can use it?

---

### Post by taurus on 2006-12-07
With 192MB of RAM, I recommend you use the Xubuntu alternate CD...  Ubuntu's going to be real slow on your machine then.

---

### Post by wpshooter on 2006-12-07
> **taurus said:**
> With 192MB of RAM, I recommend you use the Xubuntu alternate CD...  Ubuntu's going to be real slow on your machine then.


Use Xubuntu ALTERNATE, plus make sure that when you burn the ISO image to the CD that your burn at 4x or slower.

Then make sure that you test the integrity of the CD by running the verification check function that is found on the initial Ubuntu boot screen menu.

Good luck.

P.S. - However all this may not make any difference if your memory is bad.  Do a google search on memtest86+ and then download a copy to use to test the memory.

Also, you might want to consider getting the **KILLDISK** program to **WIPE** your drive completely clean.

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by tipp98 on 2006-12-07
Yes, I will use Xubuntu. I was initially under the impression that I could install it using my current disk. As you pointed out, regardless of what version I want to use or should use, it doesn't much matter if I cannot even get past the partitioning phase.

> plus make sure that when you burn the ISO image to the CD that your burn at 4x or slower.


Then make sure that you test the integrity of the CD by running the verification check function that is found on the initial Ubuntu boot screen menu.

I did 1x with my last CD and the Unbuntu integrity check did not fail to a bad burn but rather a bum download, as I used md5summer to check my .iso mounted under daemon tools which found that some files listed in the checksum file were simply missing. 

> Do a google search on memtest86+ and then download a copy to use to test the memory.

What advantages will this have over running the memtest86+ that is on the Ubuntu CD?

Is there a way to to tell Linux to only use the upper 128MB of memory. I've been trying to find information about badRAM but it doesn't look like I can do much without a funtioning install.

---

### Post by tipp98 on 2007-10-12
Lucky me, my dad had an identical laptop that I was able to install Xubuntu on. Unfortunately, Xubuntu does not support bad ram so I was forced into trying something else. I chose gentoo. Long story short, it was a rocky road getting everything to work, but I got it up and running on the laptop without bad onboard memory, applied the BadRAM patch, entered my error patterns into mm/page_alloc.c as per documentation, cloned the hard drive, and viola, I now have two functioning/stable laptops, albeit running gentoo, which I'm more than happy with.

---

