---
title: "Reinstalling packages from a list?"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2010-11-21
So I have a list of packages that were installed on my old system (and I no longer have access to the old system to fix the list).

I've found that the list should look something like this:
```

xserver-xorg					install
xserver-xorg-core				install
xserver-xorg-input-all				install
xserver-xorg-input-evdev			install

```

But instead it looks like this:
```

xserver-xorg
xserver-xorg-core
xserver-xorg-input-all
xserver-xorg-input-evdev

```

Is there an easy way to still feed this into aptitude, apt-get, or dpkg so that the packages will reinstall? Or if not, is there a way to add the "install" keyword to the end of every line in the right place?

Thanks,
Dylan

---

### Post by sikander3786 on 2010-11-23
Assuming you know what you are doing, you can try these commands to install/re-install them.

```
sudo apt-get install xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
```

```
sudo apt-get install --reinstall xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
```

---

### Post by Quackers on 2010-11-23
Did you try something similar to this?

[http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

If you did, it may have gone wrong :-(

---

### Post by oldfred on 2010-11-23
I normally use the dpkg extract & reinstall.

I copied this from someone but never used it as I commented it out in my reinstall script. It does not look quite correct as I do not see the open of pkglist.txt as package. Someone who knows bash better may be able to correct it.

#If you have your own list in pkglist.txt:
#while read package; do
#    apt-get install $package
#done < pkglist.txt

Edit
The above 3 lines are correct as the link to the file pkglist.txt is the last command.

---

