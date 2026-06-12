---
title: "Dapper Server install didn’t create LP1"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by MPH on 2007-04-19
I added a network card to a 1995 Gateway 2000 PC with a 200MHz CPU and 80MB of RAM and installed the Dapper server with Samba to create a file and print server for our home network.  The PC has an adapter card with a parallel port and a serial port on it so I expect SAMBA to eventually be able to serve a laser printer and Deskjet printer from the PC’s two parallel ports.  (Neither printer has been connected to this PC yet.)

Since the server installs without a GUI, I used “sudo ls /dev/lp*” to list the installed parallel ports.  Only “lp0” was listed so I assume only one printer port is installed.

A possible reason is the old PC couldn’t directly boot the server ISO CD I burnt.  (A newer PC could boot the CD)  After fumbling with GRUB4DOS, etc., the installation started but without any start-up screen displaying the server installation options.  The installation just charged ahead and installed “whatever”.  Apparently, it didn’t create a LAMP server but I have no idea if the process skipped any important installation steps.  Since APTITUDE has been able to install SAMBA and perform several system updates, I assume the system is reasonably functional.  I’m a Linux noobie so I have no idea about how to use the command line to make sure both parallel ports are installed properly… nor how to administer and troubleshoot hardware problems from the command line.

Most Ubuntu documents assume the user has a GUI so where do I find out how to administer server hardware via the command line?  Of most immediate need… what commands do I need to use to determine if both parallel ports were properly installed by Dapper server?

---

