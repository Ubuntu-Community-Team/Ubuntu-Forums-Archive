---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by a271828 on 2010-11-10
Doing:
> 
sudo apt-get update

After 

> 
sudo apt-get upgrade


Getting:

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up dahdi-dkms (1:2.2.1+dfsg-1ubuntu2) ...
Removing old dahdi-2.2.1+dfsg-1ubuntu2 DKMS files...

------------------------------
Deleting module version: 2.2.1+dfsg-1ubuntu2
completely from the DKMS tree.
------------------------------
Done.
Loading new dahdi-2.2.1+dfsg-1ubuntu2 DKMS files...
First Installation: checking all kernels...
Building for 2.6.31-16-generic and 2.6.32-22-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 2.6.32-22-generic

Error! Bad return status for module build on kernel: 2.6.32-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/dahdi/2.2.1+dfsg-1ubuntu2/build/ for more information.
dpkg: error processing dahdi-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of dahdi-linux:
 dahdi-linux depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dahdi:
 dahdi depends on dahdi-linux; however:
  Package dahdi-linux is not configured yet.
 dahdi depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                              Errors were encountered while processing:
while processing:
 dahdi-dkms
 dahdi-linux
 dahdi
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas how to fix this?

---

### Post by sikander3786 on 2010-11-11
Please try

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

and post the output.

---

### Post by a271828 on 2010-11-11
The problem was with:

> 
dahdi-dkms
dahdi-linux
dahdi


Those were not correctly installed before, so I did
> 
sudo apt-get purge dahdi-dkms dahdi-linux dahdi


So then 
> 
sudo apt-get upgrade 


Worked fine. 
Now I am trying to get asterisk installed again --
following 
[https://wiki.ubuntu.com/AsteriskOnUbuntu/Current]("https://wiki.ubuntu.com/AsteriskOnUbuntu/Current")
 -- and it is not successful.

For this

> 
sudo apt-get install asterisk sox asterisk-mysql asterisk-mp3 


I am getting:

> 
First Installation: checking all kernels...
Building only for 2.6.32-25-generic
Building for architecture x86_64
Building initial module for 2.6.32-25-generic

Error!  Build of dahdi_vpmadt032_loader.ko failed for: 2.6.32-25-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/dahdi/2.2.1+dfsg-1ubuntu2/build/ for more information.
dpkg: error processing dahdi-dkms (--configure):
 subprocess installed post-installation script returned error exit status 7
dpkg: dependency problems prevent configuration of dahdi-linux:
 dahdi-linux depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dahdi:
 dahdi depends on dahdi-linux; however:
  Package dahdi-linux is not configured yet.
 dahdi depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of asterisk:
 asterisk depends on dahdi; however:
  Package dahdi is not configured yet.


I could not find anything helpful in:
> 
/var/lib/dkms/dahdi/2.2.1+dfsg-1ubuntu2/build/


---

### Post by sikander3786 on 2010-11-12
> **sikander3786 said:**
> Please try

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

and post the output.
You need to try these commands and post the output.

The first one will try to install missing dependencies as you see in your error messages,

> dpkg: dependency problems prevent configuration of asterisk:

And the 2nd one will try to reconfigure all dpkg packages as there is an error regarding,

> dahdi depends on dahdi-linux; however:
Package dahdi-linux is not configured yet.

Regards.

---

### Post by a271828 on 2010-11-13
The second command fixed my issue for x64 architecture but not for x32.

I see strange error:

> 
 sudo apt-get install dahdi
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpq5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dahdi-dkms dahdi-linux
The following NEW packages will be installed:
  dahdi dahdi-dkms dahdi-linux
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/1,869kB of archives.
After this operation, 9,269kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package dahdi-dkms.
(Reading database ... 159720 files and directories currently installed.)
Unpacking dahdi-dkms (from .../dahdi-dkms_1%3a2.2.1+dfsg-1ubuntu2_all.deb) ...
Selecting previously deselected package dahdi-linux.
Unpacking dahdi-linux (from .../dahdi-linux_1%3a2.2.1+dfsg-1ubuntu2_all.deb) ...
Selecting previously deselected package dahdi.
Unpacking dahdi (from .../dahdi_1%3a2.2.1-0ubuntu2_i386.deb) ...
Processing triggers for doc-base ...
Processing 3 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up dahdi-dkms (1:2.2.1+dfsg-1ubuntu2) ...
Loading new dahdi-2.2.1+dfsg-1ubuntu2 DKMS files...
First Installation: checking all kernels...
Building for 2.6.31-16-generic and 2.6.32-22-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 2.6.32-22-generic

Error! Bad return status for module build on kernel: 2.6.32-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/dahdi/2.2.1+dfsg-1ubuntu2/build/ for more information.
dpkg: error processing dahdi-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of dahdi-linux:
 dahdi-linux depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dahdi:
 dahdi depends on dahdi-linux; however:
  Package dahdi-linux is not configured yet.
 dahdi depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
  No apport report written because the error message indicates its a followup error from a previous failure.
    Errors were encountered while processing:
 dahdi-dkms
 dahdi-linux
 dahdi
E: Sub-process /usr/bin/dpkg returned an error code (1)


>  sudo dpkg --configure -a
Setting up dahdi-dkms (1:2.2.1+dfsg-1ubuntu2) ...
Removing old dahdi-2.2.1+dfsg-1ubuntu2 DKMS files...

------------------------------
Deleting module version: 2.2.1+dfsg-1ubuntu2
completely from the DKMS tree.
------------------------------
Done.
Loading new dahdi-2.2.1+dfsg-1ubuntu2 DKMS files...
First Installation: checking all kernels...
Building for 2.6.31-16-generic and 2.6.32-22-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 2.6.32-22-generic

Error! Bad return status for module build on kernel: 2.6.32-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/dahdi/2.2.1+dfsg-1ubuntu2/build/ for more information.
dpkg: error processing dahdi-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of dahdi:
 dahdi depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dahdi-linux:
 dahdi-linux depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dahdi-dkms
 dahdi
 dahdi-linux



The content of

/var/lib/dkms/dahdi/2.2.1+dfsg-1ubuntu2/build/make.log
 
is:

> DKMS make.log for dahdi-2.2.1+dfsg-1ubuntu2 for kernel 2.6.32-22-generic (i686)
Sat Nov 13 10:10:10 EET 2010
You do not appear to have the sources for the 2.6.31-16-generic kernel installed.
make: *** [modules] Error 1


also
> 
uname -r
2.6.31-16-generic


Any ideas?

---

### Post by sikander3786 on 2010-11-13
Did you see this?

[http://www.jmkg.co.uk/page/2/](http://www.jmkg.co.uk/page/2/)

See the entry for 15 Apr/10 nearly in the middle of the page. It was intended for 9.10 but might still help.

---

### Post by a271828 on 2010-11-20
The problem was because of kernel version:

 > 2.6.31-16-generic

However 
> /lib/modules/2.6.31-16-generic

was missing while having:
> 
uname -r
2.6.31-16-generic


Another trick was that header for this kernel version were not anymore in Ubuntu 10.04

It took me a while to figure this out because

> 
sudo apt-get install linux-headers-`uname -r`


could not find the package.

Finally I realized that I had to add repository: 

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main

in order to get missing headers. Then I was able to build dahdi and all other stuff.

Why Ubuntu is not smart enough to catch this problem and fix it automatically?

---

