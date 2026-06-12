---
title: "Gnuplot install/removal"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by mamboknave on 2014-09-30
While trying to clean-up the mess of multiple & unfunctional gnuplot installation (including manual removal of system dirs) something went really wrong to the point that now in the *whole* system I have only these cache files about gnuplot & gnuplot-x11 and NOTHING else:

$ find /* -name "*gnuplot*"
/var/cache/apt/archives/gnuplot-x11_4.4.3-0ubuntu3_amd64.deb
/var/cache/apt/archives/gnuplot-nox_4.4.3-0ubuntu3_amd64.deb

I'm with Ubuntu 12.04 and here below there are some more info.

Can some kind soul help me to restore the system for normal operation with Gnuplot?

============================================================

**If I try to purge, here is the result:**

$ sudo apt-get purge gnuplot
$
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnuplot is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ sudo apt-get purge gnuplot-x11
$
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnuplot-x11*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,667 kB disk space will be freed.
Do you want to continue [Y/n]? Y
[B]dpkg: error: cannot read info directory: No such file or directory 
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]

**If I try to install, here is the result:**

$ sudo apt-get install gnuplot
$
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gnuplot-doc
The following NEW packages will be installed:
  gnuplot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,068 B of archives.
After this operation, 21.5 kB of additional disk space will be used.
**dpkg: error: cannot read info directory: No such file or directory**

$ sudo apt-get install gnuplot-x11
$
Reading package lists... Done
Building dependency tree
Reading state information... Done
[B]gnuplot-x11 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

---

### Post by sudodus on 2014-09-30
Try with these commands, originally posted by oldfred

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a
```

Run each line one after another, and check if your system will manage gnuplot after that :-)

---

### Post by mamboknave on 2014-09-30
@Sudodus,
Thank You, but it did not work. 
I used 'sudo -i' on every command except the last two, as per your code (by the way, the last dpkg requires sudo also). Here is the overall output.

I truly need to resolve this problem and reinstall Gnuplot properly.

Any other idea?

=============================================================

**$ sudo -i apt-get autoclean**
Reading package lists... Done
Building dependency tree
Reading state information... Done

**$ sudo -i apt-get clean **
[nothing happened here, no output messages]

**$ sudo -i apt-get update**
[omitted: lots of Hit and Get on Packages]
Fetched 4,268 kB in 1min 38s (43.4 kB/s)
Reading package lists... Done

**$ sudo -i apt-get upgrade**
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**$ sudo -i apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**$ sudo apt-get -f install**
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**$ sudo dpkg --configure -a**
dpkg: error: cannot read info directory: No such file or directory

---

### Post by steeldriver on 2014-09-30
What "manual removal of system dirs" did you do, exactly? if you have removed the entire /var/lib/dpkg or /var/lib/dpkg/info directories it may be somewhat tricky to recover

---

### Post by sudodus on 2014-09-30
This does not look good

```
$ sudo dpkg --configure -a
dpkg: error: cannot read info directory: No such file or directory
```

I'm not sure where to continue. Let us hope someone who knows more than I can help you with the next step.

Edit: Thanks for chipping in, *steeldriver* :-)

---

### Post by mamboknave on 2014-09-30
Guys, thanks so much!
Actually /var/lib/dpkg/info was empty.
I am lucky enough to have the laptop configured nearly identically. I got the content of the info dir from the laptop and copied into the broken desktop.
It ~seems~ things are back to normal for now.
$ sudo dpkg --configure -a
runs with no output messages. The Synaptic pack manager says the gnuplot packages are OK.
Eventually, if things turn for the worse, I'll post again.
Again: Thanks a lot.

---

