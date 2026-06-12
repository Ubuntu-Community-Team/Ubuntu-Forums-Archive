---
title: "HPLIP 3.20.6 Installation Problem"
date: 2020-06-18
forum: Installation &amp; Upgrades
---

### Post by and003 on 2020-06-18
I recently upgraded to Ubuntu 20.04. As part of this, I installed the latest version of HPLIP. However, the attempts to install have been fraught with problems. When I installed hplip-3.20.6, I got the following error messages:

 
[B]error: Channel write error
error: Unable To read the XML data from device[/B]

 
As a result, when I try to install my printer, I get this error message:

 
[B]Printer Error.
Printer is busy, offline, or in an error state. Please check the device and try again.[/B]

Strangely, I can install my printer as a fax machine. Here is the information about my setup:

Motherboard: MSI 970 GAMING DDR3 2133 ATX AMD
Processor: AMD FD8350FRHKBOX FX-8350 FX-Series 8-Core Black Edition
Memory: HyperX Kingston FURY 32GB (4x8GB) 1866MHz DDR3 CL10 DIMM - Black (HX318C10FBK2/16)
Video Card: EVGA 1GB GeForce 8400 GS DirectX 10 64-Bit DDR3 PCI Express 2.0 x16 HDCP Ready Video Card Model 01G-P3-1302-LR
Monitor: Acer V173 Djb 17-inch (LCD) 
Printer: HP Smart Tank Plus 651
Software: HPLIP 3.20.6
Operating System: Ubuntu 20.04

---

### Post by ActionParsnip on 2020-06-18
Did you download the hplip ".run" file to install? If so can you please give the full output when you run it. If you don't have the ".run" file, can you please give details as to how you are trying to install it.
Thanks

---

### Post by and003 on 2020-06-18
Here is the .run document you asked for. It is from a second attempt to install my printer.

******

