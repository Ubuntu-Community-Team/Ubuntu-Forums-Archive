---
title: "Help a noob please: Installing TCL and TK"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by Skip2MyPou on 2007-07-20
I just downloaded the tar.gz files of the tcl and tk, and i have no idea what to do with them. I've been trying to do different things for a while now and i still can't figure it out. help me please.

---

### Post by PaulFr on 2007-07-20
Any reason why you do not wish to use the standard Ubuntu packages ?

If you have X-Windows up, you can use System -> Administration -> Synaptic Package Manager in the X-Windows GUI to search for and add tcl8.4 and tk8.4 packages (these versions are for Feisty 7.04). If you want to use the command line, start up a terminal and type ```
aptitude search tcl tk
```
or use Synaptic to search for tcl and tk packages, then pick the one you want (for Feisty this is tcl8.4 and tk8.4). If you want details, say about tck8.4, then use ```
aptitude show tcl8.4
``` for example. When you have picked the appropriate packages, then type ```
sudo apt-get install tcl8.4 tk8.4
``` where you can replace tcl8.4 and tk8.4 with the packages you picked.
------------------------------
If you need to use the latest .tar and .gz files which have not yet been released as Ubuntu packages, the typical model I follow for installing is (comments are following the # symbol, you do not type these in :-)) ```
<download .tar.gz file to Desktop using browser>
mkdir -p ~/dev                         # keep all source packages in ~/dev
mv ~/Desktop/<package_version>.tar.gz ~/dev        # Move the downloaded package to ~/dev
cd ~/dev                               # Change directory to ~/dev
gunzip -c <package_version>.tar.gz | tar xvpBf -   # Open the package
cd <package_version>                   # Change directory to ~/dev/<package_version>                    
more README                            # review any special requirements (check if any other READMEs)
more INSTALL                           # usually this is boilerplate text
./configure --help                     # to review the special options
./configure <with any options>         # This will setup the parameters for the build
make                                   # To build everything
make check                             # To run any tests
sudo make install                      # This will install it, typically in /usr/local

``` Of course, there are other places to store the source like /usr/local/src. Hope this helps.

---

### Post by tahitiwibble on 2007-07-24
I just installed Ubuntu 7.04 because of financial difficulties. WHY DIDN'T I DO THIS 15 YEARS AGO?

FANTASTIC :lolflag:  hassle free (more or less) out of the box wi-fi, printing, bluetooth etc. etc. FANTASTIC.

Anyway, if someone could help with my little problem I would be very grateful.

I am trying to install v.0.97RC1-1 Amsn and it won't terminate the installation. Please can someone tell me exactly how to obtain and install the necessary TCL "package" ?

Many, many thanks!

---

### Post by tahitiwibble on 2007-07-24
The error message at the end of the installation attempt.

dad@DadsUbuntu:~$ apt-get install tcl
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dad@DadsUbuntu:~$ sudo apt-get install tcl
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tcl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tcl has no installation candidate
dad@DadsUbuntu:~$

---

### Post by PaulFr on 2007-07-27
In general when you want a package, say tcl, I would suggest you first search for it in the list of packages using```
aptitude search tcl
```. In your case, the package of interest is tcl8.4 (latest version). So you should ```
sudo apt-get install tcl8.4
```There is no **tcl** package, so **sudo apt-get install tcl** will not succeed.

---

### Post by Shivad on 2007-08-22
Hello there!

I need some help installing the lattes version of amsn (amsn-0.97RC1-1.tcl84.x86.package) :confused:

This is the problem:
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 7.04 (apt-get) to install a package with similar name to 'tcl'. 

Error: Unable to prepare package AMSN MSN client.

I install everything with a similar name “tcl”.
I have done this too: sudo apt-get install tcl8.4, but nothing

I have less then 2 month on linux, I appreciate any help thank!

---

