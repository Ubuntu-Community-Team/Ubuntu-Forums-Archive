---
title: "Cannot apt-get upgrade anything 10.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by efpob on 2010-10-11
Installed 10.10 on a fresh HDD,

tried to perform some updates,  but everytime it comes back with 

```
The following packages will be upgraded:
  ubuntu-tweak update-manager update-manager-core
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,902kB of archives.
After this operation, 8,192B disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main update-manager all 1:0.142.20 [812kB]
Get:2 http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main ubuntu-tweak all 0.5.7-1~maverick1 [896kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main update-manager-core amd64 1:0.142.20 [195kB]                             
Fetched 1,902kB in 12s (153kB/s)                                                                                                          
(Reading database ... 123311 files and directories currently installed.)
Preparing to replace update-manager 1:0.142.19 (using .../update-manager_1%3a0.142.20_all.deb) ...
Unpacking replacement update-manager ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.142.20_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/update-manager/check-new-release-gtk'
Preparing to replace update-manager-core 1:0.142.19 (using .../update-manager-core_1%3a0.142.20_amd64.deb) ...
Unpacking replacement update-manager-core ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid literal/lengths set'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.142.20_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/ubuntu-tweak_0.5.7-1~maverick1_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Processing triggers for python-central ...
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager_1%3a0.142.20_all.deb
 /var/cache/apt/archives/update-manager-core_1%3a0.142.20_amd64.deb
 /var/cache/apt/archives/ubuntu-tweak_0.5.7-1~maverick1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried apt-get clean, autoclean, dpkg -reconfigure -a, apt-get install -f

Can anyone help?

Thanks!

---

### Post by scpatl4now on 2010-10-11
Ive had the same problem I am trying to work through.  Synaptic suggested >sudo dpkg --configure -a 
which is at least giving me the list of updates...still freezing when installing though.

update:It took awhile but all seems well with mine now

---

### Post by efpob on 2010-10-12
tried that already - still having trouble :( - same errors

---

### Post by XenoPhoenix on 2010-10-13
Same issue here, nothing I've tried has seemed to resolve it :/ any ideas other than what has already been suggested above?

---

### Post by efpob on 2010-10-13
I just gave in and reinstalled.

Didn't click the install 3rd party addons during the install process, waited until afterwards

works fine now

---

### Post by efpob on 2010-10-15
spoke too soon - worked for a week, then it's back to this again

Tried installing tftp and got 

```

```pauladmin@sheldon:~$ sudo apt-get install tftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xinetd
The following NEW packages will be installed
  tftpd xinetd
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/170kB of archives.
After this operation, 500kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 168196 files and directories currently installed.)
Unpacking xinetd (from .../xinetd_1%3a2.3.14-7ubuntu3_amd64.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/xinetd_1%3a2.3.14-7ubuntu3_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./etc/init.d/xinetd'
Unpacking tftpd (from .../tftpd_0.17-17ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/tftpd_0.17-17ubuntu2_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/xinetd_1%3a2.3.14-7ubuntu3_amd64.deb
 /var/cache/apt/archives/tftpd_0.17-17ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by efpob on 2010-10-15
I tried downloading other debs from the net and double clicking or dpkg -i to install, and still get errors

I can successfully un-ar and un-tar the package, and if I share the file to another user, they can install from the share no problem

---

### Post by dino99 on 2010-10-15
use synaptic for your needs, not exotic debs found on the untrusted net, if you want a stable system.

---

### Post by efpob on 2010-10-15
the only one from the net is ubuntu tweak.

the updatemanager error and tftp error are in the repos

---

### Post by efpob on 2010-10-15
figured it out from another user's post - I had the Eset AV program running, once I uninstalled that, everything worked again :)

---

### Post by macrohard on 2010-10-16
Interesting......

I was having the same issue with with the ESET beta for Linux. I wonder if its something with one of their signature updates with Ubuntu 10.10. I am still running 10.04 with it and have not seen any issues when downloading from Synaptic. Current signature is 5538.

Uninstalling it from my Dell laptop also corrected the Update Manager issue I was havingthis evening. I have properly updated and now I am downloading the ESET beta again.

Hmmmm....looks like an ESET issue with the beta when trying to download a program through the software center. The program downloads and installs when ESET is uninstalled. Submitting a bug report to them....

---

