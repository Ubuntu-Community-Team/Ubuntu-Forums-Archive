---
title: "Broken? packages. How to remove?"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by kcsc on 2011-08-07
Hi folks
 
I have two packages that I installed some time ago when trying to fix lirc that now seem to be broken but non removable. Everytime I do anything with apt-get it has errors with these two packages. Here's an example:
 
htpc@htpc:~$ sudo apt-get upgrade
[sudo] password for htpc: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages have been kept back:
linux-backports-modules-alsa-maverick-generic linux-backports-modules-wireless-maverick-generic linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up nct677x-dkms (1.0.4-1yavdr1) ...
Removing old nct677x-1.0.4 DKMS files...
------------------------------
Deleting module version: 1.0.4
completely from the DKMS tree.
------------------------------
Done.
Loading new nct677x-1.0.4 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-25-generic
Building for architecture i686
Building initial module for 2.6.35-25-generic
Error! Bad return status for module build on kernel: 2.6.35-25-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nct677x/1.0.4/build/ for more information.
Traceback (most recent call last):
File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nct677x-dkms.0.crash'
dpkg: error processing nct677x-dkms (--configure):
subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
nct677x-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
htpc@htpc:~$ 
 
If I try to remove nct677x-dkms I get:
 
htpc@htpc:~$ sudo apt-get remove nct677x-dkms
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages were automatically installed and are no longer required:
python-alsaaudio python-pyasn1 cdparanoia python-html5lib python-freevo python-pygame python-kaa-base python-twisted-runner libsqlite0 freevo-data python-beautifulsoup
python-twisted-mail python-numpy python-kaa-metadata libsdl-ttf2.0-0 python-twisted-lore python-twisted-conch python-twisted-news python-twisted-words libenet0debian1
python-twisted python-sqlite libportmidi0 libblas3gf liblapack3gf python-kaa-imlib2 libimlib2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
nct677x-dkms
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 233kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 170922 files and directories currently installed.)
Removing nct677x-dkms ...
Error! There are no instances of module: nct677x
1.0.1 located in the DKMS tree.
dpkg: error processing nct677x-dkms (--remove):
subprocess installed pre-removal script returned error exit status 3
Errors were encountered while processing:
nct677x-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
htpc@htpc:~$ 
 
Is there a way to completely purge these?
 
Thanks

---

### Post by ~!geek!~ on 2011-08-07
As you have already tried to remove the packages, you may try fixing the broken packages using > sudo apt-get --fix-broken <packagename>
After that you may try:
> sudo apt-get autoremove

Now you can use:
> sudo apt-get purge <packagename>  to remove it completely.

---

### Post by kcsc on 2011-08-07
> **~!geek!~ said:**
> As you have already tried to remove the packages, you may try fixing the broken packages using 
After that you may try:
 
 
Now you can use:
to remove it completely.
 
This is what I get when I try --fix-broken:
 
[EMAIL="htpc@htpc:~$"]htpc@htpc:~$[/EMAIL] sudo apt-get --fix-broken nct667x-dkms
E: Invalid operation nct667x-dkms
[EMAIL="htpc@htpc:~$"]htpc@htpc:~$[/EMAIL] 

kcsc

---

