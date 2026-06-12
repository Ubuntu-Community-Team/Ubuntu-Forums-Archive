---
title: "Installing offline software"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by rituranjan on 2011-06-11
how to install offline software(if No Internet Connection)
apache
Firebird,
Gimp
Mono
etc

---

### Post by Herman on 2011-06-11
You'll need to have access to the internet somehow, at least temporarily, or have a friend who has internet access.  If you can get any kind of internet access at all, it is possible, (or at least it used to be the last time I checked), to obtain the entire Ubuntu Repositories on an .iso file and burn that to a CD-ROM. If you are interested in doing things that way, visit [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net) for more information, it's called 'APTonCD'.  

Another method that works or used to work would be to go download one of the DVD .iso files for Ubuntu, because the installation DVDs also contain all the software in the repositories.

To enable this idea to work, in older versions of Ubuntu we used to open our /etc/apt/sources.list files and 
remove the hash mark from that top line in your /etc/apt/sources.list referring to the CD-ROM. A hash mark looks like this: #    and it is used to block off a line of code in a text file that the computer reads, so by removing the hash mark you will be activating that line of code. 
After that whenever you want to install new software, Ubuntu will ask you to insert your Ubuntu DVD or CD-ROM. It will look there first and get what software it can from the DVD or CD before it will look on the internet (if connected) to try to download software from the repositories.

I'm sorry about being a little old fashioned and out of date. I'm sure there's a more modern way to enable downloading software from CD or DVD by clicking some software settings somewhere but I'm not sure exactly where until I get used to this new unity desktop, but I'm sure there's a setting around for it that can be just pointed to and clicked on. 
if you can't find it either, just open a terminal and go 'gksudo gedit /etc/apt/sources.list', 
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by M4570D0N on 2011-06-11
You can try SuperDeb Creator from the SuperOS repository

[http://hacktolive.org/wiki/SuperDeb_Creator](http://hacktolive.org/wiki/SuperDeb_Creator)

There's also apt-offline:
[http://apt-offline.alioth.debian.org/](http://apt-offline.alioth.debian.org/)

---

### Post by SidebySide on 2011-09-01
1. [http://www.webupd8.org/2009/11/get-list-of-packages-and-dependencies.html](http://www.webupd8.org/2009/11/get-list-of-packages-and-dependencies.html)

2. []("http://forum.ubuntu.ir/index.php/topic,15546.msg119657.html#msg119657")[COLOR=Red]**Keryx**[/COLOR]  is a portable, cross-platform package manager for APT-based (Ubuntu,  Debian) systems. It provides a graphical interface for gathering  updates, packages, and dependencies for offline computers. Keryx is free  and open source. You can get Keryx here: [http://keryxproject.org]("http://keryxproject.org/")

3. [Scripting]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") facility in Synaptic
[LEFT]Short instructions:
    * Launch Synaptic on the offline computer
    * Mark the packages you wish to install
    * Select File->Generate package download script
    * Save the script to your USB key
     * Take the USB key to an online Linux computer and run the script  there from the USB key. It will download only the packages required by  the offline computer to the USB key.
    * Insert the USB key into the offline computer
    * Launch Synaptic and click on File->Add downloaded packages
     * Select the directory on your USB key containing the downloaded  ".deb" files and press Open, The packages will be installed.
Note:  If you don't have access to a PC with GNU/Linux or  emulating/virtualizing GNU/Linux (Cygwin, VMware, VirtualBox, Qemu,  etc), just open the script with a text editor and enter all the URLs you  see in your browser to download the corresponding packages.
If  you have all the necessary libraries and/or dependencies, the simplest  way is of course to just download the .deb package you need, just as you  would with a Windows installer, and double-click the package to install  it with GDebi.
All Ubuntu packages are available on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages).[/LEFT]

4. [apt-get offline repository]("https://help.ubuntu.com/community/AptGet/Offline/Repository")

5. [http://sushi-huh.sourceforge.net/](http://sushi-huh.sourceforge.net/)

---

