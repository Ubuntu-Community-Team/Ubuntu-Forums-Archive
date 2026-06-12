---
title: "initrd-related kernel panics with fresh 7.10 alternate install"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by nonblock on 2008-04-15
I've installed Ubuntu 7.10 on an old AMD K6 machine with about 84M ram, using the "alternate" cd. Although it appeared to install successfully, the kernel panics after loading the initrd image.

With the default initrd I get:

  Failed to execute /init
  Kernel panic - not syncing: No init found. Try passing init= option to kernel.

Booting with the initrd.bak gives me:

  Kernel panic - not syncing: Attempted to kill init!

Using the initrd.gz from the install CD it boots the default kernel ok, but into the install sequence of course.

Could mkinitramfs have generated corrupted initrds? TIA.

---

### Post by dstew on 2008-04-17
Not enough RAM, I think.

---

### Post by martrn on 2008-04-17
From:
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

I think if you are installing ubuntu on a low spec system you have to install a terminal enviroment first.  And be able to boot into a terminal.  If you have installed a full graphical enviroment, particularly gnome and KDE it will eat memory and use quite a lot of system resources.

From "Installalling an entire lightweight system":

You have to (I would say) :

Install a terminal enviroment.
IE select [Install a command-line system]
from the boot menu.

 Then :--
Install basic xwindows and a display manager
```
sudo apt-get install xdm
sudo apt-get install xorg
```

Then install your windows manager.
 -- just ONE of the following :-

```
sudo apt-get install openbox obconf openbox-themes
//  --  or  --
sudo aptitude install icewm iceconf icepref iceme icewm-themes
//  --  or  --
sudo apt-get install fluxbox fluxconf
//  -- or  --
sudo aptitude install xubuntu-desktop
```

and from there try your xwindows system.....
```
startx
```
I would thing your kernel panic is because something in init files is requireing too much resources.

---

### Post by nonblock on 2008-04-19
> **dstew said:**
> Not enough RAM, I think.

From what I've read though, 84Mb should be enough. "Installing Ubuntu on any system requires at least 32Mb of memory...you can expect a sparse Ubuntu system to boot to a graphical desktop on anywhere from 19Mb to 54Mb."

Are you saying the kernel + initrd by themselves inflate to over 84Mb?

---

### Post by nonblock on 2008-04-19
> **martrn said:**
> From:
[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

I think if you are installing ubuntu on a low spec system you have to install a terminal enviroment first.


I ended up building up the system from the other extreme, by starting with a debian netinst.

---

### Post by martrn on 2008-04-20
Hi, I hope or am glad you installed ubuntu on your system.  For me personally XORG + KDE Desktop infaltes to over or around 96MB, (or it is at the present time).

If you are installing on your system, installing xorg then a desktop, you will find out where it fails, and then install a less resource hungry desktop.

---

