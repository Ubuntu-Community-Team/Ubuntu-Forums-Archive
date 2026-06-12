---
title: "creating partition for ubuntu on vista machine"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by salakhate on 2010-03-29
I crated unallocated space on vista disk using EASEUS partitioning software and installed ubuntu on it. I chose "use the largest free space" for ubuntu installation. Installation goes fine but only vista loads on restart...where is the installed ubuntu? 

Thanks in advance for any help!
YP

---

### Post by oldfred on 2010-03-30
It should have installed grub to the MBR of your drive. This was not a wubi install was it?

This will show your system:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by salakhate on 2010-03-30
NO, it was not WUBI install..i installed from CD.

---

### Post by salakhate on 2010-03-30
Couldnt solve the problem yet..anybody out there? any idea why ubuntu does not show up on boot??
Thnx!

---

### Post by LinuxTAd on 2010-03-30
Without much info to go on, I would suggest a reinstall. It is obvious that grub2 was not installed to the MBR. What is not obvious is why. 

 I would suggest a reinstall and to slow down and make sure that you choose the correct options. Also, if you have data on the system you do *not* wish to lose, I would suggest backing it up _before_ you continue. :)

Alternatively you could just re-install grub2 again as well, just check the wiki:
 [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Scroll down to "Recover Grub 2 via LiveCD"

Best of luck : )
Tom

---

### Post by salakhate on 2010-03-31
Thanks! Reinstall worked for me!!

---

