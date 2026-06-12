---
title: "Disable Grub2 splash screen"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by nibal on 2013-03-13
I am in the long process of customizing and breaking a perfectly good, working Ubuntu installation. Hoping for some help in this pursuit.

After booting, grub will blank the screen, put up a short progress bar and end up in a login shell. Yes I am booting to a console in init 3.:)
I would like to see those booting messages in real time instead of these splashes. How can i disable  those screens?

TIA
Nikos

---

### Post by slickymaster on 2013-03-13
If you want to disable Grub2 splash scrren, just edit [B]/etc/default/grub
[/B]Run:
```
gksudo geany /etc/default/grub
```
and remove the _"quiet splash"_ from the linux command line.
After this run:
```
sudo update-grub2
```

Make sure you don't have plymouth-theme-ubuntu-text package installed.

In addition to this, if you want to see the kernel startup messages you'll probably want to remove the _"quiet"_ boot option too.

---

### Post by nibal on 2013-03-13
@slickymaster:
> In addition to this, if you want to see the kernel startup messages you'll probably want to remove the _"quiet"_ boot option too.

Where is that "quiet" boot option you mention?

Nikos

---

### Post by slickymaster on 2013-03-13
I apologize for not being completely clear in my previous post. What I meant to say is that the presence of the word **splash** in the ```
GRUB_CMDLINE_LINUX_DEFAULT
``` entry, enables the splash screen, with condensed text output. Adding quiet as well, results in just the splash screen, which is the default for the desktop edition since 10.04 (Lucid Lynx). In order to enable the _"normal"_ text start up, you would remove both of these.

---

### Post by nibal on 2013-03-13
> **slickymaster said:**
> I apologize for not being completely clear in my previous post. What I meant to say is that the presence of the word **splash** in the ```
GRUB_CMDLINE_LINUX_DEFAULT
``` entry, enables the splash screen, with condensed text output. Adding quiet as well, results in just the splash screen, which is the default for the desktop edition since 10.04 (Lucid Lynx). In order to enable the _"normal"_ text start up, you would remove both of these.

That's what i did in the first place. Unfortunately it didn't work as expected. The only thing removed was the Ubuntu Progress Bar, that lasted only 1 sec, anyway. Between that and the grub boot menu, there is a good ~20" that are blanked by a pink screen with nothing on it. This is mostly what I want to get rid off. Any clues?

TIA
Nikos

---

### Post by slickymaster on 2013-03-13
See if [this]("http://ubuntuforums.org/showthread.php?t=1958162&p=11842047&viewfull=1#post11842047") can anyhow be of help.

---

### Post by nibal on 2013-03-13
@slickymaster:
> See if [this]("http://ubuntuforums.org/showthread.php?t=1958162&p=11842047&viewfull=1#post11842047") can anyhow be of help.

No, unfortunately, this won't do it either. It simply uses themes to replace pink background with a black. I have no problems with pink, especially now that I have replaced it with an image.;) 
I just need to get the kernel boot messages underneath.

Thanks,
Nikos

---

### Post by cldunlap on 2013-05-10
> **slickymaster said:**
> If you want to disable Grub2 splash scrren, just edit [B]/etc/default/grub
[/B]Run:
```
gksudo geany /etc/default/grub
```
and remove the _"quiet splash"_ from the linux command line.
After this run:
```
sudo update-grub2
```

Make sure you don't have plymouth-theme-ubuntu-text package installed.

In addition to this, if you want to see the kernel startup messages you'll probably want to remove the _"quiet"_ boot option too.

---
It was mentioned to 'Make sure you don't have plymouth-theme-ubuntu-text package installed', could this be explained a bit more?  I would like to understand this a little better (before I remove it).  

Thanks!

---

### Post by slickymaster on 2013-05-10
**plymouth-theme-ubuntu-text** is a binary package in Ubuntu. Plymouth is an application that runs very early in the boot process, even before the root filesystem is mounted, that provides a graphical boot animation while the boot process happens in the background..
 This package contains the default ubuntu-text text theme used when no support for a graphical theme is found on your system.

---

