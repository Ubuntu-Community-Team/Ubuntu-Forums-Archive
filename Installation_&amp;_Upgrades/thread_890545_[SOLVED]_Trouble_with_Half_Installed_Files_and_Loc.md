---
title: "[SOLVED] Trouble with Half Installed Files and Lock Files"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by kpk on 2008-08-15
Hi,

I am new to Ubuntu and my learning curve is yet to grow [novice user :-)]! I was running the update manager to install some of the available updates. The system restarted all of a sudden and i presume that the update manager crashed. I brought up those services back using $ sudo dpkg --configure -a command. I tried all possible options available in the forums, however the following issues remain unresolved. Could you please help me to:
1. Repair/Install the package 'libkpathsea4' without errors.
2. Remove unnecessary locks that were enabled during the update process.
--------------------------------------------------------------------------
~$ sudo dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 libkpathsea4         TeX Live: path search library for TeX (runtime part)
--------------------------------------------------------------------------
~$ sudo apt-get install libkpathsea4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  avm-fritz-firmware-2.6.22-14
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libkpathsea4
1 upgraded, 0 newly installed, 0 to remove and 118 not upgraded.
1 not fully installed or removed.
Need to get 109kB of archives.
After unpacking 0B of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libkpathsea4 2007-12ubuntu3.1 [109kB]
Fetched 109kB in 5s (21.7kB/s)       
(Reading database ... dpkg: error processing /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb (--unpack):
 files list file for package `libkpathsea4' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
--------------------------------------------------------------------------
~$ apt-get -f update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
--------------------------------------------------------------------------
~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
--------------------------------------------------------------------------

Sincere Apologies for my silly questions, but I would be grateful if anyone could help me get my way out!

---

### Post by iaculallad on 2008-08-15
On your terminal:

```
sudo dpkg --configure -a 
sudo apt-get autoclean

```

---

### Post by kpk on 2008-08-15
Thanks a bunch iaculallad! 

Yeah! Did try those commands and they're working :). However '~$ sudo apt-get install libkpathsea4' still gives me the same error as shown above :confused:. Any pointers on that??

---

### Post by kpk on 2008-08-15
Error:

~$ sudo apt-get install libkpathsea4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  avm-fritz-firmware-2.6.22-14
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libkpathsea4
1 upgraded, 0 newly installed, 0 to remove and 118 not upgraded.
1 not fully installed or removed.
Need to get 0B/109kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb (--unpack):
 files list file for package `libkpathsea4' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by iaculallad on 2008-08-15
> **kpk said:**
> Thanks a bunch iaculallad! 

Yeah! Did try those commands and they're working :). However '~$ sudo apt-get install libkpathsea4' still gives me the same error as shown above :confused:. Any pointers on that??

Ok. Try this on your terminal:


First option is to force install:

```
sudo dpkg -i --force-all /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb
```

If it still fails, try deleting the cache package and re-installing it.

```
sudo rm /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb
sudo apt-get update
sudo apt-get install -f

```

then

```
sudo apt-get install libkpathsea4
```

---

### Post by kpk on 2008-08-15
Hi..
I got the following errors.. Sorry to keep bugging you again and again!:(
```
sudo dpkg -i --force-all /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb (--install):
 files list file for package `libkpathsea4' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb
-------------------------------------------------------------------------------------------------------------
```
sudo rm /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb
sudo apt-get update
sudo apt-get install -f
```
~$ sudo rm /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb
[Executed without any errors]
~$ sudo apt-get update
[Executed without any errors]
~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  avm-fritz-firmware-2.6.22-14
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 119 not upgraded.
1 not fully installed or removed.
Need to get 0B/109kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3_i386.deb (--unpack):
 files list file for package `libkpathsea4' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
-------------------------------------------------------------------------------------------------------------
```
sudo apt-get install libkpathsea4
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  avm-fritz-firmware-2.6.22-14
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libkpathsea4
1 upgraded, 0 newly installed, 0 to remove and 118 not upgraded.
1 not fully installed or removed.
Need to get 109kB of archives.
After unpacking 0B of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libkpathsea4 2007-12ubuntu3.1 [109kB]
Fetched 109kB in 4s (22.9kB/s)       
(Reading database ... dpkg: error processing /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb (--unpack):
 files list file for package `libkpathsea4' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libkpathsea4_2007-12ubuntu3.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by iaculallad on 2008-08-15
Ok, try this other option:

```
sudo rm /var/lib/dpkg/info/libkpathsea4.list
```

Then:

```
sudo apt-get remove libkpathsea4
sudo apt-get install libkpathsea4

```

---

### Post by kpk on 2008-08-15
```
sudo rm /var/lib/dpkg/info/libkpathsea4.list
```
Executed without any errors...
--- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- 
```
sudo apt-get remove libkpathsea4
```
~$ sudo apt-get remove libkpathsea4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  avm-fritz-firmware-2.6.22-14
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  evince libkpathsea4 ubuntu-desktop
0 upgraded, 0 newly installed, 3 to remove and 117 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 6631kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `libkpathsea4' missing, assuming package has no files currently installed.
dpkg: error processing ubuntu-desktop (--remove):
 files list file for package `libpoppler-glib2' is missing final newline
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

---

### Post by iaculallad on 2008-08-15
Apply the same process whenever it says something about newline error:

> *** list file for package `libpoppler-glib2' is missing final newline

Again in your terminal, this time use **libpoppler-glib2**L

```
sudo rm /var/lib/dpkg/info/libpoppler-glib2.list
```

then:

```
sudo apt-get install libkpathsea4
```

---

### Post by kpk on 2008-08-15
A '~$ sudo dpkg -C' gave the following results:

```
~$ sudo dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 libkpathsea4         TeX Live: path search library for TeX (runtime part)
```

Thanks yaar! I was down after trying all possible options on my own... but the ur support at this forum has really brought me alive... i'm raring to get this done with ur support.

---

### Post by iaculallad on 2008-08-15
With that error message, try doing this:

```
sudo apt-get install linuxdoc-tools-latex libkpathsea4 tetex-base tetex-bin tetex-extra latex-ucs kile imagemagick ps2eps
```

---

### Post by kpk on 2008-08-15
:) Thankssssssssssss a million Friend :)
The issue is resolved!
Kudos to You...
You made my day...

---

### Post by iaculallad on 2008-08-15
> **kpk said:**
> :) Thankssssssssssss a million Friend :)
The issue is resolved!
Kudos to You...
You made my day...

You're welcome. I'm glad you made it work.

---

### Post by kpk on 2008-08-15
> **iaculallad said:**
> With that error message, try doing this:

```
sudo apt-get install linuxdoc-tools-latex libkpathsea4 tetex-base tetex-bin tetex-extra latex-ucs kile imagemagick ps2eps
```

Didnt try this one though! 
Your suggestion in the previous post fixed the issue... 
~$ sudo dpkg -C didn't throw any warnings. Hope it worked...Please let me know if I need to run the above command...

---

### Post by iaculallad on 2008-08-15
> **kpk said:**
> Didnt try this one though! 
Your suggestion in the previous post fixed the issue... 
~$ sudo dpkg -C didn't throw any warnings. Hope it worked...Please let me know if I need to run the above command...

No need if the problem was already resolved. You can skip that process.

---

### Post by kpk on 2008-08-15
> **iaculallad said:**
> No need if the problem was already resolved. You can skip that process.

Sure! As You say sir!! =D>

---

