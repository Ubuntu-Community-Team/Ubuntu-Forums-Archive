---
title: "Installing Fiesty on IBM Thinkcentre"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by lsilver on 2007-04-29
Hello.

I'm trying to install Fiesty on my IBM desktop.  Boots OK from the Live disc if I use F4 to set VGA to 1028 x 764 and then completes the install right through to ejecting the disc and restart command where it hangs.  If I turn the machine off and on by hand I correctly get GRUB up showing Ubuntu 10.4 and Windows XP on second disc.  However, when I let it go on to run Ubuntu the system just hangs without anything showing on the display and it will not repsond to any keyboard commands.

However, if I select the recovery boot mode everything works fine.   I have read/write access to the hard discs and internet access.  Going in on recovery mode I get the root prompt and can even enter startx to boot into what seems to be a fully functioning Gnome desktop.  Also, I can still boot from the live CD and se e all working OK. 

So, it seems to me that everything has installed properly but I just can't get it to boot up.  Is there a way of setting it to display each command as it executes the boot sequence so that I can see where it is stopping?

I thought it was my ATI card and/or the monitor (Imagequest L50S) but have checked xorg.conf and dmesg against a laptop running 6.10 and another IBM desktop running Edubutu 7.04 and the xorg set-up looks OK.  Also, I have set up remote access via XMDCP and this works fine if I boot in recovery mode (I can log in from on of the other machines) but I don't see the machine in the list of potential servers if I try after it hangs from a standard boot so I don't think I am even getting as far as X in the boot sequence.

Thanks for any suggestions.

Leo.

---

### Post by lsilver on 2007-04-30
Seem to have fixed my own problem but thought I'd log the answer in case anyone else finds it useful.  It was infact a graphics mode problem.  I added vga=771 to the Kernel line for the primary Ubuntu install in Grub:

sudo gedit /boot/grub/menu.lst

and change the line as per below

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5c4c6695-f724-48aa-ae24-6cf3be3db050 ro splash vga=771

---

