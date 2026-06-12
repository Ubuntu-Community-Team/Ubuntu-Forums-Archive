---
title: "Installed Ubuntu 6.06.  Now can't start Windows"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by sdouglas949 on 2007-06-18
Today I installed Ubuntu 6.06 on my desktop.  I had Windows Vista installed on my primary hd and installed Ubuntu on my secondary drive (sdb)  Now there's no dual boot option for me to run Windows Vista.

I double checked to make sure Ubuntu was installed on the correct hd, and it is.

Any suggestions on how I can also run Windows on this machine?  Keep in mind I'm a Linux newbie.  I installed ubuntu on my laptop a little over a week ago (and it's working great!)

Thanks for your help.

Steve

---

### Post by tgoose on 2007-06-18
When in Ubuntu, if you go to the terminal and type

```
sudo gedit /boot/grub/menu.lst
``` (you'll need to enter your account password)

you should see some writing about Ubuntu. 

Underneath all of that, if you add

```

# Windows Vista
title Microsoft Windows Vista
rootnoverify (hd0,0)
makeactive
chainloader  +1

```

(hd0,0) changes depending on where Vista is installed. the first number is the hard disk number (starting at zero) and the second the partition number (again, starting at zero.) On any normal system with Vista pre-installed, (hd0,0) will work.

---

### Post by sdouglas949 on 2007-06-18
That did the trick! :)

Thanks for your help!

---

