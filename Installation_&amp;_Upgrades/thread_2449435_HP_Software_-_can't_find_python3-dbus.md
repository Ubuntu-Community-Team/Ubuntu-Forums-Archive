---
title: "HP Software - can't find python3-dbus"
date: 2020-08-26
forum: Installation &amp; Upgrades
---

### Post by wforbes on 2020-08-26
**I'm following the steps and have run the command below. I'm also a new Ubuntu user.**

[https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index)

$ sh hplip-3.20.6.runCreating directory hplip-3.20.6
Verifying archive integrity... All good.
Uncompressing HPLIP 3.20.6 Self Extracting Archive.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.20.6)
HPLIP Installer ver. 5.1

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Wed-26-Aug-2020_12:22:55.log

\
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
 

INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a


INTRODUCTION
------------
This installer will install HPLIP version 3.20.6 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 20.04.

Is "Ubuntu 20.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y

Initializing. Please wait...


ENTER USER PASSWORD
-------------------
Please enter the sudoer (wesley)'s password: 
 

INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


SECURITY PACKAGES
-----------------
AppArmor is installed. 
AppArmor protects the application from external intrusion attempts making the application secure

Would you like to have this installer install the hplip specific policy/profile (y=yes*, n=no, q=quit) ? y


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


MISSING DEPENDENCIES
--------------------
Following dependencies are not installed. HPLIP will not work if all REQUIRED dependencies are not installed and some of the HPLIP features will not work if OPTIONAL dependencies are not installed.
Package-Name         Component            Required/Optional   
python3-notify2      gui_qt5              OPTIONAL            
python3-pyqt5-dbus   gui_qt5              OPTIONAL            
python3-dbus         fax                  REQUIRED            
python3-pil          scan                 OPTIONAL            
python3-reportlab    fax                  OPTIONAL            
Do you want to install these missing dependencies (y=yes*, n=no, q=quit) ? y


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: python3-dbus (Python DBus - Python bindings for DBus)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
note: Installation of dependencies requires an active internet connection.
warning: Missing OPTIONAL dependency for option 'gui_qt5': python3-notify2 (Python libnotify - Python bindings for the libnotify Desktop notifications)
warning: Missing OPTIONAL dependency for option 'gui_qt5': python3-pyqt5-dbus (PyQt 5 DBus - DBus Support for PyQt5)
warning: Missing OPTIONAL dependency for option 'fax': python3-reportlab (Reportlab - PDF library for Python)
warning: Missing OPTIONAL dependency for option 'scan': python3-pil (PIL - Python Imaging Library (required for commandline scanning with hp-scan))


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)
OK


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes python3-dbus'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes python3-gi'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes python3-notify2'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes python3-dbus.mainloop.pyqt5'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes python3-reportlab'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes python3-pil'
Please wait, this may take several minutes...
error: A required dependency 'python3-dbus (Python DBus - Python bindings for DBus)' is still missing.


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'python3-dbus (Python DBus - Python bindings for DBus)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.


[B]
However, it appears that the package is installed somewhere. It seems that the HP installer isn't finding the package for some reason.[/B]

(base) wesley@comp-pde:~/Downloads$ apt policy python3-dbus
python3-dbus:
  Installed: 1.2.16-1build1
  Candidate: 1.2.16-1build1
  Version table:
 *** 1.2.16-1build1 500
        500 [http://mirrors.tuxedocomputers.com/ubuntu/mirror/archive.ubuntu.com/ubuntu](http://mirrors.tuxedocomputers.com/ubuntu/mirror/archive.ubuntu.com/ubuntu) focal/main amd64 Packages
        100 /var/lib/dpkg/status

[B]Here's some more information.

[/B](base) wesley@comp-pde:~/Downloads$ which python
/home/wesley/miniconda3/bin/python[B]


PATH
[/B]
(base) wesley@comp-pde:~/Downloads$ printenv
PATH=/home/wesley/miniconda3/bin:/home/wesley/miniconda3/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

---

