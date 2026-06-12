---
title: "dependency problems - leaving unconfigured"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by funkenstein on 2006-06-19
Hi there, I've just upgraded my GF's lappy from breezy to dapper. Everything works, but when I try to update the system, I get errors preventing me from doing so. 
As you'll see, the first error has to do with perl and locale settings, and after that all the errors have to do with things being unconfigured.
Finally, I've tried apt-get upgrade and dist-upgrade too. They all give me the similar results. 
Can anyone help? The lappy is still working, but it just doesn't feel right to not fix these problems. Thanks for any help you can give me :(

```
user@box:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Setting up libgnomeprint-data (0.37-11) ...
dpkg: error processing libgnomeprint-data (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgnomeprint15:
 libgnomeprint15 depends on libgnomeprint-data (= 0.37-11); however:
  Package libgnomeprint-data is not configured yet.
dpkg: error processing libgnomeprint15 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonobo2:
 libbonobo2 depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing libbonobo2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bonobo:
 bonobo depends on libbonobo2 (>= 1.0.22); however:
  Package libbonobo2 is not configured yet.
 bonobo depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing bonobo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgal23:
 libgal23 depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing libgal23 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml1.1-3:
 libgtkhtml1.1-3 depends on bonobo (>= 1.0.22); however:
  Package bonobo is not configured yet.
 libgtkhtml1.1-3 depends on libbonobo2 (>= 1.0.22); however:
  Package libbonobo2 is not configured yet.
 libgtkhtml1.1-3 depends on libgal23 (>= 0.24); however:
  Package libgal23 is not configured yet.
 libgtkhtml1.1-3 depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing libgtkhtml1.1-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libguppi16:
 libguppi16 depends on libgnomeprint15 (>= 0.37-10); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing libguppi16 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnucash:
 gnucash depends on bonobo (>= 1.0.22); however:
  Package bonobo is not configured yet.
 gnucash depends on libbonobo2 (>= 1.0.22); however:
  Package libbonobo2 is not configured yet.
 gnucash depends on libgal23 (>= 0.24); however:
  Package libgal23 is not configured yet.
 gnucash depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
 gnucash depends on libgtkhtml1.1-3 (>= 1.1.10); however:
  Package libgtkhtml1.1-3 is not configured yet.
 gnucash depends on libguppi16; however:
  Package libguppi16 is not configured yet.
dpkg: error processing gnucash (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnomeprint-data
 libgnomeprint15
 libbonobo2
 bonobo
 libgal23
 libgtkhtml1.1-3
 libguppi16
 gnucash
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libgnomeprint-data (0.37-11) ...
dpkg: error processing libgnomeprint-data (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgnomeprint15:
 libgnomeprint15 depends on libgnomeprint-data (= 0.37-11); however:
  Package libgnomeprint-data is not configured yet.
dpkg: error processing libgnomeprint15 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libguppi16:
 libguppi16 depends on libgnomeprint15 (>= 0.37-10); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing libguppi16 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bonobo:
 bonobo depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing bonobo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnucash:
 gnucash depends on bonobo (>= 1.0.22); however:
  Package bonobo is not configured yet.
 gnucash depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
 gnucash depends on libguppi16; however:
  Package libguppi16 is not configured yet.
dpkg: error processing gnucash (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonobo2:
 libbonobo2 depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing libbonobo2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgal23:
 libgal23 depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing libgal23 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml1.1-3:
 libgtkhtml1.1-3 depends on bonobo (>= 1.0.22); however:
  Package bonobo is not configured yet.
 libgtkhtml1.1-3 depends on libbonobo2 (>= 1.0.22); however:
  Package libbonobo2 is not configured yet.
 libgtkhtml1.1-3 depends on libgal23 (>= 0.24); however:
  Package libgal23 is not configured yet.
 libgtkhtml1.1-3 depends on libgnomeprint15 (>= 0.29-1); however:
  Package libgnomeprint15 is not configured yet.
dpkg: error processing libgtkhtml1.1-3 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnomeprint-data
 libgnomeprint15
 libguppi16
 bonobo
 gnucash
 libbonobo2
 libgal23
 libgtkhtml1.1-3

```

---

### Post by barbarian on 2006-06-19
hei, make sure that u have ubuntu-desktop installed before upgrading.

[I]sudo aptitude update
sudo aptitude install ubuntu-desktop[/I]

---

### Post by funkenstein on 2006-06-19
I made sure everything was up to date before the upgrade, including ubuntu-desktop. 

Ubuntu-desktop won't install right now anyway because of all the errors.

---

### Post by barbarian on 2006-06-19
Did u go [here]("https://wiki.ubuntu.com/DapperUpgrades?action=show&redirect=DapperUpgradeNotes")?

---

### Post by martinbriscoe on 2006-10-28
I have a similar problem with the dapper to edgy upgrade. I only have 3 dependency problems:

E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

These occur whatever method uf upgrade I try including aptitude, synaptic or update manager

Also rather strangly the upgrade has installed the kubuntu splash boot screen even tho I am using gnome.

Does any one know what I should do to overcome this and complete the installation?

Martin

---

### Post by daradib on 2006-10-29
I have the same problem.
First, i got the locale warnings from perl, but during apt-get install, several locales were installed and I received no more warnings. However, I received acpi-support and acpid errors, stating that they depended on each other and acpid was not configured. Another post tells me to run the following:

sudo /etc/init.d/acpid stop
sudo dpkg --configure -a

I will try and see if that works. The other major problem has to do with the the X server since I am running an ATI graphics card. The X server does not start. I have installed the xorg-driver-fglrx and configured, but the X server still gives me errors when I try to start it. I will check and see if this might be related to acpid and acpi-support.

I upgraded from Kubuntu 64-bit Dapper to Kubuntu 64-bit Edgy. However, I believe this is also a problem with Ubuntu as well.

---

### Post by daradib on 2006-10-29
I tried it and it worked. I did sudo apt-get install and apt-get upgrade and  the X server started successfully and I was successfully using Edgy.

---

