---
title: "Trouble Compiling Smartlink drivers in Feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by dckirba on 2007-04-21
Hello Everyone :)

Hope you're all having a great weekend. I installed feisty at home (going up from previous install of dapper) from an alternate CD last night.

Got most things working, was a little confused by my two IDEs showing up as sda and sdb, but all is normal. Had one issue though were fsck would run every time I booted and find some errors on my first harddisk (windows one), but then that was fixed after playing around with fstab. 

So all in all, feisty is beautiful and I love it... my only problem being I can't compile my modem drivers.

I use a modem that is identified as smartlink my scanmodem. I followed instructions on the wiki howto while using dapper and had it running great. 

Now when I try to compile things I need for the driver I get a make error.

```
david@ChomonKora:~/Desktop/ungrab$ sudo make
make modules -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/david/Desktop/ungrab
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/david/Desktop/ungrab/ungrab-winmodem.o
/home/david/Desktop/ungrab/ungrab-winmodem.c:14:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/david/Desktop/ungrab/ungrab-winmodem.o] Error 1
make[1]: *** [_module_/home/david/Desktop/ungrab] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2
david@ChomonKora:~/Desktop/ungrab$ 

```

I have installed build-essential, kernel headers and gcc (nice having an alternate CD, even got the NVidia drivers all done in one go!).

I get a similar error while compiling the modem driver. I need ungrab-winmodem installed before I install the driver so I can't go beyond this step.

Any help would be greatly appreciated because I would truly like to log off windows right now and pl;ay with my shiny new feisty :)

Cheers and have a good one,
David K

---

### Post by dckirba on 2007-04-23
Solution found:

[http://ubuntuforums.org/showthread.php?p=2518977#post2518977]("http://ubuntuforums.org/showthread.php?p=2518977#post2518977")

Feisty setup in less than three dyas!!! I&#7743; a happy man :)

Cheers,
David K

---

