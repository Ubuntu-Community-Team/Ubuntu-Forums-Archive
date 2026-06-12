---
title: "Remove hplip version cleanly"
date: 2016-07-22
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2016-07-22
I haven't used the printer in awhile HP P1006 and plugging it in gave me a system error which was reported, cups issue.  Upon investigation Synaptic stated I have hplip-3.16.3 installed and will not let me mark it for removal etc.  I have versions .5 and .6 on my desktop. I just downloaded the latest .7.
First question is how do I determine which version is running and then how do I remove it completely, at which point I will install .7

Is it me or is hp drivers becoming a huge pain?

Ron

---

### Post by QDR06VV9 on 2016-07-22
```
sudo hp-toolbox status
warning: hp-toolbox should not be run as root/superuser.

HP Linux Imaging and Printing System (ver. 3.16.5)
HP Device Manager ver. 15.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

 
```
Or you find by
```
apt-cache policy hplip
```
This will needed first to help you with the un-install

---

### Post by Alligator on 2016-07-24
I tried both commands and got two different answers.  What next?

```

apt-cache policy hplip
hplip:
  Installed: (none)
  Candidate: 3.16.3+repack0-1
  Version table:
     3.16.3+repack0-1 500
        500 http://mirrors.accretive-networks.net/ubuntu xenial/main amd64 Packages

___________________________________________________________________________________
 sudo hp-toolbox status

warning: hp-toolbox should not be run as root/superuser.

HP Linux Imaging and Printing System (ver. 3.16.7)
HP Device Manager ver. 15.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

No protocol specified
hp-toolbox: cannot connect to X server :1

```

---

### Post by Alligator on 2016-07-25
I have removed 3.16.5 and 3.16.17 as per a howto and reinstalled 17. But, synaptic shows 3.16.3 and will not let me mark it for anything.  After a reboot, I get a "system problem" , a cups error which was reported.

---

### Post by QDR06VV9 on 2016-07-25
> I have removed 3.16.5 and 3.16.17 as per a howto and reinstalled 17. But, synaptic shows 3.16.3
With out knowing what you have followed...I can only guess.  Can you provide the link for the how to you followed?
> hp-toolbox: cannot connect to X server
The above error Is a permission problem
And what happens when you issue this in the terminal
```
sudo apt-get install hplip
```
And you are kind of hard to help when immediately after posting you log out???:confused:

---

### Post by Alligator on 2016-07-26
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  hplip-data libhpmud0 libsane-hpaio printer-driver-hpcups
  printer-driver-postscript-hp
Suggested packages:
  hplip-doc hplip-gui system-config-printer
