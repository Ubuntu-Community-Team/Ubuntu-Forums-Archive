---
title: "Xubuntu install error"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by dluu13 on 2008-04-20
Hi everyone,

I have this old computer with 768MB RAM and a PIII CPU, and I wanted to dual boot some stuff on it.

Anyways, I have Windows 98 installed on it right now, and I want to put Xubuntu on it as well.
I've downloaded an image file of the Xubuntu 7.10 from the site.

I've burned it onto a disk, and no matter what option I choose at the startup menu for the live CD, I get a little dialog popping up with a red title bar saying that I have an I/O error.  The message is Error reading boot CD and the only option is to reboot.

In the corner of the screen there seems to be this string of hex digits that says 3242009F.

Other info:
The ISO file is 566MB and all the stuff on the CD is also 566MB.

I can't really think of any other information that I should include.  Just ask me if there's anything else needed.

EDIT:  I don't think it's my drive that's broken.  All the other ubuntu live CD's and windows CD's work with no problem.  Also, I've burned two xubuntu disks and they both do not work.

---

### Post by NightwishFan on 2008-04-20
Likely the disc was burned at too fast speed. Test the md5sum of the iso and if it matches burn on a cd-r and at slowest speed and check burn for errors. If you still get error download a new iso. Make sure to check for errors on cd before you attempt an install. It could be the harddrive but thats unlikely. Also make sure you got the 32bit version.

---

### Post by Pumalite on 2008-04-20
Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less on CD-R, check CD integrity after burn and before install.

---

### Post by dluu13 on 2008-04-20
Oh,thanks

I'll go try that.  I'll report back when I'm done.

By the way, how exactly do I check the md5sum?

---

### Post by Pumalite on 2008-04-20
[http://etree.org/md5com.html](http://etree.org/md5com.html)
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

### Post by NightwishFan on 2008-04-20
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by dluu13 on 2008-04-20
Whoa, it works now.  Thanks for helping me with this problem.  Now all I have to do is install this.

---

### Post by NightwishFan on 2008-04-20
Good luck, and enjoy. Ask if you need further assistance. :popcorn:

---

### Post by Pumalite on 2008-04-20
Happy Ubuntuing!

---

