---
title: "mixing debian and ubuntu--safe?"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by John Stoner on 2006-08-08
I'm trying to install slimserver on my new ubuntu dapper drake box.  I could not find a .deb through unbuntu or slim devices. I did find it on debian.

I added this line to my /etc/apt/sources.list :

deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) unstable main contrib non-free

(mixing protocols seems to work.)

My problem is, now it says it wants to update everything from libc6 on up, and I just don't want to screw up this box and start over. Should I proceed or should I just try a different archive?

---

### Post by Anduu on 2006-08-08
Don't do it!!!!
For the love of God noooooooooooooooooooooooooo.....!!!!

Seriuosly tho...this is a very bad idea.Chances are you will completely hose your Ubuntu install.***Never*** mix Debian repos with Ubuntus.

God I hope I'm not too late :(

---

### Post by John Stoner on 2006-08-08
aaack... figured out where the slimserver archive was... it's up on my box now. 

the line is deb [http://deian.slimdevices.com](http://deian.slimdevices.com) stable main

much less invasive.

---

### Post by Anduu on 2006-08-08
Yes ...much better ;)

It is alright to add those kind of repos...still be careful and keep a close eye on what kind of stuff it tries to update other than that specific app...not that it would but just in case.

---

