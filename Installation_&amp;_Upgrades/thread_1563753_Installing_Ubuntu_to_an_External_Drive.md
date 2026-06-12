---
title: "Installing Ubuntu to an External Drive"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by Experimental on 2010-08-29
I tried to install ubuntu to my external hdd like I install it to a internal hdd nut I have a serious problem. When I plug out the usb drive and restart pc it says "Grub not loaded" and I can't go further than that. How can I solve that problem

---

### Post by oldfred on 2010-08-29
Boot Problems:Computer does not boot without external drive

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by Experimental on 2010-08-29
Thanks dude that helped me a lot. Another quick question. Can I duplicate ubuntu from one external to another ?

---

### Post by howefield on 2010-08-29
Clonezilla will help you, as long as the destination drive is equal or larger than the source.

clonezilla.org

---

### Post by oldfred on 2010-08-29
While you can use clonezilla or remastersys if you want I just believe in another install. You can then just copy /home and you can create a list of installed apps and reimport them.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

I installed to my desktop but knew I wanted to install to my portable and then install the beta also. So I did as much configuration from command line as possible and copied a list of commands using history to make a bash file to do 90% of a new install.

---

### Post by C.S.Cameron on 2010-08-29
You can clone Ubuntu from sda to sdb using ```
dd if=/dev/sda of=/dev/sdb
```

if sda is bootable sdb will be also.

sdb > sda

The process takes hours with a large drive and there are no blinking lights to show it is working.

For more info:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Experimental on 2010-08-30
Actually I will buy a larger capacity external and I don't want to install and update everything again and again into it. Doesn't linux have something like that. In machintosh when I install another leopard into external ,at the end of the install it asks me "do you want to import anything from another... " and when I choose import from the computer that I use, it imports completely everything and it doesn't require me to do anything. I'm asking possibility of this. Can clonezilla do that ?

---

