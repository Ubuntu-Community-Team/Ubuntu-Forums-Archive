---
title: "Upgrade worked, then next boot it DIED!"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by helpdeskdan on 2006-11-12
I was very concerned; I use a lilo setup that uses hda to boot sdb.  However, after upgrading, it worked - just had to fix the netscape thing. 

TILL... the next day when I booted up and it hung right after it finished mounting the scsi drives.  I hit return and I'm in initram er something.  Reboot, same thing.  Monkey trumpets!  

Highly doubtfull there is a fix, but thought it was worth a try asking - I don't want to reinstall.  If I DO reinstall, I shouldn't loose the items in my home directory, right?  (why would I?)  REALLY don't want to loose my email.  

(Sigh)  Probably best to reinstall, huh?

---

### Post by bulldog on 2006-11-12
I don't understand your situation completely,but is a reinstall of GRUB not possible?

---

### Post by helpdeskdan on 2006-11-12
Nope, GRUB will not work on my old clunker.  I have SCSI drives, but the computer will only boot off of IDE drives.  SO, I have to install Lilo to the boot block of the SCSI and I have system commander installed on a cheap IDE drive.  It works. 

Anyway, I can NOT figure out what happened.  It worked the first time!  Dang!  Now, it won't finish booting.  I mean, if X was broken I'd at least have somewhere to start, but what do I do here?!!

(Sigh)  Anybody had much luck with doing a clean install?  (Obviously I want to keep my home folder - don't want to loose my email)

-Dan

---

