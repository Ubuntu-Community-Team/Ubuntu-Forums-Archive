---
title: "problem burning 8.04 desktop CD"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by julianop on 2008-05-11
I'm having a lot of trouble burning a CD of 8.04 desktop. I've tried several machines and several speeds. The burns complete, but I keep getting verify errors.

It could be a bad batch of media, I guess, but I was half way down the spindle of 50 before I started this project, and hadn't lost one till now.

This is the first time I've ever had such problems, and I'm certainly no beginner. I'm using 700k media, not 650k, so i don't think that's the problem, but I don't know what else to try.

I'm mystified. Has anyone else had this problem?

It would be nice if I could install from the mounted ISO on my (cough! Suse 10) server via NFS. is that possible?

Thanks in advance.

---

### Post by evilc on 2008-05-11
What kind of CD burning program are/have you tried, you could also check the checksum if you haven't one do this:
1. Use FastSum or MD5summer to CREATE an md5sum of the ISO. (Note: an md5sum is sort of like a 'key')
2. Look at the file MD5SUMS that you will find at the bottom of the page from where you downloaded ubuntu or kubuntu
3. That file MD5SUMS will list a whole bunch of MD5 'sums' or 'keys'
4. Compare the md5sum you created with the one displayed on the MD5SUMS page.
5. If they're the same, your ISO is fine and ready for burning! If they're not the same, download again!

Hope that helps a little.

---

### Post by julianop on 2008-05-11
Thanks for the reply. Clive.
Yep, I know about MD5, and used md5sum to check the disks I burned. On several of them I got i/o errors as soon as it got to ./casper/initrd.gz.
I did a second d/l of the ISO, with similar results.
I just (as in "as I was writing this reply to you") tried another burn with a different brand of media - cracked open an old box of 12X Acers I had lying around - instead of the OfficeMax 52X ones I'd been running, and Bingo! I finally got a successful MD5 check.

Darn cheapo CD media, I guess. Serves me right ;-)

Thanks for your help, anyway, mate!

---

### Post by BoogieKnight on 2008-05-11
I also had similar problems... I was using Nero (within Windows) to burn and kept getting verification errors when i tested the CDs. I finally solved the problem by booting to my Ubuntu 7.10 partition and burning from there... worked like a charm.

I'm not sure why but Nero seems to give me bad Linux .iso burns more times then not. Everything else burns perfectly.

---

### Post by julianop on 2008-05-11
Yes, I tried Nero this time too, after getting bad burns using K3b my old trusty Suse 10.0 server. I was totally spooked when Nero failed on my XP box, because it's never failed me before (that I can remember, anyway). That's when I came cryin' to ths forum ;-)

Anyway, at this moment, Hardy is happily loading onto my old Gateway Solo laptop, which was the object of all this effort.

I'm new to Ubuntu, and I must say that - media aside - this has to be the simplest and most effortless Linux install I've ever done, and I've been doing them as far back as RedHat 5.1.

Thanks for your comments!

---

