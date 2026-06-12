---
title: "bcm43xx error during installation"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by brauer.erik on 2008-03-01
I am trying to load ubuntu on my computer, I keep getting the error message bcm43xx: error: Microcode "bcm43XX_microcode5.fw" not available or load failed.

This is during installation and it will keep repeating it.  Remember that Ubuntu is not installed.  I don't know what to do so it will install on my system.  I even did in vista is disable my wireless card but it still came up.

I would like to install it but I can't seem to get it going.  I actually don't use my internal wireless card but I use a express 34 card in my laptop instead.

Thanks
Erik

---

### Post by Herman on 2008-03-01
I have a laptop with that wireless card too but Ubuntu installs in mine okay.  Is your computer plugged in to the internet (wired) during installation?
Is the error stopping the installation process? Or can you just ignore it and continue anyway? That's what I would do if possible.

Regards, Herman :)

---

### Post by brauer.erik on 2008-03-01
It actually stops the installation, and I tried it plugged directly to the internet with the ethernet cable and without and it makes no difference.  The message will pop up and not quit for over 30 minutes

Erik

---

### Post by Herman on 2008-03-01
I am guessing probably it will be simple to get around that by using some boot parameters when you start the installation.
You might need to press F1 for help from the first screen in the installation to find out more.
I am already looking things up for you to try to find out exactly, but maybe you already know or you can find the right parameter faster than I can, and someone else can help as well.
I don't want to keep you waiting too long, so here are some of the links I'm looking in, you might like to take a look too, 
Links,
                                         [grumpymole: Ubuntu - How To Edit Grub Boot Parameters]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")

[The Linux BootPrompt-HowTo]("http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1")

More links on kernel parameters, 
                                         [10 boot time parameters you should know about the Linux kernel ...]("http://www.cyberciti.biz/nixcraft/vivek/blogger/2006/03/10-boot-time-parameters-you-should.php")
                                         [5.2. Boot Parameters]("http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html")
                                         [The Linux BootPrompt-HowTo]("http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html")
                                         [Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")
                                         [Kernel-parameters-2.6.11 - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Kernel-parameters-2.6.11")

We should be able to find the right boot parameter to make the wireless card get ignored until you finish the installation, later you can enable it if you want. 

Regards, Herman :)

---

### Post by Herman on 2008-03-01
I read a few more web pages and finished up on this one, [One step from getting wireless working on my Acer Aspire]("http://ubuntuforums.org/showthread.php?t=184033") - Ubuntu Web Forums.
I'm not very certain about this, I haven't needed to use boot parameters myself,  but I think this might help, if I understand correctly the pages I have been reading,
```
acpi=off
```
I hope I'm right, you can either do some reading to try to check or just try to start the installer with the option.
I don't know about the Ubuntu 'Desktop'  install CDs, but for the 'Alternate' CDs you press F6 before you boot the installer and it brings up a lione of boot options and you can type in your own at the end of that line.
You can try that or see if someone else can confirm or reject that idea. 

Also, Acer Aspire notebooks have a switch in the front with an LED lamp in it that you can press to turn wireless on or off,  it's not very obvious to see what it is. Whether that's on or off might affect things too, I'm not sure. 

Regards, Herman :)

---

### Post by Pumalite on 2008-03-01
[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

---