The following NEW packages will be installed:
  hplip hplip-data libhpmud0 libsane-hpaio printer-driver-hpcups
  printer-driver-postscript-hp
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,940 kB of archives.
After this operation, 15.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://mirrors.accretive-networks.net/ubuntu xenial/main amd64 hplip-data all 3.16.3+repack0-1 [6,393 kB]
Get:2 http://mirrors.accretive-networks.net/ubuntu xenial/main amd64 libhpmud0 amd64 3.16.3+repack0-1 [107 kB]
Get:3 http://mirrors.accretive-networks.net/ubuntu xenial/main amd64 libsane-hpaio amd64 3.16.3+repack0-1 [114 kB]
Get:4 http://mirrors.accretive-networks.net/ubuntu xenial/main amd64 printer-driver-hpcups amd64 3.16.3+repack0-1 [252 kB]
Get:5 http://mirrors.accretive-networks.net/ubuntu xenial/main amd64 hplip amd64 3.16.3+repack0-1 [65.6 kB]
Get:6 http://mirrors.accretive-networks.net/ubuntu xenial/main amd64 printer-driver-postscript-hp all 3.16.3+repack0-1 [1,009 kB]
Fetched 7,940 kB in 13s (599 kB/s)                                             
Selecting previously unselected package hplip-data.
(Reading database ... 334227 files and directories currently installed.)
Preparing to unpack .../hplip-data_3.16.3+repack0-1_all.deb ...
Unpacking hplip-data (3.16.3+repack0-1) ...
Selecting previously unselected package libhpmud0:amd64.
Preparing to unpack .../libhpmud0_3.16.3+repack0-1_amd64.deb ...
Unpacking libhpmud0:amd64 (3.16.3+repack0-1) ...
Selecting previously unselected package libsane-hpaio:amd64.
Preparing to unpack .../libsane-hpaio_3.16.3+repack0-1_amd64.deb ...
Unpacking libsane-hpaio:amd64 (3.16.3+repack0-1) ...
Selecting previously unselected package printer-driver-hpcups.
Preparing to unpack .../printer-driver-hpcups_3.16.3+repack0-1_amd64.deb ...
Unpacking printer-driver-hpcups (3.16.3+repack0-1) ...
Selecting previously unselected package hplip.
Preparing to unpack .../hplip_3.16.3+repack0-1_amd64.deb ...
Unpacking hplip (3.16.3+repack0-1) ...
Selecting previously unselected package printer-driver-postscript-hp.
Preparing to unpack .../printer-driver-postscript-hp_3.16.3+repack0-1_all.deb ...
Unpacking printer-driver-postscript-hp (3.16.3+repack0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for cups (2.1.3-4) ...
Updating PPD files for hpcups ...
PPD for printer HP_LaserJet_P1006 updated
PPD for printer Officejet_6600 updated
PPD for printer Officejet_6600_fax updated
Updating PPD files for postscript-hp ...
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up hplip-data (3.16.3+repack0-1) ...
Setting up libhpmud0:amd64 (3.16.3+repack0-1) ...
Setting up libsane-hpaio:amd64 (3.16.3+repack0-1) ...

Configuration file '/etc/hp/hplip.conf'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** hplip.conf (Y/I/N/O/D/Z) [default=N] ? 
Setting up printer-driver-hpcups (3.16.3+repack0-1) ...
Setting up hplip (3.16.3+repack0-1) ...
Creating/updating hplip user account...
dpkg-statoverride: warning: --update given but /var/run/hplip does not exist
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
Setting up printer-driver-postscript-hp (3.16.3+repack0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for dbus (1.10.6-1ubuntu3) ...

```

If I have to leave I normally log out.  I have a boss.

---

### Post by Alligator on 2016-07-26
The thread to uninstall hplip is from

[http://www.hplipopensource.com/node/188](http://www.hplipopensource.com/node/188)

---

### Post by QDR06VV9 on 2016-07-26
> If I have to leave I normally log out.  I have a boss.
Well that makes sense then :o:)
Now lets see what we got going on...show me the out put of this
```
sudo dpkg -l | grep hplip
```

---

### Post by Alligator on 2016-07-26
```

ii  hplip                                          3.16.3+repack0-1                                            amd64        HP Linux Printing and Imaging System (HPLIP)
ii  hplip-data                                     3.16.3+repack0-1                                            all          HP Linux Printing and Imaging - data files

```

---

### Post by QDR06VV9 on 2016-07-27
Ok that shows everything nice and tidy.
I like to have the Control Panel installed also...to manage Scans, fax, etc etc.
So I always install these along with the hplip glob
```
sudo apt-get install hplip-gui system-config-printer
```
And once those are installed I add the printer...My way may be different but it works quickly and easy.
```
hp-setup 192.168.x.x
``` 
Where you will need your IP the above is just an example. 
But you will need to know your printers IP.
And most HP Printers have a Menu that will show that Address.
But after the last command "hp-setup" It should be straight forward from there.

---

### Post by Alligator on 2016-07-28
```

sudo apt-get install  system-config-printer-gnome system-config-printer-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
system-config-printer-common is already the newest version (1.5.7+20160212-0ubuntu2).
system-config-printer-gnome is already the newest version (1.5.7+20160212-0ubuntu2).

hp-setup

HP Linux Imaging and Printing System (ver. 3.16.7)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)


```
Manual discovery resulted in this

HP LaserJet p1006 hp:/usb/HP_Laser_P1006?serial=AC29TN3

I just did a reboot and 

The printer works; however, there is this System program problem detected

Action: com.ubuntu.apport.apport-gtk-root

---

### Post by QDR06VV9 on 2016-07-28
Was you able to see what the error was?

---

### Post by leunam12 on 2016-07-28
That is a great little printer indeed. Do you actually need hplip to install it? I think it installs and prints fine without it.

---

### Post by QDR06VV9 on 2016-07-28
> **leunam12 said:**
> That is a great little printer indeed. Do you actually need hplip to install it? I think it installs and prints fine without it.

> [h=2][SIZE=3]Driver Plugin Information:[/SIZE][/h] This printer REQUIRES a downloadable driver plug-in, which is  required to enable print, fax or scan support. Use hp-setup to install  the printer, and to download and install the plug-in. Driver plug-ins  are released under a proprietary (non-open) license and are not part of  the HPLIP tarball release.


Source [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1006.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1006.html)

---

### Post by Alligator on 2016-07-28
Unfortunately installing hplip gave me this error. The "Action" point to the error, but when I report, nothing is shown. Also I have another hp 3 in one printer Officejet 6600 which I only use as a scanner.  Too cheap to buy refills.

---

### Post by QDR06VV9 on 2016-07-28
Are both printers hooked to this machine?
At this point I am as lost as you are...It is just not this hard.:(

---

### Post by Alligator on 2016-07-28
Yes both printers are connected and working.  I will try searching for the action item.  When I had 15.10 installed there was an annoying error, no fix, so I upgraded to 16.04 and now I have another. Oh well not a big deal.  Thanks for you help,  I'm off to a retirement party.

---

