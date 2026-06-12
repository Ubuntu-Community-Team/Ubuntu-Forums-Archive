---
title: "Where is menu.lst?"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by bod720 on 2010-06-08
Hello,
I had 9.10 installed using Wubi, and upgraded to 10.04. 

My problem now is that when I go to load up Ubuntu (via. GRUB Bootloader) it says "Error: You need to load the kernel first"

I have searched for a while to try and get this fixed, coming very close: I just don't have a menu.lst file anywhere in my files! (Accessed files via. [this method]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?"))

Any help in editing the menu.lst file is appreciated!

Regards,
-Rob

---

### Post by mörgæs on 2010-06-09
I have not used Wubi, just regular Ubuntu installs, but I guess that this applies to Wubi as well:


In 10.04, Grub has been replaced by Grub 2, and menu.list is now grub.cfg

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

