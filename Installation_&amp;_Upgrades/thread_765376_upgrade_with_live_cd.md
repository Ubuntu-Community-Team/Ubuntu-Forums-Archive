---
title: "upgrade with live cd"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by ubergeek2 on 2008-04-24
Hi,

I downloaded the 8.04 live cd, can I upgrade my 7.10 installation using this cd? or do I need the alternate cd?

thanks.

---

### Post by forkd on 2008-04-24
I believe you need to use the alternate CD.  When you insert the disk I believe it indicates it has found updates and asks if you want to upgrade.  

This info is old but is accurate.  [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by rseiler on 2008-04-24
Thanks for that tip. With the Alternate CD I was able to use:
gksu "sh /cdrom/cdromupgrade"

But a question: If you can install Ubuntu fresh with the Desktop CD, why can't that same CD also be used for an upgrade?  I assume it's because the files are in a different format for some reason (one for clean, one for upgrade), but why is that?

---

### Post by ptcbus on 2008-04-24
Upgrade requires an alternate cd. For the steps see: [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by rseiler on 2008-04-25
Yes, that's been mentioned, but it still kind of begs the question I asked above.

---

### Post by MightyMe on 2008-04-25
Just a tip. I upgraded with the alternate CD by booting into Gutsy, inserting the CD and i got a pop-up with a third button to upgrade my system. Worked for me. This option was not available when inserting the dektop/live CD.

I agree, it shouldn't be too much of a problem to add the upgrade feature to the desktop CD. Maybe it's a size issue where the magic 700Mb is exceeded...?

---

### Post by Argus on 2008-04-25
I had the same question why does there have to be two CD's why can we do a CD upgrade with the live CD?

---

