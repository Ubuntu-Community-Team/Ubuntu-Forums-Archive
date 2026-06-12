---
title: "Hardy Install - Buffer I/O error"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by puleen on 2008-04-25
Every time I boot he pc up with the x86 DISC to try and install Hardy, I keep getting this error after I select to Try Hardy from the Live CD.

[ xxx.xxxxxx] Buffer I/O error on device fd0, logical block 0


Where xxx.xxxx seems to be some number.

I keep seeing this lines appear and they keep going on and on....

Could this be something to do with my drives? Not sure how to troubleshoot these...

When I put in Gutsy CD, I don't have this happen and am able to boot into the Live version of Gutsy.

Any thoughts??

---

### Post by uranus65 on 2008-04-25
I'm pretty sure I got the same errors when I did the install.  For me, I just waited because I think it was checking out the hardware and looking for floppy drives - which I don't have.  After a while - 15 or 30 seconds maybe - the install program moved on with other hardware discovery stuff and continued installing.

---

### Post by puleen on 2008-04-25
I shall wait it out and see what happens.....

Thanks :)

---

### Post by puleen on 2008-04-25
I waited it out and after about 20-25 minutes, I get to a BusyBox prompt (initramfs).....

So far Hary 0, Gutsy 1.....

---

### Post by uranus65 on 2008-04-25
It sounds like you might want to try reburning a new CD.  It might be trying to read it and not finding what it is looking for.  Did you use a CD-R or a DVD-R?  I'm not sure if it matters.  I used a CD-R though.

---

### Post by puleen on 2008-04-25
I did burn a CD-R, shall try burning a new CD and see....

---

### Post by uranus65 on 2008-04-25
Sorry, I went and grabbed another beer.  I think you should burn another CD.

---

### Post by puleen on 2008-04-25
Nice....

I decided to download a new iso image all together... Download is at 91% so once that is done will burn it and see what happens... :)

Cheers! (no beers here)

---

### Post by puleen on 2008-04-25
The issue seems to be with HARDY itself, based on some of the other forum messages by users who experienced the same problem.

So long hardy....Hello Gutsy.... :)

---

### Post by juliocesargarcia on 2008-04-25
I think I have seen this error in the past when I burned the CD too "fast". Try burning at 24X. Maybe that will help. I plan to install this Sunday. I will be crossing my fingers until then.;)

---

### Post by jimoz on 2008-04-30
Have the same issue. No problem with hardware as I have previously installed gutsy via livecd (im using livecd again because i couldnt resolve networking issues- hoping hardy copes better). Tried messing around with ultra-dma settings which didnt make any difference. burnt another copy onto cd-r, initially was on dvd. dvd has buffer i/o errors, cd just hangs when it finishes loading the kernel then brings up an error after a couple of minutes. at the time of writing i usually aborted after about 15 minutes, so ill try again now and just leave it until something different happens.

---

### Post by hardyn on 2008-04-30
anybody know why its polling /dev/fd0?

Do you have floppy disk in your system?  do you have a floppy disk but disabled in bios? vice-versa?

if you have a floppy, what about removing it temporarily?

---

