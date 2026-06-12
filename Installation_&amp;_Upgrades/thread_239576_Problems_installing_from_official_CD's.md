---
title: "Problems installing from official CD's"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by patleamon on 2006-08-19
I have 4 cd's of dapper drake, two are live cd's from the beta period (i386 and amd64, downloaded and burnt myself) and 2 are the official release that were sent to me (i386 and amd64, not burnt myself).

I get a crc error when I try to use either of the two official releases or the amd64 beta that I burnt myself.  It occurs when I select any menu item other than the memory test.  When using the amd64 beta disc I burnt myself I get an error similar to "Kernel panic- VFS: Unable to mount root fs on unknown block (1,0).".  I thought the live cd's ran on a RAM disc so I ran the memory test but haven't got any errors showing up after a few hours of tests. 

My system:
- Amd 64 x2 3800 (socket AM2)
- 1gb pc-5300 ddr2 3-3-3-12 ram (1 stick)
- SATA2 250gb hard drive 
- no usb drives attached
- sony dvd-rw 16x

I've got a pain of a download limit (2gb a month) so grabbing a new iso to test it out is going to be a bit difficult.

I have managed to run the beta live cd for i386 and have installed from there with no problems.  Still, I would prefer to be running the amd64 version.  The crc error seems to occur for a variety of reasons, and I can't seem to find any that match my situation or anything obvious that is wrong (seeing as the beta i386 cd works...).

---

### Post by em3raldxiii on 2006-08-20
This is a very odd problem indeed!  There have been a few other problems associated with the dapper 64bit release, but nothing identical to yours, as far as I know.  Having a 2GB d/l limit would be a serious crimp in my style - my condolences.
 
Now, as far as fixing is concerned.  A couple of strange options:  have you tried moving your ram to a different slot?  There doesn't seem to be anything special (from a problem POV) abotu your hardware, so I doubt that is the problem, unless there is something specific about your brand of motherboard.  Perhaps for the sake of some of the other troubleshooters here, let us know what sort of Motherboard you have.  It's entirely possible that there is a conflict there that hasn't been identified yet.
 
Also, from what I can tell, the newest point release of dapper (6.06.1 LTS) has a number of bugfixes over 6.06, particularly in the live boot / installation process.  They may have addressed your problems already.
 
I am interested in how this plays out, so please post here if you have made any movement toward a solution.
 
I believe that it is entirely possible for your RAM to pass the memtest, but for it to be in a timing or orientation that isn't friendly with Ubuntu.  I don't have any proof to substantiate that though.  I know I probably didn't solve your troubles, but at least I moved your post to the very top :D  Good luck!

---

### Post by patleamon on 2006-08-21
I'll try moving the RAM to a different slot tonight.  My motherboard is an [MSI K9N Neo]("http://msicomputer.co.uk/Products.aspx?product_id=703670&cat_id=77") based on the nforce 550 chipset.  Think it's running a rev 1.2 BIOS and nothing in their 1.3 looked like helping.

I'll see how persuasive I can be in getting someone else to download the latest install cd's for me.

Once the i386 version had installed I started playing with it some more, and had some errors installing other programs from CD (admittedly through wine which introduces a whole lot more room for error), but I'm thinking that the drive itself may not be 100%.  The cd's work fine on my laptop, though it's running straight windows.

Hopefully someone at work has a spare CD drive so I can check if that's the problem.

I've also tried twiddling my BIOS settings and jumpers on the drive but nothing has made any difference.  Tried some of the boot arguments (noapic etc) but with no luck.

---

### Post by wpshooter on 2006-08-21
Have you tried cleaning your CD drive lately ???

---

### Post by em3raldxiii on 2006-08-21
Indeed, it's not a particularly high-tech solution, but it's really worth a shot.  A can of electronics-approved compressed dusting gas could do wonders.  I'm not entirely convinced that this is the problem, but it certainly would be the most mundane ;)
 
If you were in the North Edmonton, Alberta, Canada area I would be willing to bring out a drive (considering I have 5 computers and 3 extra optical drives) ... Otherwise you might consider trying to get in touch with one of the local linux help groups in your area.

---

### Post by patleamon on 2006-08-22
Okay, tried swapping the RAM position and using the latest 6.06.1 CD and still have the crc error.  So there are a few options:
- Dirty/Dodgy CD drive.  It's only been out of the box for a week but I guess there could be some dirt in there.  Will grab a cd cleaning kit and give it a try if I can't find a drive to borrow.
- Bad RAM.  Not so sure this is it seeing as I've had no crashes/glitches running anything else so far.
- Bad motherboard.  Maybe the IDE connection is no good.  Could be anything.  

Whatever the problem is, it definately looks hardware related so I won't be asking these forums for more help.  I'll update this thread if I find a fix.

Thanks for your help.

---

### Post by patleamon on 2006-08-26
Looks like it is a dodgy drive - put in an old cdrom drive and it installs fine.

Now I have to convince the shop that their drive doesn't work (kind of) and they need to give me another one...

Edit: Drive must've been dirty - tried it on a different PC and it worked fine.  Put it back in my PC and now it works fine.  Guess the movement between PC's dislodged whatever was causing problems.

---

### Post by em3raldxiii on 2006-08-27
Eureka!!!  Well, I recommend going with a Plextor if you are buying a burner; for a standard CD or DVD drive, I dunno ... I always liked LG drives, but they're not exactly "top-of-the-line" ... never had one fail though :D

---

