---
title: "screen resolution"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by Ted Catchpole on 2005-05-09
I've just installed Ubuntu Hoary on my AMD64 machine, converting from SuSE9.1. 
During installation I set the screen (Philips Brilliance 109) resolution as 1280x1024, the same as I had on SuSE. But when I log in, I get 1024x768. If I try to change it using System -> Preferences -> Screen Resolution, the only options I get are 1024x768, 800x600 and 640x480.  Can I get 1280x1024 somehow?

Ted.

---

### Post by Xian on 2005-05-09
You could just reset X by issuing the command:  

$ sudo dpkg-reconfigure xserver-xorg

Or, you could review the /etc/X11/xorg.conf file and check that the listed monitor refresh rates are correct, and that the DefaultDepth resolution is set as desired.

---

### Post by Ted Catchpole on 2005-05-10
[QUOTE=Xian]You could just reset X by issuing the command:  

$ sudo dpkg-reconfigure xserver-xorg

Or, you could review the /etc/X11/xorg.conf file and check that the listed monitor refresh rates are correct, and that the DefaultDepth resolution is set as desired.[/QUOTE]

Great, thanks for the quick reply, Xian. I'll try it tonight as soon as I get home from work.   Ted.

---

### Post by Ted Catchpole on 2005-05-10
[QUOTE=Xian]You could just reset X by issuing the command:  

$ sudo dpkg-reconfigure xserver-xorg

Or, you could review the /etc/X11/xorg.conf file and check that the listed monitor refresh rates are correct, and that the DefaultDepth resolution is set as desired.[/QUOTE]

The command-line solution worked flawlessly. I now have the full resolution that the monitor is capable of. Thanks very much for this solution.

Ted.

---

### Post by ubuanu on 2005-05-10
Hi,

If somebody else has problems with Screen Resolution, there is a really good wikipedia page to solve the problem:
[http://www.ubuntulinux.org/wiki/FixVideoResolutionHowto](http://www.ubuntulinux.org/wiki/FixVideoResolutionHowto)

I found the chapter "undetected monitor specs" helpful after installing Ubuntu.

---

