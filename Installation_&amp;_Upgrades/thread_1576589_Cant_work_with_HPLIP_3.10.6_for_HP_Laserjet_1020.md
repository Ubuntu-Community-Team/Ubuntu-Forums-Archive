---
title: "Cant work with HPLIP 3.10.6 for HP Laserjet 1020"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by rkrinfo on 2010-09-17
I am working with Ubuntu 10.04
I can't print documents on HP Laserjet 1020
While printing, the jobs shows up in the print queue and disappears without any error, but no printout 

I tried to install HPLIP 3.10.6 from [http://hplipopensource.com](http://hplipopensource.com)
I followed the instructions but it ends with the error


```
INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 5 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups-devel (CUPS devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 5 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'fax': dbus (DBus - Message bus system)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'base': cups-ddk (CUPS DDK - CUPS driver development kit)


CHECKING FOR NETWORK CONNECTION
-------------------------------
error: 
The network appears to be unreachable. Installation cannot complete without access to
error: distribution repositories. Please check the network and try again.
```

My PC is always connected to the internet.
I tried to install missing packages through synaptic, but i can't find those.

HELP ME.

---

### Post by sikander3786 on 2010-09-17
Try

```

sudo apt-get update

```

```

sudo apt-get install -f

```

If you are sure you are connected to the internet (make sure by browsing some websites) and the apt-get update command doesn't work, try changing the server from System >>> Administration >>> Software Sources. Select Main and retry the commands. Post the errors if any.

---

### Post by SR_ELPIRATA on 2010-09-18
I've installed HPLIP many times, and I dont remember now but there was a command that would tell you the dependencies it needed, once I had them I would go to synaptics and add them before running the hplip software.

There was one file that the name, though, was not accurate, but I can't say for sure right now cause I dont remember which, it was somethign 'dev' and I had to use the one that said 'devel'.

ELP

---

### Post by Th3Alchemist on 2010-10-20
try:

```

sudo apt-get install aptitude

sudo aptitude install --assume-yes libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane
```

then retry installation process

---

### Post by htor on 2010-10-24
I have the same problem on ubuntu 10.10... Your solutions don't work.

---

### Post by htor on 2010-10-24
_Solution that worked for me:_
1) Execute:
```
wget http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.10.6-plugin.run
```
2)
```
sudo hp-setup -i
```

3) in the stage "PLUG-IN INSTALLATION FOR HPLIP 3.10.6" you should choose the option
> p           Specify a path to the plug-in (advanced)
and write the path of the downloaded file.

---

### Post by rkrinfo on 2011-03-01
Sorry for late reply.
This one is worked for me

> **htor said:**
> _Solution that worked for me:_
1) Execute:
```
wget http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.10.6-plugin.run
```
2)
```
sudo hp-setup -i
```

3) in the stage "PLUG-IN INSTALLATION FOR HPLIP 3.10.6" you should choose the option

and write the path of the downloaded file.

---

### Post by josephj on 2011-04-29
Just did roughly the same thing on lucid.  Used hplip-3.10.2-plugin.run instead for compatibility with lucid. I also had to uninstall and reinstall hplip and then reinstall foo2zjs.  Got a few segfaults along the way, but it still worked.  Finally, I deleted my printer and reinstalled it.  Now, it seems to work.  We'll see what happens once I reboot. 

Thanks so much for finding and reporting this solution!

I was in a catch-22.  I needed to print out these debugging instructions so I could print out these debugging instructions <G>.

Joe

---

### Post by mik01aj on 2011-06-03
I'm using ubuntu 11.04, Natty. Here's what worked for me:

1. Download [http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.11.1-plugin.run](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.11.1-plugin.run) (NOTE version 3.11.1)

2. Plug in the printer. There appears a prompt for password and then an installation dialog, where you have to select the file you just downloaded. (If it's for version 3.10.6, the field will turn yellow, and "Next" will be greyed out).

3. Enjoy :)

---

### Post by linbynd on 2011-09-01
> **mik01aj said:**
> I'm using ubuntu 11.04, Natty. Here's what worked for me:

1. Download [http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.11.1-plugin.run](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.11.1-plugin.run) (NOTE version 3.11.1)

2. Plug in the printer. There appears a prompt for password and then an installation dialog, where you have to select the file you just downloaded. (If it's for version 3.10.6, the field will turn yellow, and "Next" will be greyed out).

3. Enjoy :)


This works in Kubuntu 11.04 as well.... the problem that the installation through the GUI fails is due to the GPG Key..... but from the manual installation all works well.

Note : Download the correct plugin for the HP GUI,... for me, I had to download hplip 3.11.1 as mentioned above.......

---

### Post by Jimmy Goal on 2012-04-06
For me only this one below worked with my HP Laserjet 1020 with ubuntu 10.10 on Ibook G4 and on PC-i686

1 
Go to 
    [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Reading
**Install and Setup**

                                        
[LIST]
[*][Download]("http://hplipopensource.com/hplip-web/gethplip.html")
[*][Install]("http://hplipopensource.com/hplip-web/install.html")
[*][Install Wizard]("http://hplipopensource.com/hplip-web/install_wizard/index.html")
[/LIST]
should do


Basically
Download hplip-3.12.2.run from [http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)
then run   'sh hplip-3.12.2.run' (check version)

Cheeers

---

