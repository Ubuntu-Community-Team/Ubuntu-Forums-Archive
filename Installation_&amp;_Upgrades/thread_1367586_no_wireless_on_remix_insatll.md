---
title: "no wireless on remix insatll"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by jmaddox on 2009-12-29
Installed netbook remix within windows xp on a new Dell mini v10. I have no wireless connection. Can't even figure out how to see if the wireless card was installed or not. Any ideas?

---

### Post by phillw on 2009-12-29
Hello and welcome to the forums.

One of the most common causes for dell minis not to like wireless is because of the broadcom wireless chip. 

> sudo apt-get install bcmwl-kernel-source
 
Then System --> Administration --> Hardware Drivers and install the broadcom driver that is there. I now am connected to the internet wirelessly.Should that not get you running, there is a Dell area over here --> [http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

They're more 'up to speed' with ubuntu & dell.

As you say "within windows" I'm assuming you chose the Wubi installation - If you can put that as a tag or as an opening comment - it's easy for us to miss & is quite important !!

Regards,

Phill.

---

### Post by jmaddox on 2009-12-30
Hi Phil,
I didn't use the wubi installer. I used the full iso and installed it in xp.
Jack

---

