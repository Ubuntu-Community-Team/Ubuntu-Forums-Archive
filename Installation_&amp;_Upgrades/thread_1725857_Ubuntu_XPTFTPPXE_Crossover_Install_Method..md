---
title: "Ubuntu XP/TFTP/PXE Crossover Install Method."
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by D3miend on 2011-04-10
_**Ubuntu Install from  Windows XP - TFTPD32 - PXE - Crossover Installation Method.**_ Step by Step.
[U]
You will need:[/U]

- one laptop/desktop with internet connection.
- and one laptop/desktop for the installation.
- a crossover cable (any CAT5/CAT6 ethernet wire)
- Tftpd32 : [http://tftpd32.jounin.net/tftpd32_download.html](http://tftpd32.jounin.net/tftpd32_download.html)
- Netboot : [ftp://ftp.linux.org.uk/pub/distributions/debian/dists/sarge/main/installer-ia64/20041118/images/netboot/netboot.tar.gz](ftp://ftp.linux.org.uk/pub/distributions/debian/dists/sarge/main/installer-ia64/20041118/images/netboot/netboot.tar.gz)
- and some brain power.

-------------------------------------------------------------------------------

**_On the windows xp machine do as follows:_**

- go to properties tab of the nic you will be using for crossover.
- go to ipv4 and edit as follow:
- _IP Address: 192.168.5.1_
- _Subnet mask: 255.255.255.0_

- everything else stays blank.
- you will notice why later on.

- now lets move on with the tools you downloaded from the links above
- exctract tftpd32 anywhere, lets say desktop
- go into the folder and start the application
- now hit settings button and check the *DHCP server* / restart tftpd32
- now go again to settings button, and at the top go to DHCP tab.
- setup everything as follows:

- _IP start addr: 192.168.5.2_
- _Size of pool: 20_
- _Bootfile: netboot\pxelinux.0_
- _WINS/DNS: 192.168.5.1_
- _Default Router: 192.168.5.1_
- _Mask: 255.255.255.0_

- hit ok
- remember now the tftpd32 server interface must be set 192.168.5.1
- it will change automatically or need a change when we connect both machines with the wire.
- remember to have all firewalls turned off!

- now extract netboot anywhere.
- go to tftpd32 directory and create a folder there called netboot
- copy all files from extracted netboot in to the new created folder.
- it will be : ubuntu-installer / pxelinux.0 / version.info
- so now when you are in the tftpd32/netboot
- go to the ubuntu-installer/i386 & copy the pxelinux.cfg folder
- paste it once in the main tftpd32 directory and once in the tftpd/netboot directory
- thats all folks, now connect your crossover cable
- start or restart the tftpd32 daemon.
- boot the machine you are installing on into PXE mode
- it will auto DHCP and kick you in to the installation
- follow the steps, good luck.

**make sure the other laptop has Internet connection or Internet connection share**
[B]ubuntu will be downloaded from the ubuntu internet archives
if you just install the core it's ok
_once your installation was successful, login and do sudo apt-get install ubuntu-desktop_
[/B] 
):P

---

