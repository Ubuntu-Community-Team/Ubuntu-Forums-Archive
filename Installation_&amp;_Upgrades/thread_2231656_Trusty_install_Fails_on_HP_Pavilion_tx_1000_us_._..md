---
title: "Trusty install Fails on HP Pavilion tx 1000 us . . b43 error, and System Lockup"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by JeQhdMD on 2014-06-27
Hello,

I'm trying to install Ubuntu 14.04 on a friends laptop.  The laptop is an HP Pavilion tx1000us with 2 gb ram, and running a older version of nVidia (not sure which).   The install seems to go normal and I see the initial login screen and Unity desktop.   After about 10 seconds or so, the mouse pointer totally freezes, and therefore I can't get to the System Settings application / Software & Updates to install the proprietary nVidia drivers.   The trackpad and keyboard also seem disabled, so I am not sure I can access a terminal session to try a manual install of the drivers.

Is there a way to get this driver installed - - can I do something as the system is booting up and before the system freezes up?   If there is a way, I'd also appreciate info on the CLI text to use to do the install . . . sudo apt-get install nVidia b43 . . . ????

As info, after trying the 32 bit, and 64 bit DVD's with the same results (2 or 3 times), I did succeed in installing Linux Lite v2 (based on Ubuntu 14.04) and it installed perfectly (no gpu issues).  My friend prefers the Unity DE over XFCE (if that's do-able).

Thanks.

---

### Post by Bucky Ball on 2014-06-27
*Thread moved to **Installation & Upgrades**.*

To improve your chances of getting support please post in the appropriate forum section. ;)

Boot the machine and when you are at the grub list where you can choose OS, select the Ubuntu kernel you want to run then press 'e' to edit. At the end of the kernel line which ends with 'quiet splash', or something like it, add 'nomodset', without the apostrophes. Ctl+X to save changes and boot. Any different?

If that works we can show you how to make the 'nomodset' change permanent (editing the grub line only lasts until reboot). Other option is to install the correct drivers if it works. Try updating then looking in 'Additional Drivers'.

PS: Also, at the grub list after boot, choose the recovery kernel (below the regular one). When you get to the options, choose 'Resume boot', the top option. Does that work ok?

---

### Post by JeQhdMD on 2014-06-27
Thanks Bucky re best place to post.

There is no grub screen at boot-up (to choose kernel or press e) . . . as Ubuntu 14.04 is the only OS - - so I see a screen that allows change of boot order and input of F10 to enter bios.  So, the system goes directly to the user login screen (where all graphics, mouse pointer, widgets, etc. work as normal.   After login the system consistently freezes.   I can use my "Parted Magic" CD to load that live OS, and then create another partition.  I can then load another distro (such as Linux Lite), and then do another install of ubuntu 14.04.   I assume then I will get a Grub screen so I can follow your suggestion.

What say you?

---

### Post by Bucky Ball on 2014-06-27
Okay, after the BIOS screen, start hitting 'shift'. That should bring up the menu. If it doesn't, try again. The timing must be just so. ;)

Don't worry about Parted Magic or installing any other OS for now. Incidentally, you can boot a Live DVD/USB, 'Try Ubuntu, and use Gparted to create partitions, etc. Then just install with the 'install ubuntu' icon on the desktop.

---

### Post by JeQhdMD on 2014-06-27
After one attempt at nomodset, it doesn't seem to have any effect (entered that as suggested, then f10 to boot to login).   System still locks up.   I'll likely just re-install Linux Lite tomorrow afternoon.   I personally like the XFCE desktop, and maybe this is a way to refresh my skills on it.

Thanks again.

---

### Post by Bucky Ball on 2014-06-27
I only use a minimal install with xfce4. Try it if you're game:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Don't choose what type of system you want when it gets there during install, hit ok and skip it. Once the kernel is installed, reboot and you should get to a menu. Choose Ubuntu and you will get a CLI to log in to. Once there, 'sudo apt-get' whatever you like, in your case:

```
sudo apt-get xfce4 xorg xfwm4 xdm synaptic 
```

... reboot, and that should get you started and refreshing those skills. Good luck, whatever you try. ;)

The less moving parts the better, I say!

---

### Post by yancek on 2014-06-27
> After one attempt at nomodset, it doesn't seem to have any effect 

Try "nomodeset" instead.  Not sure if this is your problem but that is the correct spelling of the parameter.

---

### Post by Bucky Ball on 2014-06-28
> **yancek said:**
> Try "nomodeset" instead.  Not sure if this is your problem but that is the correct spelling of the parameter.

^^^
This!

My mistake, sorry. Try again. Was wondering why that didn't work! :-k

---