```
and003@TGRAMZN-U20-MS-7693:~$ cd /home/and003/Downloads
and003@TGRAMZN-U20-MS-7693:~/Downloads$ sh hplip-3.20.6.run
Creating directory hplip-3.20.6
Verifying archive integrity... All good.
Uncompressing HPLIP 3.20.6 Self Extracting Archive.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.20.6)
HPLIP Installer ver. 5.1

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Thu-18-Jun-2020_14:10:50.log

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
Please enter the sudoer (and003)'s password: 
 

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
HPLIP-3.20.6 exists, this may conflict with the new one being installed.
Do you want to ('i'= Remove and Install*, 'q'= Quit)?    :i
Starting uninstallation...
HPLIP uninstallation is completed


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
OK


RUNNING SCANJET DEPENDENCY COMMANDS
-----------------------------------
sudo apt-get install --assume-yes python3-pip (Scanjet-depend step 1)
sudo pip3 install --upgrade pip (Scanjet-depend step 2)
sudo apt-get install --assume-yes libleptonica-dev (Scanjet-depend step 3)
sudo apt-get install --assume-yes tesseract-ocr (Scanjet-depend step 4)
sudo apt-get install --assume-yes libtesseract-dev (Scanjet-depend step 5)
sudo -H pip3 install tesserocr (Scanjet-depend step 6)
sudo -H pip3 install opencv-python (Scanjet-depend step 7)
sudo -H pip3 install PyPDF2 (Scanjet-depend step 8)
sudo -H pip3 install imutils (Scanjet-depend step 9)
sudo -H pip3 install ocrmypdf (Scanjet-depend step 10)
sudo -H pip3 install scikit-image (Scanjet-depend step 11)
sudo -H pip3 install scipy (Scanjet-depend step 12)
sudo apt-get install --assume-yes qpdf (Scanjet-depend step 13)
OK


PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --with-hpppddir=/usr/share/ppd/HP --libdir=/usr/lib --prefix=/usr --enable-network-build --enable-scan-build --enable-fax-build --enable-dbus-build --disable-qt4 --enable-qt5 --disable-class-driver --enable-doc-build --disable-policykit --disable-libusb01_build --disable-udev_sysfs_rules --enable-hpcups-install --disable-hpijs-install --disable-foomatic-ppd-install --disable-foomatic-drv-install --disable-cups-ppd-install --enable-cups-drv-install --enable-apparmor_build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
Command completed successfully.

Running 'sudo make install'
Please wait, this may take several minutes...
Command completed successfully.


Build complete.



POST-BUILD COMMANDS
-------------------
 

CLOSE HP_SYSTRAY
----------------
Sending close message to hp-systray (if it is currently running)...
OK


HPLIP UPDATE NOTIFICATION
-------------------------
Do you want to check for HPLIP updates?. (y=yes*, n=no) : y


RESTART OR RE-PLUG IS REQUIRED
------------------------------
If you are installing a USB connected printer, and the printer was plugged in   
when you started this installer, you will need to either restart your PC or     
unplug and re-plug in your printer (USB cable only). If you choose to restart,  
run this command after restarting: hp-setup (Note: If you are using a parallel  
connection, you will have to restart your PC. If you are using network/wireless,
you can ignore and continue).                                                   

Restart or re-plug in your printer (r=restart, p=re-plug in*, i=ignore/continue, q=quit) : p
Please unplug and re-plugin your printer now.  Press <enter> to continue or 'q' to quit: 


PRINTER SETUP
-------------
Please make sure your printer is connected and powered on at this time.
Do you want to setup printer in GUI mode? (u=GUI mode*, i=Interactive mode) : u

HP Linux Imaging and Printing System (ver. 3.20.6)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
error: Channel write error
error: Unable To read the XML data from device
error: Channel write error
error: Unable To read the XML data from device
error: Channel write error
error: <b>Device I/O Error</b><p>Could not communicate with device. Device may be busy.
Traceback (most recent call last):
  File "/usr/share/hplip/ui5/setupdialog.py", line 1131, in readwriteFaxInformation
    d.setStationName(self.fax_name_company)
  File "/usr/share/hplip/fax/ledmfax.py", line 140, in setStationName
    return self.put("/DevMgmt/FaxConfigDyn.xml", xml)
  File "/usr/share/hplip/fax/ledmfax.py", line 102, in put
    self.writeLEDM(data.encode('utf-8'))
  File "/usr/share/hplip/base/device.py", line 2225, in writeLEDM
    return self.__writeChannel(self.openLEDM, data)
  File "/usr/share/hplip/base/device.py", line 2258, in __writeChannel
    raise Error(ERROR_DEVICE_IO_ERROR)
base.g.Error: ('Device I/O error', 12)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/share/hplip/ui5/setupdialog.py", line 1317, in NextButton_clicked
    self.addPrinter()
  File "/usr/share/hplip/ui5/setupdialog.py", line 1021, in addPrinter
    self.readwriteFaxInformation(False)
  File "/usr/share/hplip/ui5/setupdialog.py", line 1138, in readwriteFaxInformation
    if QMessageBox.critical(self,
TypeError: critical(QWidget, str, str, buttons: Union[QMessageBox.StandardButtons, QMessageBox.StandardButton] = QMessageBox.Ok, defaultButton: QMessageBox.StandardButton = QMessageBox.NoButton): argument 5 has unexpected type 'StandardButtons'

Done.


RE-STARTING HP_SYSTRAY
----------------------

HP Linux Imaging and Printing System (ver. 3.20.6)
System Tray Status Service ver. 2.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

and003@TGRAMZN-U20-MS-7693:~/Downloads$

```
******

Let me know if this helps.

---

### Post by and003 on 2020-06-18
I am also prepared to provide the ".run" file of a previous attempt to upgrade from hplip-3.20.3 if requested since the same problem occurred with it. Furthermore, I can provide an hp-check document if that is also required.

---

### Post by and003 on 2020-06-20
> **and003 said:**
> I am also prepared to provide the ".run" file of a previous attempt to upgrade from hplip-3.20.3 if requested since the same problem occurred with it. Furthermore, I can provide an hp-check document if that is also required.
There is something else. When I tried to install the printer again with the HP Device Manager, I noticed something in the PPD File that suggests a PPD link might help. The PPD file was listed at the following address:

**_drv:///hpcups.drv/hp-smart_tank_plus_650_series.ppd_**

Is this supposed to be where the PPD file is located? I was wondering because there is no _drv:///hpcups.drv/_ on my computer.

---

### Post by ActionParsnip on 2020-06-20
Search for the PPD file online. You may find it available and can use it to setup the printer

---

### Post by and003 on 2020-06-20
> **ActionParsnip said:**
> Search for the PPD file online. You may find it available and can use it to setup the printer
I have the PPD file in my possession, but now I need to know how to use it. I put the file in a separate directory and tried using the HP Device Manager to access it, but for some reason the directory change doesn't happen.

---

