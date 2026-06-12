---
title: "Fiesty and a &quot;new&quot; nvidia"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by thevictor390 on 2007-11-14
So I haven't used Ubuntu for a while, and recently I upgraded to an Nvidia Geforce4 MX 440 for a little more performance in Windows.  However, the gui seems to be completely broken now in Linux.  I get a command prompt only and can log in, but that's it.  dpkg-reconfigure xserver-xorg only tells me it doesn't recognize the dpkg-reconfigure command.  So I somehow need to install drivers or reconfigure xorg in the terminal (which I am mostly unfamiliar with).  I also have no idea how to use vim, if that is needed.  

This is on Feisty, as I said I haven't booted Linux for a while so I haven't upgraded yet.  I would like to do that from Ubuntu so I don't lose my settings or have to burn a disk.

---

### Post by confused57 on 2007-11-15
> **thevictor390 said:**
> So I haven't used Ubuntu for a while, and recently I upgraded to an Nvidia Geforce4 MX 440 for a little more performance in Windows.  However, the gui seems to be completely broken now in Linux.  I get a command prompt only and can log in, but that's it.  dpkg-reconfigure xserver-xorg only tells me it doesn't recognize the dpkg-reconfigure command.  So I somehow need to install drivers or reconfigure xorg in the terminal (which I am mostly unfamiliar with).  I also have no idea how to use vim, if that is needed.  

This is on Feisty, as I said I haven't booted Linux for a while so I haven't upgraded yet.  I would like to do that from Ubuntu so I don't lose my settings or have to burn a disk.
You can try:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
sudo nano xorg.conf
```
that's an uppercase X and (one)(one)

page down to the section for you video device, change the driver to "vesa" or "nv" might work with this card...include the quotes in your driver entry.  The "nv" driver will give much better performance than "vesa", until you can install "nvidia" drivers.

Ctrl+X, y, enter...this will save the changes.

You'll probably need to reboot(sudo reboot) or you can try:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

