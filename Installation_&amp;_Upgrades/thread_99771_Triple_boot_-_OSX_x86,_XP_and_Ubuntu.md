---
title: "Triple boot - OSX x86, XP and Ubuntu?"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by urbanamc on 2005-12-06
Hello,

imagine  I had a HD with OS X x86 on one partition, XP on a second and then an empty third partition.

If I install Ubuntu on the third partition would the GRUB bootloader recognize the OS X x86 install, it would obviously see the XP install.

Thanks :)

---

### Post by danne on 2005-12-06
I can't promise you anything, but if it is an empty partition, why not just try it...? you'll notice it before he actually installs it so it's not going to harm or affect your system....and a ubuntu install is done in 15 mins ;-)

---

### Post by urbanamc on 2005-12-06
I'll have to imagine giving it ago ;)

---

### Post by cdhotfire on 2005-12-06
I don't know about recognizing it but you can surely add it,
```

$ sudo gedit /boot/grub/menu.lst

``` 
Look where it says
```

............
## ## End Default Options ##
............

``` 
Then add something like this under that
```

title MacOSX
 root (hd0,1)
 chainloader --force +1
``` 
change 1 to your partition, in (hd0,1).

Then just reboot.:rolleyes:

If you have any more trouble check this page out.
[http://wiki.osx86project.org/wiki/index.php/Install_On_A_Partition_Simple_And_Accurate](http://wiki.osx86project.org/wiki/index.php/Install_On_A_Partition_Simple_And_Accurate)

---

### Post by cdhotfire on 2005-12-06
[quote=cdhotfire]I don't know about recognizing it but you can surely add it,
```

$ sudo gedit /boot/grub/menu.lst

``` 
Look where it says
```

............
## ## End Default Options ##
............

``` 
Then add something like this under that
```

title MacOSX
 root (hd0,1)
 chainloader --force +1
``` 
change 1 to your partition, in (hd0,1).

Then just reboot.:rolleyes:

If you have any more trouble check this page out.
[http://wiki.osx86project.org/wiki/index.php/Install_On_A_Partition_Simple_And_Accurate]("http://wiki.osx86project.org/wiki/index.php/Install_On_A_Partition_Simple_And_Accurate")[/quote]

Im hoping of doing this myself, after my tiger finishes dling.:???:

---

### Post by urbanamc on 2005-12-06
thanks, looks good info I'll give it ago!

---

