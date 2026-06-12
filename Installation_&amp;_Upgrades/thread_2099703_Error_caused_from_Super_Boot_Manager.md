---
title: "Error caused from Super Boot Manager"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by Ninjex on 2012-12-30
The specs:

```
$ uname -a
Linux Ninjex 3.2.0-35-generic-pae #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 i686 athlon i386 GNU/Linux
```
The issue:

I have recently added a new repository for super-boot-manager and installed it.

The repository addition:
```
sudo add-apt-repository ppa:ingalex/super-boot-manager 
```After adding the repository, I then updated packages and installed super boot manager.

The instillation: 
```
sudo apt-get update && sudo apt-get install super-boot-manager
```Everything installed correctly and works perfectly on the system, but I now have an issue.

Anytime I try to install or remove anything I get the following error code:

```
dpkg returned an error code (1)
```I decided I would remove super boot manager.

Removing the repository:
```
sudo add-apt-repository -r ppa:ingalex/super-boot-manager
[sudo] password for Ninjex: 
You are about to remove the following PPA from your system:
 Super-Boot-Manger is a simple gui created with buc (http://buc.intilinux.com/wiki/index.php?title=Pagina_principale).
This  interface has the main purpose to make easier and intuitive  configuration of Grub, Burg (Brand-new Universal loadeR from GRUB) and  Plymouth. This interface also allows the installation of Burg, the  installation of many graphic themes for Burg and Plymouth and it allows  the creation of customized themes.

Project Official Webpage: http://www.sourceslist.eu/projects/super-boot-manager/
 More info: https://launchpad.net/~ingalex/+archive/super-boot-manager
Press [ENTER] to continue or ctrl-c to cancel removing it

```I pressed Enter and it sent me back to a blank line in the terminal, so I think it removed but I am not sure.

Next I decided to remove super-boot-manager.

Trying to remove super-boot-manager:
```
$ sudo apt-get remove --purge super-boot-manager 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plymouth-x11 librecode0 plowshare buc aview recode librhino-java rhino
  tesseract-ocr-eng
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  burg-theme-what-am-i super-boot-manager*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 16.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 206245 files and directories currently installed.)
Removing burg-theme-what-am-i ...
Generating burg.cfg ...
/usr/sbin/burg-probe: error: cannot stat `/boot/burg/locale'.
No path or device is specified.
Try `/usr/sbin/burg-probe --help' for more information.
dpkg: error processing burg-theme-what-am-i (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 burg-theme-what-am-i
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I followed up with the errors printed on the terminal and first tried the autoremove command given above.

Running apt-get autoremove:
```
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  burg-theme-what-am-i
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,163 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 206245 files and directories currently installed.)
Removing burg-theme-what-am-i ...
Generating burg.cfg ...
/usr/sbin/burg-probe: error: cannot stat `/boot/burg/locale'.
No path or device is specified.
Try `/usr/sbin/burg-probe --help' for more information.
dpkg: error processing burg-theme-what-am-i (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 burg-theme-what-am-i
E: Sub-process /usr/bin/dpkg returned an error code (1)
```So that was a total fail, so now we go try the /usr/sbin/burg-probe --help for more information.

Running the help command:
```
$ /usr/sbin/burg-probe --help
Usage: /usr/sbin/burg-probe [OPTION]... [PATH|DEVICE]

Probe device information for a given path (or device, if the -d option is given).

  -d, --device              given argument is a system device, not a path
  -m, --device-map=FILE     use FILE as the device map [default=/boot/burg/device.map]
  -t, --target=(fs|fs_uuid|drive|device|partmap|abstraction)
                             print filesystem module, GRUB drive, system device, partition map  module or abstraction module [default=fs]
  -h, --help                display this message and exit
  -V, --version             print version information and exit
  -v, --verbose             print verbose messages

```Now this is where I am lost..

Also, a little more intel, I tried to install the ppa purge tool, only to get the same error as above, so I don't think my system is even allowing me to install software.

Any help?

Thanks in advance,
Ninjex

---

### Post by gordintoronto on 2012-12-30
Remove the package before you remove the ppa.

---

### Post by Ninjex on 2012-12-30
I found the issue and fixed it. 
I decided to take a look inside of  the boot/burg directory and apparently it did not install correctly and I  only had 2 files, a grub.cfg and another file.

Turns out I was missing the /locale file that was given in one of the error outputs in the op above.

I simply ran:
```
cd boot/burg
sudo mkdir locale
```After  this, the uninstall of burg-theme-what-am-i was successful as well as  the removal of the repository and super-boot-manager!

---

