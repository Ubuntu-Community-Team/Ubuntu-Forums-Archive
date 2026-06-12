---
title: "Can't install any updates 11.04"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by notanerd on 2011-09-24
Hi. I have been unable to install any of the updates that I have downloaded for more than a month now.
Update Manager downloads the updates but when it tries to install them it comes up with this error "Package Operation Failed" and whn you check the details is says this at the bottom


dpkg: error: parsing file '/var/lib/dpkg/status' near line 37640 package 'gnome-applets':
 'Depends' field, reference to 'gir1.2-gdkpixbuf-2.0': invalid architecture name 'i386': a value different from 'any' is currently not allowed

I have no idea what this means. Any ideas out there?

---

### Post by mörgæs on 2011-09-25
Let's try to get a better error message. Please boot the computer, close all windows which may open and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Please post the error messages, if any.

---

### Post by notanerd on 2011-09-26
Fetched 142 MB in 12min 52s (183 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 37640 package 'gnome-applets':
 'Depends' field, reference to 'gir1.2-gdkpixbuf-2.0': invalid architecture name 'i386': a value different from 'any' is currently not allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by mörgæs on 2011-09-27
Let's try removing the package which makes trouble:

```
sudo apt-get --purge remove gnome-applets
```

---

### Post by notanerd on 2011-09-27
didn't work i'm afraid


evan@evan-netbook:~$ sudo apt-get --purge remove gnome-applets
[sudo] password for evan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  desktop-base libbluray0 xfce4-appfinder libgarcon-1-0 tango-icon-theme
  libgarcon-common thunar-data gtk2-engines-xfce xfdesktop4-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-applets* ubuntu-desktop* ubuntu-netbook*
0 upgraded, 0 newly installed, 3 to remove and 122 not upgraded.
After this operation, 692 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error: parsing file '/var/lib/dpkg/status' near line 37640 package 'gnome-applets':
 'Depends' field, reference to 'gir1.2-gdkpixbuf-2.0': invalid architecture name 'i386': a value different from 'any' is currently not allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)
evan@evan-netbook:~$ sudo apt-get --purge remove gnome-applets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  desktop-base libbluray0 xfce4-appfinder libgarcon-1-0 tango-icon-theme
  libgarcon-common thunar-data gtk2-engines-xfce xfdesktop4-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-applets* ubuntu-desktop* ubuntu-netbook*
0 upgraded, 0 newly installed, 3 to remove and 122 not upgraded.
After this operation, 692 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error: parsing file '/var/lib/dpkg/status' near line 37640 package 'gnome-applets':
 'Depends' field, reference to 'gir1.2-gdkpixbuf-2.0': invalid architecture name 'i386': a value different from 'any' is currently not allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by mörgæs on 2011-09-27
Then I am out of ideas, sorry.

---

### Post by notanerd on 2011-10-01
Actually I can't install anything now, applications or updates! Help!

---

### Post by Old_Grey_Wolf on 2011-10-02
If you look in /var/lib/dpkg/ you will find a file with the name "status" and another named "status-old". Change the name of "status" to "status-bak". Then change the name of "status-old" to "status". Then try to update.

You will need to use sudo or gksudo the change the name of the file.

---

### Post by notanerd on 2011-10-02
ok so gedit allowed me save the file names to a different one, so 'status' became 'status-bak', 'status-old' became 'status'. It did not seem possible to delete other files so there is now 2 identical files, once called 'status-old' and the other called 'status'. 

When I ran update manager it just got stuck at 'waiting' and will not download anything

---

### Post by Old_Grey_Wolf on 2011-10-03
> **notanerd said:**
> ok so gedit allowed me save the file names to a different one, so 'status' became 'status-bak', 'status-old' became 'status'. It did not seem possible to delete other files so there is now 2 identical files, once called 'status-old' and the other called 'status'. 

When I ran update manager it just got stuck at 'waiting' and will not download anything

Are you saying you have 2 files named status-old and 2 files named status? You should have used gksudo nautilus or sudo mv to change the name of the files.

If you run the commands ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` and post the errors; then, we can see what it may be waiting on.

---

### Post by notanerd on 2011-10-11
OK, I changed the file names using gksudo nautilus, then ran the two commands you asked me to and it seems to have been successful. Terminal downloaded and installed a massive amount of updates with no errors. Thank you.
Do I now need to change the status files back to their original names or should I leave them as is?

---

### Post by Old_Grey_Wolf on 2011-10-12
Leave the files as is.

---

### Post by notanerd on 2011-10-13
OK thank you I will mark this thread as solved

---

