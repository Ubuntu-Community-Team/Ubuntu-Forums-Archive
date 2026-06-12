---
title: "ATI Radeon proprietary driver not working"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by KurtP on 2007-11-18
Has anyone managed to make the proprietary ATI Linux driver for Radeon X1800 GTO (PCI-Express x16 VIVO aka R520 for Direct 3D 9) to work with Ubuntu 7.10 (Gutsy Gibbon). I downloaded **ati-driver-installer-8.42.3-x86.x86_64.run** from [AMD]("http://ati.amd.com/support/drivers/linux/linux-radeon.html"), ran the script according to the instructions at
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html")
and rebooted. I then did a 
```
sudo dpkg-reconfigure -phigh xserver-xorg 
sudo /etc/init.d/gdm restart
```
which flubbed things up on 6.10 and 7.10 and now I cannot even get a terminal. Rebooting gives me only the progress bar screen, a blank screen and then "no signal". Pressing ctl-alt-F1 (login terminal) gives the screen showing concentric circles and ubuntu split across it. alt-F2 doesn't work either.

I noticed that after I "installed" the drivers that fglrxinfo wasn't recognized.

Now I have several installations of Ubuntu showing up in Grub. How do I delete one of them? Which one should go? 

I have a Gigabyte GA-G1975X m/b with an Intel Pentium D 805 processor. My aim is to overclock it to finish playing Morrowind which got interrupted by a power surge on the other fried system.

Kurt

---

