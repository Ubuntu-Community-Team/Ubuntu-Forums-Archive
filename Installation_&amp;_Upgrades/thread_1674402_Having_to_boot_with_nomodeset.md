---
title: "Having to boot with nomodeset"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by shinobilunchbox on 2011-01-23
Hey all, first post and in advance sorry for the Noobishness.

I recently installed Ubuntu 10.04 onto my computer. In order to get it to install, I had to boot with nomodeset, because I was getting "no signal input" Trying to install it regularly. Now everything is installed, and when I try to boot, I still get the "no signal input". The only way I was able to make this post, is by using the option of "Try ubuntu before you install" and booting with nomodeset.

Now Obviously I have done a little bit of research and discovered, it was because I have an Nvidia graphics card. What I need is a step by step guide to fixing this problem. This is my first time using ubuntu, and I would like to learn to use it and get the hang of it. Thanks in advance.

---

### Post by confused57 on 2011-01-23
Welcome to the forum & to Ubuntu, don't worry we were all "noobs" at one time.  I'll try to help, although I'm using mostly Ubuntu 8.04, which uses grub vs 10.04, which uses grub2.

If you're dual booting, you should see a grub menu at boot.  If you're not dual booting, I think you have to press shift(?) to get to the grub menu...someone else may be able to tell you for sure(for grub, it's the "esc" key).

Anyway, once you get the grub menu, make sure the first Ubuntu entry is highlighted, press "e" to edit.  Press the up/down arrows to highlight the kernel line, navigate to the end of the line, remove quiet & splash, then enter nomodeset.  Press ctrl+x to boot.  This should get you to the desktop, then you can System--->Administration--->Hardware Drivers.
Install the Nvidia proprietary driver, which should then allow you to boot your pc.

Someone will probably chime in if I've missed a step.

---

### Post by sikander3786 on 2011-01-24
Just to confirm that you need to press <Shift> key to get to the Grub menu. From the Bios screen, press and _hold_ down <Shift> key until you see the menu. All other steps as mentioned above by forum member *confused57*.

---

### Post by BicyclerBoy on 2011-01-24
What nvidia graphics card ?

This nomodeset is probably effecting the nouveau driver kernel module.

The nouveau is the default Ubuntu driver for nvidia but this driver module prevents the nvidia driver from installing.
This kernel mopdule is compiled into the kernel.

Search for **blacklist nouveau ** to find the exact details.

Blacklisting will have no adverse effects if you use the nvidia driver.
AFAIK nomodeset=1  (no kernel mode setting) is a performance problem for all graphics drivers.

---

### Post by smudgy on 2011-01-25
> **shinobilunchbox said:**
> Hey all, first post and in advance sorry for the Noobishness.

I recently installed Ubuntu 10.04 onto my computer. In order to get it to install, I had to boot with nomodeset, because I was getting "no signal input" Trying to install it regularly. 

Does this mean that to make nomodeset permanent one has to reinstall? :?:

grrrr...

I know at least 1 distro has an etc/sysconfing/kernel file you can edit to make the value NO_KMS_IN_INITRD=yes

then mkinitrd makes nomodeset permanent

Otherwise its a real bind to have to keep burrowing into the grub2 menu each time to make sure it loads..  :>(

---

### Post by sikander3786 on 2011-01-25
> Does this mean that to make nomodeset permanent one has to reinstall?

No. You can make that change permanent by editing your /etc/default/grub. But before we do that, we need to know about your graphics card. Which one is it?

```
lspci | grep VGA
```

Did you check for proprietary drivers under System > Administration > Hardware Drivers/Additional Drivers? If drivers are available, driver installation will sort out the issue itself.

**[COLOR="Red"]Edit:[/COLOR]**

This might help.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