### Post by dragonfly41 on 2020-06-20
What does [http://localhost:631](http://localhost:631) (CUPS) show in your browser?

[Later edit] I was searching around since my old HP LaserJet 2500 printer works on 16.04 but not (yet) on 18.04.
I found [this discussion]("https://askubuntu.com/questions/831166/where-are-the-printer-drivers").

---

### Post by and003 on 2020-06-20
> **dragonfly41 said:**
> What does [http://localhost:631](http://localhost:631) (CUPS) show in your browser?
**No Printers Found.**

Also, I just checked the printers.conf file and found this line: 

**DeviceURI implicitclass://Smart_Tank_Plus_650_series_CN9B8240ZR_/**

Do I need to make any corrections? I believe so, but I wanted to be sure.

---

### Post by dragonfly41 on 2020-06-21
I have just completed a troubleshooting exercise of comparing my old /etc/cups (working on Ubuntu 16.04) configuration with my new /etc/cups (not working on Ubuntu 18.04) configuration.

Started from the point where printer was not detected in localhost:631.

I have Krusader installed as a file manager and with two panes it is easier to compare old directory with new.  I observed differences in file sizes and some files were missing in my new configuration.

I also noticed there is /etc/cupshelpers folder alongside /etc/cups.

To cut a long story short I changed the folder names in my new directory to /etc/_cups and /etc/_cupshelper just to back them up.

Next I copied /etc/cups and /etc/cupshelpers from old (16.04) to new (18.04). 
 For good measure I restarted Ubuntu.
 
 And on viewing localhost:631 I was back in business. Printer showed in browser.

...

Now to address your issues;
In my searching around while troubleshooting I found this tutorial.
[https://www.linux.com/training-tutorials/how-manage-printers-linux/](https://www.linux.com/training-tutorials/how-manage-printers-linux/)
 
Suggests going to System Settings > Devices > Printers

Also there is this command:  sudo lpinfo -v

I have not fathomed out all the mysteries but these help,

Also I have ripgrep installed ..
[https://github.com/BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep)

and I can scan the innards of files and directories to look for patterns (such as "DeviceURI" which you report).

cd /etc/cups
sudo rg DeviceURI ./

and I get this ..

[FONT=monospace][COLOR=#18B218]263[/COLOR][COLOR=#000000]:# Set IPBased[/COLOR][COLOR=#FF5454]**DeviceURI**[/COLOR][COLOR=#000000]s to "Yes" if cups-browsed should create its[/COLOR]
[COLOR=#18B218]272[/COLOR][COLOR=#000000]:# IPBased[/COLOR][COLOR=#FF5454]**DeviceURI**[/COLOR][COLOR=#000000]s to "IPv4" to only get IPv4 IP addresses or[/COLOR]
[COLOR=#18B218]273[/COLOR][COLOR=#000000]:# IPBased[/COLOR][COLOR=#FF5454]**DeviceURI**[/COLOR][COLOR=#000000]s to "IPv6" to only get IPv6 IP addresses.[/COLOR]
[COLOR=#18B218]275[/COLOR][COLOR=#000000]:# IPBased[/COLOR][COLOR=#FF5454]**DeviceURI**[/COLOR][COLOR=#000000]s No[/COLOR]
[COLOR=#18B218]276[/COLOR][COLOR=#000000]:# IPBased[/COLOR][COLOR=#FF5454]**DeviceURI**[/COLOR][COLOR=#000000]s Yes[/COLOR]
[COLOR=#18B218]277[/COLOR][COLOR=#000000]:# IPBased[/COLOR][COLOR=#FF5454]**DeviceURI**[/COLOR][COLOR=#000000]s IPv4[/COLOR]
[COLOR=#18B218]278[/COLOR][COLOR=#000000]:# IPBased[/COLOR][COLOR=#FF5454]**DeviceURI**[/COLOR][COLOR=#000000]s IPv6[/COLOR]

[COLOR=#B218B2]./printers.conf.O[/COLOR]
[COLOR=#18B218]9[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#FF5454]**DeviceURI**[/COLOR][COLOR=#000000] usb://HP/LaserJet%202100%20Series[/COLOR]

[COLOR=#B218B2]./printers.conf[/COLOR]
[COLOR=#18B218]9[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#FF5454]**DeviceURI**[/COLOR][COLOR=#000000] usb://HP/LaserJet%202100%20Series

[/COLOR]========================================

**[Later edit]**
Another thread I found .. referring to "[/FONT][COLOR=#000000][FONT=&quot]DeviceURI implicitclass:"[/FONT][/COLOR][FONT=monospace]
[/FONT][FONT=monospace]
[/FONT][https://ubuntuforums.org/showthread.php?t=2441601](https://ubuntuforums.org/showthread.php?t=2441601)
[FONT=monospace]

[/FONT]

---

### Post by and003 on 2020-06-21
> **dragonfly41 said:**
> I have just completed a troubleshooting exercise of comparing my old /etc/cups (working on Ubuntu 16.04) configuration with my new /etc/cups (not working on Ubuntu 18.04) configuration.

Started from the point where printer was not detected in localhost:631.

I have Krusader installed as a file manager and with two panes it is easier to compare old directory with new.  I observed differences in file sizes and some files were missing in my new configuration.

I also noticed there is /etc/cupshelpers folder alongside /etc/cups.

To cut a long story short I changed the folder names in my new directory to /etc/_cups and /etc/_cupshelper just to back them up.

Next I copied /etc/cups and /etc/cupshelpers from old (16.04) to new (18.04). 
 For good measure I restarted Ubuntu.
 
 And on viewing localhost:631 I was back in business. Printer showed in browser.

Did you have 16.04 and 18.04 on your computer at the same time? I only installed 20.04 on mine and no other Ubuntu version. Indeed, I reinstalled it today to start with a clean slate with regards to a printer installation using HPLIP 3.20.3, adding Cinnamon and LXDE as I went along.

Which brings me to a clue that might interest you. When I plugged my printer into an USB port after the reinstallation, the 'system-config-printer' program detected it as a network printer, signalling that it is connected to **_localhost_**, but when I went to localhost:631 and pressed the "Find New Printers" button, the aforementioned 'No Printers Found' error message appeared. Also, when I clicked on the "Add Printer" button, this came up:

**[http://localhost:631](http://localhost:631) is requesting your username and password. The site says: "CUPS"**

Perhaps using my printer as a Network printer might be an avenue I can pursue? I could devise my own username and password in the process. I was using the Cinnamon desktop environment at the time I plugged the printer into the USB port if it matters. Also, when I click on the "Manage Printers" button, my printer does show up.

---

### Post by dragonfly41 on 2020-06-21
[COLOR=#000000]> Did you have 16.04 and 18.04 on your computer at the same time? 

Sorry, I should have explained that I have an old Ubuntu 16.04 installed alongside Windows 10 in /dev/sda
and in /dev/sdb I have Ubuntu 18.04 installed on an SSD in a docking bay.  This way I can refer back to old installations.

I have solved my problem of missing printer and I posted the above workflow not as a question but perhaps to help you in your troubleshooting.

...

However, although my printer is recognised I have just tried printing and I get this message ..

[/COLOR][I]"The PPD version (5.2.11) is not compatible with Gutenprint 5.2.13. Please run `/usr/sbin/cups-genppdupdate' as administrator."

[/I][FONT=monospace][COLOR=#000000]Updated /etc/cups/ppd/HP-LaserJet-2100M.ppd using gutenprint.5.2://hp-lj_2100m/expert[/COLOR]
Updated 1 PPD file.  Restart cupsd for the changes to take effect.

That works and I printed my job.[/FONT]

---

### Post by and003 on 2020-06-24
I've discovered something about my XSane installation that might be connected. When I tried using it without HPLIP, I received this error message:

**Failed to open device 'hpaio:/usb/Smart_Tank_Plus_650_series?serial=CN9B8240ZR': Error during device I/O.**

Perhaps the answer lies in this particular issue?

---

### Post by dragonfly41 on 2020-06-24
I'm sorry I can't throw some more ideas into the pot.

---

### Post by and003 on 2020-06-28
> **dragonfly41 said:**
> I'm sorry I can't throw some more ideas into the pot.
That's okay. I'm certain if I can figure out how to change the driver through the HPLIP interface, the problem should clear up. It will mean contacting the people at HPLIP for assistance, though. In the meantime, I can use other programs for scanning and printing.

---

### Post by and003 on 2020-10-19
I wouldn't call it solved, but designating it as such is the only way to close this thread.

---

### Post by carlo-negri-it on 2020-10-30
this is not fair because other users hope a solution has been found, they waste time reading all the posts to find that the problem has not been solved

---

### Post by coffeecat on 2020-10-30
> **carlo-negri-it said:**
> this is not fair because other users hope a solution has been found, they waste time reading all the posts to find that the problem has not been solved

I agree. I have removed the solved prefix. 

> **and003 said:**
> I wouldn't call it solved, but designating it as such is the only way to close this thread.

@and003, please do not do that. It is most discourteous to those searching the internet for solutions to problems. If you want a thread closed, simply click on the "report post" button in your thread opening post to request closure and a member of forum staff will do that for you. I have now closed this thread.

---

