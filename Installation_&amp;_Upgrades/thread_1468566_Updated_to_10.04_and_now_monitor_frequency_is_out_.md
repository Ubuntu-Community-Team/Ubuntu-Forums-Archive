---
title: "Updated to 10.04 and now monitor frequency is out of range"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by valtra on 2010-05-01
I just updated my Wubi install of 9.10 to 10.04 last night. Everything went well until it required me to reboot the computer. I rebooted, loaded Ubuntu from the startup list, and then the screen went blank and I got "H.V. frequency over range" on the monitor.

I can load the GRUB options, but recovery mode using the most recent kernel does not work. I am entirely unexperienced with using the terminal and command prompt options. 

Here's what I have attempted so far:

*$ sudo dpkg-reconfigure xserver-xorg*
this did not do anything, the command was not recognized

*$sudo nano xorg.config*
I don't even know what to do when I get to this screen :(

and I am about to try 
*$ sudo displayconfig-gtk*

Any help is really appreciated!
I have an ATI Radeon 9100 IGP card

---

### Post by kamikazepsi on 2010-05-01
on boot up menu, 

-hit "e"
-replace "quiet splash" with "nomodeset"
-hit ctrl + x

then install your restricted drivers once you get into your desktop

---

### Post by valtra on 2010-05-01
Thanks!!! That worked. How do I install restricted drivers though?

---

### Post by kamikazepsi on 2010-05-01
system > administration > hardware drivers

there's a good chance you'll run into a corrupted boot splash problem after this....if so, follow this guide:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by valtra on 2010-05-02
It says I have no proprietary drivers to install. I used Synaptic to install all ATI X.Org Xserver drivers. Will this be enough?

---

### Post by valtra on 2010-05-02
bump

---

### Post by valtra on 2010-05-04
Can anyone help me out? Can I make that "nomodeset" line permanent?

---

### Post by ppellet on 2010-05-05
> **kamikazepsi said:**
> on boot up menu, 

-hit "e"
-replace "quiet splash" with "nomodeset"
-hit ctrl + x

then install your restricted drivers once you get into your desktop


Thank you, These worked for me.
I have an old pc, but Lucid Lynx work faster than other in it.
Greetings from Chile.

.

---

