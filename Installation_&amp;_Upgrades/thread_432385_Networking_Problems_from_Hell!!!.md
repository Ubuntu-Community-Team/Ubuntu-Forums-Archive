---
title: "Networking Problems from Hell!!!"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by jack_teagarden on 2007-05-03
I got myself into a bind, again.
My Feisty boots slow, so I find this : "http://ubuntuforums.org/showthread.php?t=402452" (page 2),
and I edit my "/etc/rcS.d/S40networking" by copying over the section.
 I reboot, you know, and guess what? No networking!
I then copied the backup over it (/etc/rcS.d/S40networking) and still no dice
*Then* I get the *smart* idea to remake the link from /etc/init.d/networking
Still **nothing!**

  I have a windows box which I am using now, so I can use the internet sorta, but I really want my boo boo fixed!
I got in over my head!
Anything, anyone?

---

### Post by jack_teagarden on 2007-05-05
OK!
I figured it out.
I booted and ran "sudo /etc/rcS.d/S40networking restart"
and presto! it worked!

---

