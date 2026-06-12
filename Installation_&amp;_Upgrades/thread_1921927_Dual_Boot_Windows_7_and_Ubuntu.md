---
title: "Dual Boot: Windows 7 and Ubuntu"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by magh-87 on 2012-02-07
Hey folks,

So I've recently come back to Ubuntu and I'm running the latest, 11.10. I have noticed that there's quite a bit of changes since the 9.04 I last used.

The biggest thing for me that I've noticed so far is that I am now having trouble selecting dual-boot options. It used to be as simple as editing menu.lst but from what I gather, that's no longer there (though I seem to have created that file.)

What is the correct method of setting up machine to dual boot W7 and Ubuntu? By default Ubuntu will load first, but I need that changed to W7 for my girlfriends convenience.

Good to be back

---

### Post by WariusBirde on 2012-02-07
I'd just install W7 and then use the Windows Ubuntu installer for your gf's machine. [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Hope that helps!

---

### Post by oldfred on 2012-02-07
If you have everything installed, you just need to edit a grub file.

Manual way:
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Gui way:
HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by efflandt on 2012-02-07
One way to have grub default to whatever was booted last is to use **sudo nano /etc/default/grub** or **gksu gedit /etc/default/grub** and comment out the first line below with **#** prefix, and adding the following 2 lines:

```
#GRUB_DEFAULT=0
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```Then do **sudo update-grub**

---

### Post by magh-87 on 2012-02-07
> **efflandt said:**
> One way to have grub default to whatever was booted last is to use **sudo nano /etc/default/grub** or **gksu gedit /etc/default/grub** and comment out the first line below with **#** prefix, and adding the following 2 lines:

```
#GRUB_DEFAULT=0
GRUB_DEFAULT=saved
GRUBSAVEDEFAULT=true
```Then do **sudo update-grub**

What if I don't want it to boot what was loaded last and always boot Windows? I know how to boot into Ubuntu but she's not going to want to bother with selecting W7 in the selection list

---

### Post by magh-87 on 2012-02-07
> **oldfred said:**
> If you have everything installed, you just need to edit a grub file.

Manual way:
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Gui way:
HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

So it's taken me a while to finally get this installed.. where do I go next to prioritize W7 over Ubuntu?

---

### Post by Mark Phelps on 2012-02-08
I believe there's a menu option that says Preferences.

Click that and you will find a feature for setting the default boot.  Select the entry that says something like Windows 7 (Loader) ...
Save the results.

When you reboot, Win7 will then be the default boot selection.

---

