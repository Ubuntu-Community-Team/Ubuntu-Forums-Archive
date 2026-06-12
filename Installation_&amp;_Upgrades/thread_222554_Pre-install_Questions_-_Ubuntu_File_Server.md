---
title: "Pre-install Questions - Ubuntu File Server"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by virtualy on 2006-07-25
I need more data storage.  I want to put together a box of unused parts (running Ubuntu), connect it to my home network, and access it for data storage and retrieval.

Old parts:
AMD K7700 (700 MHz) on unknown mobo (100 MHz Bus)
ATI 128 rage AGP video card
generic NIC
Apple Express Base station
various HDs
No dedicated monitor but expect to use a TV for set up

Current Network:
Belkin wireless G hub/router
Windows XP desktop
Mac OSX laptop

First question: is this even feasible?
Do I set up the Ubuntu box as a desktop or server (or does it matter)?
Once set up, can I administer the Ubuntu system from elsewhere on the network (with the XP, or Mac, or both)?
I'm assuming I need Samba for this to work with XP - is there anything special needed for use with the Mac?
I *may* eventually install MythTV and use the box as a DVR.  If I change (or add) video cards in the future, how difficult is it to reconfigure Ubuntu?

Lots of questions (and probably more to come).

Thanks.

-Paul

---

### Post by ahallubuntu on 2006-07-25
Googling the K5, it looks like the fastest speed is about 166MHZ.  The Motherboard disk controller is most likely ATA/33 at best.  The memory is probably limited to 64MB but it depends on the motherboard.

I'll bet you could install Ubuntu on this, but it would be pretty slow going.  You would probably be disappointed in the performance.   

Have you tried to obtain a faster "slow" computer?  I'll bet you could get one for little or nothing.  Case in point:  Someone gave away a Cyrix 333MHZ (Pentium II 250MHZ equivalent) with 192MB of RAM a year ago on Craigslist and I grabbed it.  Had Windows ME on it that was corrupted but otherwise the hardware worked great.  Runs Ubuntu OK, would probably work modestly well as a slightly slow file server, I haven't tried it.  So, I'll bet you could find something like that that is much faster than your ancient K5 system.

---

### Post by virtualy on 2006-07-25
Endless apologies.  I just took the old box apart and discovered the processor is actually an AMD K7700MTR51B A.  (I've modified my orginal post)

This is a 700MHz chip on a 100MHz Bus mobo.

BTW, there is 512 MB of PC100 RAM.

Sorry for the posting error.  Thanks for your reply.

--P

---

### Post by jacrider on 2006-08-03
You should be fine.

I built a file server recently with a slightly bigger spec machine and it runs beautifully.  (P111 933MHz 133 fsb, 768MB RAM)

I used the 40GB hard drive that was in the machine as the drive for the OS.  I installed Ubuntu Server.  I installed the LAMP version, then decided to install Gnome to make it easier for me.

I set-up samba to allow it to act as the file and printer server.  I used very simple samba configuration settings.  Worked first time.

Then I added two identical drives and set them up as a RAID 1 array (the two drives are mirrors of eachother) for safe data storage.  A bit of work, but not too hard.  Now works beautifully.

I have several XP machines on the network for my kids that now have their "My Documents" folders located on the server.  My wife's Mac has access, she stores documents on the server and we back-up her iPhoto directory on the server.

Really successful implementation.  The box was an old one from one of the kids.  All I had to add was the two drives at $60 each to make it all work.

---

