---
title: "Brother MFC-j615w"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by mv1962 on 2012-02-21
It's my first time at forum. I have a issue that maybe someone can help me
 I'm  not able print a document at my all-in-one Brother MFC-J615w(UBUNTU 11.10). It  seems to be connected, act as connected but doesn't print actually it is  missing driver. I already look unsuccessfully for drivers to download  at Internet. Looking forward for some help.

---

### Post by kurt18947 on 2012-02-22
Here are Brother's drivers:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J615W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J615W)

Even though it says to use CUPS if available,  you need both LPR & CUPS and you want to install the LPR .deb first.

Be sure to take a look here first if you're using a 64 bit distro.  Brother's printer drivers are 32 bit.  They work fine on 64 bit systems but you need to install the 32 bit libraries.  Also note that .deb & .rpm instructions are mixed.  Ubuntu users only need .deb info.  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004)
You may enter certain of the commands are get a message that it's not required.  That's fine, on to the next one.   # 5, 6 and 8 are required in 11.10 I believe.


If you install via the command line - required with 64 bit systems - you'll see some error messages, something to the effect of /var/something/ not found.  I ignore them and my printer still seems to function properly. 
There is a glitch in scanners in 11.10 & 12.04 so far.  Some files get copied to the wrong location.  Here's the fix for that:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

Also for a non-privileged user to use the scanner you'll need to do this:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

Good luck.  This all seems more complicated that it is once you do it once or twice.

---

