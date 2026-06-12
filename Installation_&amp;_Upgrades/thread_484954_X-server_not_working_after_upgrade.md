---
title: "X-server not working after upgrade"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by Mikeinnc on 2007-06-26
I am running Ubuntu 7.04 and have been succesfully using the 2.6.20-16 kernel with Nvidia drivers on a 'GEForce4 MX Integrated GPU' and using Beryl as well. Last week, I performed a normal upgrade to software as a result of the indication that there were 'upgrades available'. Now I cannot boot into X using the 2.6.20-16 kernel. I get a message:

could not open /lib/modules/2.6.20-16-generic/volatile/nvidia.ko

However, if I reboot and choose the 2.6.20-15 kernel instead, everything works perfectly! The GUI appears and everything seems to be great - including Beryl!

Does anyone know if there have there been any reports that an upgrade last week caused problems with the Nvidia drivers?

Incidentally, I have downloaded and run Envy whilst in the 2.6.20-15 kernel to upgrade the Nvidia drivers to the latest version. It doesn't make any difference to the later kernel. though - it still will not boot into X.

Comments or fixes will be very welcome! Thanks.

---

### Post by dreadlord_chris on 2007-06-26
you need to reinstall you graphics drivers for the -16 kernel. After choosing that kernel from GRUB it probably drops you too a command line login - right? Log in. From there there's 2 things you can do:
1: rerun Envy - honestly, I'm not sure if it can be run from the command line - but if not, it will tell you:
```

sudo envy

```
If it runs just go through it and reinstall your drivers. If not you need to:
2. reset X's grahics driver to the default, log into your Desktop, and run Envy from there:
```

sudo dpkg-reconfigure xserver-xorg

```
leave everything the same except for the driver - choose **vesa**
Now you should be able to start GNOME:
```

sudo /etc/init.d/gdm start

```
After logging in run Envy from there (unless you already sucessfully ran it from the command line)

---

### Post by dabl on 2007-06-26
On mine, I have to use ```
sudo envy -t
``` to run envy in text mode.  GUI mode doesn't work for some reason.

---

### Post by Mikeinnc on 2007-06-28
Thanks guys! The sudo envy -t command after I'd logged in did the trick :D

---

