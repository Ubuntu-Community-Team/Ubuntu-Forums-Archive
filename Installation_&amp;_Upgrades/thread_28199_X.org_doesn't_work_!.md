---
title: "X.org doesn't work !"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by WalterSullivan on 2005-04-19
Hi,

I've finished to install my Ubuntu 5.04 Linux but, when I restarted the X.org server  doesn't work :(. I've looked the log and it seems that the system don't recognize the graphic board (Radeon 9100 128).
I cannot do anything, sigh, anybody can help me ?

---

### Post by StacyWebb on 2005-04-19
Follow  [this](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati)  Should solve your problems.

---

### Post by heimo on 2005-04-19
Ok... could you describe the problem in detail? Do you get any error messages (what errors do you see in logs?) and so on..
 
You can try to reconfigure the Xorg on command line like this:
```
 sudo dpkg-reconfigure xserver-xorg
``` 
 
If it's screen resolution related problem, check advice on this thread:
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")
 
If you could attach your xorg.conf and errors in log, that'd be nice.
 
EDIT: To test if it's about driver, you could change driver to vesa or vga in xorg.conf and try if that works at all.

---

### Post by WalterSullivan on 2005-04-19
I've modified the xorg.conf file with vega in the driver instance, and it works :) ( fiuuu )

---

### Post by heimo on 2005-04-19
[QUOTE=WalterSullivan]I've modified the xorg.conf file with vega in the driver instance, and it works :) ( fiuuu )[/QUOTE]

Well, at least now you can do something - like trying to figure out how to get ati drivers to work... :) (I assume ati driver is correct for your card) ... if you will. With correct drivers and 3D acceleration user interface will feel faster.

---

