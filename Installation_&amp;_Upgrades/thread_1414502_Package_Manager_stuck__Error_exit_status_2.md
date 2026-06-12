---
title: "Package Manager stuck?  Error exit status 2"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by Sandy Al on 2010-02-23
Hey, I'm new to ubuntu and loving it!  :D
I've run into a small issue, and I'm hoping you may be able to help.  
I was installing the hardware driver for Nvidia when there was an error and it didn't complete the install.  From that point on, any time anything is installed (whether through synaptic package manager or ubuntu software center, or wherever), the installation 'fails' even though the newly installed app then seems to work perfectly fine.  It's like it keeps coming back to what it previously was not able to install, and then has the same 'error exit status 2' 

This is the failure message I get (it's always the same list of python packages at the end):

[INDENT]installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Selecting previously deselected package python-numeric.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 148578 files and directories currently installed.)
Unpacking python-numeric (from .../python-numeric_24.2-9ubuntu1_i386.deb) ...
Selecting previously deselected package gdesklets.
Unpacking gdesklets (from .../gdesklets_0.36.1-2ubuntu1_i386.deb) ...
Selecting previously deselected package gdesklets-data.
Unpacking gdesklets-data (from .../gdesklets-data_0.35.6-3_all.deb) ...
Selecting previously deselected package libcarp-clan-perl.
Unpacking libcarp-clan-perl (from .../libcarp-clan-perl_6.00-1_all.deb) ...
Selecting previously deselected package libbit-vector-perl.
Unpacking libbit-vector-perl (from .../libbit-vector-perl_6.6-1_i386.deb) ...
Selecting previously deselected package libdate-manip-perl.
Unpacking libdate-manip-perl (from .../libdate-manip-perl_5.54-1_all.deb) ...
Selecting previously deselected package libuser-perl.
Unpacking libuser-perl (from .../libuser-perl_1.6-2_all.deb) ...
Selecting previously deselected package libfile-slurp-perl.
Unpacking libfile-slurp-perl (from .../libfile-slurp-perl_9999.12-2_all.deb) ...
Selecting previously deselected package libwww-search-perl.
Unpacking libwww-search-perl (from .../libwww-search-perl_2.50.70.debian.2_all.deb) ...
Selecting previously deselected package python-fpconst.
Unpacking python-fpconst (from .../python-fpconst_0.7.2-4_all.deb) ...
Selecting previously deselected package python-soappy.
Unpacking python-soappy (from .../python-soappy_0.12.0-4_all.deb) ...
Selecting previously deselected package hddtemp.
Unpacking hddtemp (from .../hddtemp_0.3-beta15-45_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up python-evolution (2.28.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-evolution (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-gtkmozembed (2.25.3-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gtkmozembed (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-lxml (2.1.5-1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-lxml (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-numpy (1:1.3.0-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-reportlab (2.3-0ubuntu1) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-reportlab (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-reportlab-accel:
 python-reportlab-accel depends on python-reportlab (>= 2.3-0ubuntu1); however:
  Package python-reportlab is not configured yet.
dpkg: error processing python-reportlab-accel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uniconvertor:
 python-uniconvertor depends on python-reportlab; however:
  Package python-reportlab is not configured yet.
dpkg: error processing python-uniconvertor (--configure):
 dependency problems - leaving unconfigured
Setting up python-numeric (24.2-9ubuntu1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already

Setting up gdesklets (0.36.1-2ubuntu1) ...
/usr/lib/gdesklets/sensor/Sensor.py:82: SyntaxWarning: assertion is always true, perhaps remove parentheses?
  assert(self.__id, "The ID is invalid in the constructor.")

Setting up gdesklets-data (0.35.6-3) ...
Setting up libcarp-clan-perl (6.00-1) ...
Setting up libbit-vector-perl (6.6-1) ...
Setting up libdate-manip-perl (5.54-1) ...
Setting up libuser-perl (1.6-2) ...
Setting up libfile-slurp-perl (9999.12-2) ...
Setting up libwww-search-perl (2.50.70.debian.2) ...
Setting up python-fpconst (0.7.2-4) ...

Setting up python-soappy (0.12.0-4) ...

Setting up hddtemp (0.3-beta15-45) ...
 * Starting disk temperature monitoring daemon hddtemp:
   ...done.

Processing triggers for menu ...
Processing triggers for python-support ...
Errors were encountered while processing:
 python-evolution
 python-gtkmozembed
 python-lxml
 python-numpy
 python-reportlab
 python-reportlab-accel
 python-uniconvertor
[/INDENT]
HELP!
Thanks in advance!

---

### Post by lidex on 2010-02-23
Try this in a terminal:
```
sudo dpkg --configure -a
```

"Applications>Accessories>Terminal"

---

### Post by Sandy Al on 2010-02-24
Hey thanks for your help - this is what it gave me:
:(
sandy@sandy-laptop:~$ sudo dpkg --configure -a
[sudo] password for sandy: 
Setting up python-lxml (2.1.5-1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-lxml (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-reportlab (2.3-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-reportlab (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-reportlab-accel:
 python-reportlab-accel depends on python-reportlab (>= 2.3-0ubuntu1); however:
  Package python-reportlab is not configured yet.
dpkg: error processing python-reportlab-accel (--configure):
 dependency problems - leaving unconfigured
Setting up python-numpy (1:1.3.0-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-gtkmozembed (2.25.3-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gtkmozembed (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-uniconvertor:
 python-uniconvertor depends on python-reportlab; however:
  Package python-reportlab is not configured yet.
dpkg: error processing python-uniconvertor (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-lxml
 python-reportlab
 python-reportlab-accel
 python-numpy
 python-gtkmozembed
 python-uniconvertor

---

### Post by lidex on 2010-02-25
Try this:
```
sudo dpkg --force all --remove
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Sandy Al on 2010-02-26
Hmmm? did the first command, and this was the result.  Thanks again for your help...

sandy@sandy-laptop:~$ sudo dpkg --force all --remove
[sudo] password for sandy: 
dpkg: --remove needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
sandy@sandy-laptop:~$ 
:(

---

### Post by lidex on 2010-02-26
Ah, sorry.
```
sudo dpkg --force all --remove python-lxml python-reportlab python-reportlab-accel python-numpy python-gtkmozembed python-uniconvertor

```

All one line, BTW

---

### Post by Sandy Al on 2010-03-01
Thanks lindex,
I ran into some other troubles with nautilus, so decided to re-install ubuntu.

And that fixed it :)

Thanks for all your help.  This forum is awesome!

---

