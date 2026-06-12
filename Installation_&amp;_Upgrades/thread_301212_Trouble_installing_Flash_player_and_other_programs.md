---
title: "Trouble installing Flash player and other programs"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by ghindo on 2006-11-16
I recently installed Ubuntu 6.10 and am attempting to get it up to speed.  After fixing [this](http://www.ubuntuforums.org/showthread.php?t=300609&highlight=dpkg) problem, I'm finding another one:  when I attempt to install anything, the system gives me this error message:```
E: The package flashplayer-nonfree needs to be reinstalled, but I can't find an archive for it.
```When I attempt to install Flash, I get *this* error message:```
Could not open 'file name'

The package might be corrupted or you are not allowed to open the file.  Check permissions of the file
```

Any suggestions?

---

### Post by ghindo on 2006-11-17
Bump!

---

### Post by ghindo on 2006-11-18
bump!

---

### Post by appdx on 2006-11-18
try sudo

---

### Post by ghindo on 2006-11-18
> **appdx said:**
> try sudoThanks for the help, but I don't understand what you mean; could you elaborate please?

---

### Post by ghindo on 2006-11-20
*Someone's* gotta be able to help me. :(

---

### Post by almaddin on 2006-11-20
> **ghindo said:**
> Thanks for the help, but I don't understand what you mean; could you elaborate please?

what he simply means is: use a terminal
then use the commands: sudo apt-get update, followed by sudo apt-get install flashplayer-nonfree.

---

### Post by 20after4 on 2006-11-21
Try downloading the flash 9 beta from adobe labs. That worked a lot better for me than flash 7, even though it has a bug or two this beta is better than the ancient version.

---

### Post by rodent43 on 2006-11-21
i found easyubuntu an easy way to enable flash, java and codecs etc...it can be found here 

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

hope that helps for flash :)

---

### Post by ghindo on 2006-11-22
> **rodent43 said:**
> i found easyubuntu an easy way to enable flash, java and codecs etc...it can be found here 

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

hope that helps for flash :)This looks like what I need, but even after I follow the instructions to download easyubuntu, I get this message:```
The package might be corrupted or you are not allowed to open the file.  Check the permissions of the file.
```This message is very similar to what I get when I try to install Flash.

---

