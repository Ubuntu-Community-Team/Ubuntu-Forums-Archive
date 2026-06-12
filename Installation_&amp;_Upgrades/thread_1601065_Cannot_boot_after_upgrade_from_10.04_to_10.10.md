---
title: "Cannot boot after upgrade from 10.04 to 10.10"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by manny_buret on 2010-10-19
I just upgraded Ubuntu 10.04 (32bit) to Ubuntu 10.10 (32bit) desktop edition using Update Manger.  After installation, the system restarted and it boots straight into a grub> command line.  I cannot but into Ubuntu.   

I am currently dual booting with Windows XP.  I also fired up a LiveCD session and opened up GParted, but it does not list my Ubuntu partition.  It only lists the Windows partition.  

Any help is appreciated.

---

### Post by mjh_ca on 2010-10-20
Any error messages appearing during boot?  Sign in to the terminal using your usual username/password, then run dmesg and check for error messages.  Possibly a problem with your video driver which is preventing X from starting?

You could try removing and re-installing ubuntu-desktop.  It's a little drastic, but you shouldn't lose any settings.  It will reinstall a lot of packages and should fix your settings.  I did this today to fix a much more broken 10.04 to 10.10 upgrade.

From terminal, run:

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop
sudo reboot

---

