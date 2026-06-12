---
title: "Couldn't get a file descriptor referring to the console"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by sataylor56 on 2010-11-12
I have a Soekris 5501 on which I was able to install 9.04 server. This is a small system I want to use as a web server. It boots over the serial console. All was working fine until I upgraded to 9.10 using the network method. Now the serial console reports "Couldn't get a file descriptor referring to the console" at the very beginning of the boot process. Then it continues to boot but when it gets to "Starting Apache2" the console output stops and I can't login. I can, however, access it from ssh and can login just fine. Also, Apache is up and running as I can access the box with a browser. It's just the serial console port that has broken. As far as I can tell, all the stuff I had to do when initially installing Ubuntu to get the serial console working is still there and has not changed so I don't know what else needs to be done to get it back in operation.
Thanks,
Steve

---

### Post by sataylor56 on 2010-11-15
Not having gotten any help on this, I tried a fresh installation of 10.04 server. This time the serial console port worked fine, but the ethernet port didn't work. I looked this problem up on the web and found that other people have had this same problem. I wasn't able to find a solution, so I reinstalled 9.04 and now all is well again. Now I am hesitant to even try an upgrade. I think I'll save a disk image before I do anything else so that it will be easier to get back to this point. Maybe I will just leave well enough alone.

---

