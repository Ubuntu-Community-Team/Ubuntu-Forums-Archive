---
title: "BIOS won't install Ubuntu from USB"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by tandemrider on 2011-04-03
I'm almost completely new to Ubuntu. I have successfully installed  Ubuntu on my wife's desktop, and she likes it a lot. Now I wanted to  install it onto my new netbook instead of Windows 7 Starter, but I can't  get things to work.

Here's my situation:
Acer Aspire One 533 netbook

I put Ubuntu Netbook edition on a USB stick as decribed under [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download).

Once I boot from USB I get s short syslinux 4.03-message, and then a black screen reading Intel(r) PineView PCI Accelerated SVGA BIOS Build Number: 1818 PC 14.34 etc. etc. Everything stops right there.

I have upgraded my BIOS from 1.02 to 1.15  using the files supplied on the Acer website. That has worked, but I  still can't get system to boot from USB - thus no Ubuntu for me! :confused:

I have also retried everything having used UNetbootin to create the bootable USB this time, but to no avail.

From what I have gathered around the web there seems to be a problem with the BIOS supplied with these Acer netbooks, but I seem to be to inexperienced to understand the workarounds suggested.

Thanks for any help you can provide!

Tandemrider

---

### Post by Hedgehog1 on 2011-04-03
The steps you have followed seem like the right ones (congratulations on updating the BIOS, not everyone can pull that off!).

A few folks found that the brand of USB stick they were using just did not work for booting.  So a change in brand MAY get you working.  Most folks who saw this had a 'quick blink' of the USB light as the computer attempted a boot and got stuck.

Also - if your system has USB 3.0 ports, right now Ubuntu will not boot from USB 3.0 ports, you need to boot from a USB 2.0 port.


***The Hedge***

:KS

---

### Post by tandemrider on 2011-04-05
:D Even with a second USB stick I haven't been able to install Ubuntu from USB. Now I borrowed an external DVD drive, burned the netbook.iso onto a CD and just gave it a try - it works! I tried it for while from CD, and currently I am installing Ubuntu onto my hardrive! :D

Even though installing from CD is not mentioned as an option is not mentioned on the Netbook-download page, it works just like it is explained on the download page for the desktop edition (just use the netbook.iso, of course).

I'm happy!

---

### Post by Hedgehog1 on 2011-04-05
**Hurray!** As long as you are working (and happy). :P
 
Looks like you may need to get and external DVD drive of your very own one of these days... **More TOYS!!!!**
 
 
***The Hedge***
 
:KS

---

### Post by OldAndTired on 2012-03-11
Well, I have the same problem, I'm not working, and I'm not happy.  I hope someone can address this.

---

### Post by oldos2er on 2012-03-11
OldAndTired, please start a new thread for your question, and include as much detail as possible; OS version, hardware specs, etc.

---

