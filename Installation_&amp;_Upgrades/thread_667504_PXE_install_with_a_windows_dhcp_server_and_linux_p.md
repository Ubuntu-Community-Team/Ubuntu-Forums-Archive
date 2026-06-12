---
title: "PXE install with a windows dhcp server and linux pxe server"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by citybird on 2008-01-14
Hi all I just thought I'd share with you my experience in setting up a PXE server in a windows/linux mixed enviornment

**First I used the instructions found here to set up my TFTP server on a Ubuntu 7.10 server machine:**
[http://myy.helia.fi/~karte/ubuntu_pxe.html](http://myy.helia.fi/~karte/ubuntu_pxe.html)

the only thing that I had to change was the version from breezy to gutsy and I cut out creating the new user. so here is the step by step:

 Install TFPT server. Also install client for testing. Trivial file transfer protocol is not related to FTP.

>  $ sudo apt-get install tftpd-hpa tftp-hpa

Configure TFTP server. Notice nice path for TFTPd root (don&#8217;t use &#8220;/tftpsomething&#8221;). In RUN_DAEMON, &#8220;yes&#8221; must be small caps.

>  $ sudo nano /etc/default/tftpd-hpa

```
# /etc/default/tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /home/tftpboot/"
```

Allow your normal user to modify /home/tftpboot/. Ues your own username and group

>  $ whoami 
administrator
 $ sudo mkdir /home/tftpboot
 $ sudo chown -R administrator:administrator /home/tftpboot/


Now you can modify files in TFTPd root dir (/home/tftpboot/) without using sudo

Download netboot files to /home/tftpboot. (mirror of netboot files):

```
 $ cd /home/tftpboot
 $ wget -np -r http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/
 $ mv archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/* .
 $ rm -rf archive.ubuntu.com/

```

Start TFTP server and test it

>  $ sudo /etc/init.d/tftpd-hpa start
 $ cd
 $ tftp localhost -c get pxelinux.0
 $ ls pxeli*
 pxelinux.0


**Now we move on to the windows DHCP server.**
I used this tutorial here to configure it but again not the entire thing since this was not my environment.
[http://pxes.sourceforge.net/howtos/ms_only_environment/](http://pxes.sourceforge.net/howtos/ms_only_environment/)

just skip down to how to configure the DHCP server section and open the DHCP tool.

it says that you need to add 4 new entries but in a mixed environment you only need 2: 066 and 067
On my server I added:
> 066 Boot Server Host Name and the IP address of my PXEserver as the string
067 Bootfile Name and a String Value of pxelinux.0

_*Do not add 043 and 060*_  =;

That's it!

\\:D/

The last thing that I need to learn is how to create a menu that allows me to choose from different images to install. Since this is a mixed environment I would be interested in Ubuntu Server and Workstation and Windows Server and Workstation install images. I also need to create custom Ubuntu server images which load/install special drivers.


UPDATE:
If you have never tried the network install oh my world!
The Choices!! THE CHOICES!!

Why hasn't anyone ever shown us the Choices before??

DNS Server
Edubuntu server
LAMP server
Mail server
OpenSSH server
PostgreSQL database
Print server
Samba File server
2D/3D creation and editing suite
Audio creation and editing suite
Edubuntu KDE desktop
Edubuntu desktop
Gobuntu desktop
Kubuntu desktop
LADSPA and DSSI audio plugins
Mythbuntu additional roles
Ubuntu Studio desktop
Ubuntu desktop
Video creation and editing suite
Xubuntu desktop

ARE YOU KIDDING ME?? THIS IS INSANE!!
I at first wanted this just for automating workstation and server install but now I gota testdrive some of these application suites 

:guitar:

---

