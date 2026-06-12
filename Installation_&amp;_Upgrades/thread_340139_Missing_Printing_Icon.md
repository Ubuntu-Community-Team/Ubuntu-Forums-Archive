---
title: "Missing Printing Icon"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by MainFrame185 on 2007-01-16
Good Day,

I am using a pre-loaded version of Ubuntu in a virtual machine using VMWare. It is a scaled down distro used as a kiosk PC for hotel guests to access the Internet. I need to connect this machine to a network printer but the printing icon is missing from the System/Administration menu. I tried installing the "Printers" application, but that is something different and doesn't give me what I need.

Any idea of how I can restore this ion to my System/Administration menu? If not, can I et up a printer from the command line? If so, what is the syntax?

Thank you,

---

### Post by taurus on 2007-01-16
Maybe try

```
sudo aptitude update
sudo aptitude install printconf
```

---

### Post by MainFrame185 on 2007-01-16
No joy -- I get "sudo: aptitude: command not found"

Any other ideas?

---

### Post by taurus on 2007-01-16
You need to enable both universe and multiverse in /etc/apt/sources.list by removing the # in front of the lines with deb.

```
gksudo gedit /etc/apt/sources.list
```
Save the changes and run

```
sudo aptitude update
sudo aptitude install printconf
```
Otherwise, you can use webmin to configure your printer too.

---

### Post by MainFrame185 on 2007-01-16
All the lines with "deb" do not have a # in front of them.

???

---

### Post by taurus on 2007-01-16
Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by MainFrame185 on 2007-01-17
```
vmware@vmware-bavm:/etc/apt$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
vmware@vmware-bavm:/etc/apt$

```

Thanks for your assistance!

---

### Post by taurus on 2007-01-17
Do you get any error message when you run "sudo aptitude update" at all?

Remove the **us.** from all the repos in /etc/apt/sources.list and run those two commands again.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by MainFrame185 on 2007-01-17
I edited the sources.list file but I still get a "command not found" error when I try to run aptitude. What ever happened to apt get?

Thanks for your continued assistance

---

### Post by MainFrame185 on 2007-01-17
OK, I just completed the two commands by using apt-get vs aptitude:

```
vmware@vmware-bavm:/etc/apt$ sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [191B]
Get:2 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [191B]
Get:4 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:5 http://security.ubuntu.com breezy-security Release [44.6kB]
Get:6 http://archive.ubuntu.com breezy-backports Release.gpg [191B]
Get:7 http://us.archive.ubuntu.com breezy Release [30.9kB]
Get:8 http://archive.ubuntu.com breezy-updates Release [29.6kB]
Get:9 http://security.ubuntu.com breezy-security/main Packages [132kB]
Get:10 http://archive.ubuntu.com breezy Release [30.9kB]
Get:11 http://us.archive.ubuntu.com breezy/main Packages [585kB]
Get:12 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Get:13 http://archive.ubuntu.com breezy-updates/main Packages [59.5kB]
Get:14 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:15 http://archive.ubuntu.com breezy-updates/main Sources [18.8kB]
Get:16 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:17 http://archive.ubuntu.com breezy/universe Packages [2304kB]
Get:18 http://security.ubuntu.com breezy-security/restricted Packages [6355B]
Get:19 http://security.ubuntu.com breezy-security/main Sources [27.2kB]
Get:20 http://security.ubuntu.com breezy-security/restricted Sources [960B]
Get:21 http://security.ubuntu.com breezy-security/universe Packages [74.9kB]
Get:22 http://security.ubuntu.com breezy-security/universe Sources [7323B]
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Get:23 http://archive.ubuntu.com breezy/universe Sources [915kB]
Get:24 http://archive.ubuntu.com breezy-backports/main Packages [16.7kB]
Get:25 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:26 http://archive.ubuntu.com breezy-backports/universe Packages [31.8kB]
Get:27 http://archive.ubuntu.com breezy-backports/multiverse Packages [1521B]
Get:28 http://archive.ubuntu.com breezy-backports/main Sources [5185B]
Get:29 http://archive.ubuntu.com breezy-backports/restricted Sources [14B]
Get:30 http://archive.ubuntu.com breezy-backports/universe Sources [10.2kB]
Get:31 http://archive.ubuntu.com breezy-backports/multiverse Sources [701B]
Fetched 4354kB in 24s (177kB/s)
Reading package lists... Done
vmware@vmware-bavm:/etc/apt$ sudo apt-get install printconf
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cupsys-client
Suggested packages:
  kdeprint gtklp cupsys-pt xpp foo2zjs pnm2ppa
Recommended packages:
  cupsys-bsd
The following packages will be REMOVED:
  lprng printtool
The following NEW packages will be installed:
  cupsys-client printconf
0 upgraded, 2 newly installed, 2 to remove and 100 not upgraded.
Need to get 123kB of archives.
After unpacking 4055kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com breezy/universe printconf 0.7.4.15ubuntu1 [14.3kB]
Get:2 http://us.archive.ubuntu.com breezy/main cupsys-client 1.1.23-10ubuntu4 [108kB]
Fetched 123kB in 1s (92.3kB/s)

Preconfiguring packages ...
(Reading database ... 36808 files and directories currently installed.)
Removing printtool ...
Removing lprng ...
Selecting previously deselected package cupsys-client.
(Reading database ... 36744 files and directories currently installed.)
Unpacking cupsys-client (from .../cupsys-client_1.1.23-10ubuntu4_i386.deb) ...
Selecting previously deselected package printconf.
Unpacking printconf (from .../printconf_0.7.4.15ubuntu1_all.deb) ...
Setting up cupsys-client (1.1.23-10ubuntu4) ...

Setting up printconf (0.7.4.15ubuntu1) ...
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
If printconf was unable to install all of your printers, please visit
http://www.linuxprinting.org/ for printer information and support from fellow
users.

```

The installation seems to have been OK, but I still don't see the icon. 

???

Thanks for your continued assistance.

---

### Post by MainFrame185 on 2007-01-17
OK -- I installed all of the other recommended and suggested packages after installing printconf using apt-get install. I see the new icons for KDEPrint Fax, KJobViewer, PrintJobs (CUPS) but there is still no "Printing" icon! (Grrrrr) I think I am close here but may need a different package?

Any asistance you can provide would be much appriciated.

---

### Post by taurus on 2007-01-17
Click on the Printing icon and see if you can add a printer, new, to it.  Otherwise, install webmin and use it to add a printer for your system.

---

### Post by MainFrame185 on 2007-01-17
There is no printing icon! That's the problem. Any good how to's on installing webmin?

---

### Post by taurus on 2007-01-17
[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by MainFrame185 on 2007-01-17
OK, now Webmin is installed and running. When I try to install a printer I get this error message:

The spool directory /var/spool/lpd does not exist on your system, which indicates that the Linux print system is not installed. Either install the software for your chosen print system, or use the module configuration to change it.

I tried to use the module configuration link, but it didn't change anything. It's obvious that the linux printing system isn't installed. Do you know what package will install it?

---

### Post by taurus on 2007-01-17
Search in synaptic for lpd package.

```
kdesu synaptic
```

---

### Post by MainFrame185 on 2007-01-18
kdesu -- command not found.

---

### Post by taurus on 2007-01-18
Are you using KDE?

---

### Post by MainFrame185 on 2007-01-18
I don't know. How would I find that out?

---

### Post by taurus on 2007-01-18
Do you see the Ubuntu logo on the top left corner or the menu bar in at the bottom, just like Windows?  Otherwise, take a screenshot of your desktop and post it here.

---

