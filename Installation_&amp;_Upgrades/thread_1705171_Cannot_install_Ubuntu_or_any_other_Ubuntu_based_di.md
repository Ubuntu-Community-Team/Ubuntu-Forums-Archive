---
title: "Cannot install Ubuntu or any other Ubuntu based distro"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by danielkraak on 2011-03-11
I bought a new NVidia Asus EN210 for my HTPC, but I can't get Ubuntu to install. 

First I made a live USB disk of 10.10 with Unetbootin and when I choose the option of "try Ubuntu" it starts loading and then just hangs, still showing the menu of boot options. After this I tried Xubuntu on a USB disk. This one also starts loading but then just fails. I also tried XBMC Live. This one does show the Ubuntu 10.04 screen but then just shows a black screen.

After this I found a CD with Ubuntu 10.04, I think or it is 10.10, laying around in my room. I booted it and once I select an option from the install menu it starts to load, but then just gives a black  screen with a flashing "-" sign. 

The strange thing is, once I pop in the old video card, which is an ATI HD4350, my Ubuntu 10.10 Live CD on USB disk does work and it does get past the menu of boot options (in my second paragraph I describe how this isn't the case with Ubuntu 10.10 combined with my NVidia card).

I really hope someone can help me. I have been trying the whole day already.

---

### Post by Quackers on 2011-03-11
Welcome to UF :-)
This is a video problem, it seems.
When booting from the cd/usb, at the first purple screen (the one with the little ma icon at the bottom) press any key. Then choose your language and on the next screen press F6. Some boot options will appear bottom right. Try the "nomodeset" option first.

---

### Post by Rubi1200 on 2011-03-12
As Quackers pointed out, this is likely a graphics issue.

Try the nomodeset option when booting.

For more, see here:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by danielkraak on 2011-03-12
The CD turned out to be Ubuntu 10.04. With nomodeset I was able to boot the liveCD and install Ubuntu. However, when I boot it doesn't work. I get the following error: Pointer to BIT loadval table invalid. 

So I modified GRUB, like in the link above, by making it Ubuntu boot with the option nomodeset. After this Gnome doesn't launch and I just stay in the terminal. When I type in the commando 'startx' Gnome launches. But once in Gnome my network isn't working and I can't open hardware drivers because of that.

---

