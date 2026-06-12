---
title: "Installing=Xserver ugh's"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by Inhumane on 2006-09-04
Well I just finished downloading Drapper, shoved the CD in the drive, rebooted, before it launched the installation (not the menu, but the OS itself, where you can test the LIVE version and also install from), it gave me an xserver error, the problem was that my monitor can't be detected..

I read around a bit and tried dkpg-reconfigure xserver-xorg, I tried it twice, with slightly different configurations each time, did reboot and still no go. It seems that it thinks my monitor should be connected to my built in VGA card, but it's connected to my radeon card (my built in card is even disabled in the BIOS), because it automatically names my graphic card after the name of the built in card (I tried both VESA and ati, btw).

Any tips?:-k ](*,)

---

### Post by chicken101 on 2006-09-05
Ahhh, ok, the problem is that it thinks that your integrated card is default, so it tries to use it.  Try booting it up using your integrated, and then you can see what bus your radeon is on (system -> administration-> device manager).  

Then type

> sudo dpkg-reconfigure xserver-xorg

change the driver to ati, and change it to the correct card and agp bus.  


Hope that helps...

---

### Post by Inhumane on 2006-09-05
Ok I'll try that when I get home, is there a way to make the computer think that there is no built in card and to just use my PCI card as default, either using windows or some kind of command? Because getting behind my computer is a pain so it'll take some effort to connect the monitor to the built in card >.<

---

### Post by Inhumane on 2006-09-05
OK, that worked, but I can't seem to find the BUS number for my radeon card, under info.bus it just says pci, and there's nothing close to x : x : x, so I'm not sure what to input, here's a screenshot of what it looks like

---

### Post by chicken101 on 2006-09-05
It should autodetect anyway, just dl the frglx driver and use that.

(again, use xserver config to change it)

Good luck!

---

