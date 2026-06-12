---
title: "[SOLVED] Upgrade to 7.10 lost all monitor resolution settings"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by MacDuff on 2007-10-20
Just upgraded from 7.04 to 7.1 and my monitor resolution has gone to 800 x 600 with no options to change it.  When I tried to use "sudo dpkg-reconfigure xserver-xorg" it displays the first page of the reconfigure routine but I cannot make any selections/changes.

Can anyone suggest what I can do to get my screen resolution back to high res?

Thanks

---

### Post by Pumalite on 2007-10-20
If you have an ATI or Nvidia try ENVY: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by MacDuff on 2007-10-21
Well I did install Envy and it did work, sort of.   After the first install, it provided me with resolutions that are within the range of my 22" LCD monitor to display but screen fonts were quite ragged with parts of the characters dropped out.

Since I have an on-board video chipset which from the box the MB came in,Ii take to be Nvidea GeForce 6100, I thought I would try to use Envy to install the drivers manually.  Long story short, I now have destroyed my monitor display.  On boot-up I get a message that screen resolution is not supported and cannot get into the system to try some other settings.

I know that there must be a way to force load of generic, low-res drivers on Ubuntu start-up but I do not know the secret.  Can you advise me how to restore some sort of monitor display?

Thanks

---

### Post by MacDuff on 2007-10-21
Found a method of installing Nvidia driver from command line in Community Documents.

The problem "dropout" on screen fonts was fixed by increasing the frequency of the monitor display.

---

