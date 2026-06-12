---
title: "Changing graphic card without full install?"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by eks on 2007-05-22
Hello,

I will be changing my graphic board tomorrow but I've already installed and configured lot's of softwares and wouldn't like to have to do a new install from scratch. I supose I won't have any problems if I take the following steps:

> 
. uninstall ATI drivers through Restricted Driver Manager (the same channel I used to install them)

. do a "sudo dpkg-reconfigure xserver-xorg" so x configuration is back to the default.

. take out the ATI and install the nVidia

. install the new drivers through...? Restricted Driver Manager? Or Envy?


And with that it shouldn't be problematic, right? Any other considerations I should mind?


eks

---

### Post by mikewhatever on 2007-05-22
I think it should work. Good luck.

---

### Post by eks on 2007-05-26
It did :)

I had just to run the reconfigure xserver on the command line after installing the nVidia card, otherwise X wouldn't load.

BUT... I'm trying to install the nVidia drivers now and I'm having some problems...

For starters, when I load the Restricted Drivers Manager it gives me:

```

Your hardware does not need any restricted drivers

```

Anyone have any ideas?


eks

---

### Post by Cows on 2007-05-26
just type the following:

```
sudo aptitude install nvidia-glx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-xconfig

```

After that just Ctrl + Alt + Backspace

---

