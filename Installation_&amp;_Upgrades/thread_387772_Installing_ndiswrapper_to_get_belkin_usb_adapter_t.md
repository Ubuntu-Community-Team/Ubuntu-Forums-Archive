---
title: "Installing ndiswrapper to get belkin usb adapter to work"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by avenger421 on 2007-03-18
hi, im very new to linux and im trying to get my belkin wireless G+ USB Adapter (F5D7051) to work

i was trying to follow a guide to this and found i first had to install ndiswrapper, tried to do this by following another guide. It told me to navigate with the terminal to the folder then put "make install" did this and got this error:

> adam@adam-desktop:~/ndiswrapper-1.38$ make install
make -C driver install
make[1]: Entering directory `/home/adam/ndiswrapper-1.38/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/adam/ndiswrapper-1.38/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
echo /lib/modules/2.6.17-10-generic/misc
/lib/modules/2.6.17-10-generic/misc
mkdir -p /lib/modules/2.6.17-10-generic/misc
mkdir: cannot create directory `/lib/modules/2.6.17-10-generic/misc': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/adam/ndiswrapper-1.38/driver'
make: *** [install] Error 2


please help? im using 6.10 edgy btw

thanks in advance

---

### Post by vayde on 2007-03-18
The howto you are following is having you compile ndiswrapper.  It's possible, but not necessary.  There is a binary package already in the repository just waiting for you.

Open up a terminal and type the following:

```

sudo apt-get install ndiswrapper-utils

```

That will install ndiswrapper, assuming you have the repositories enabled.

If it doesn't work, get back to us.

You can also contact us on freenode irc at #ubuntuforums-beginners.

Good Luck.

---

### Post by aysiu on 2007-03-18
If you don't yet have internet access, you can install *ndiswrapper* from the Ubuntu CD: ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```

---

