---
title: "Nvidia driver update failed"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by gbritton on 2010-12-28
Hi -- The Update Manager found a new version of my Nvidia driver (260.19.29) and tried to install it. However, the installation failed with a compiler error:


jerryb@TheBrittons:/home/britton$ sudo aptitude safe-upgrade
The following partially installed packages will be configured:
  nvidia-current nvidia-glx-185 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up nvidia-current (260.19.29-0ubuntu1~xup~maverick3) ...
update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-260.19.29 DKMS files...

------------------------------
Deleting module version: 260.19.29
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-260.19.29 DKMS files...
Building only for 2.6.35-24-generic
Building for architecture x86_64
Building initial module for 2.6.35-24-generic

Error! Bad return status for module build on kernel: 2.6.35-24-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/260.19.29/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidia-current.0.crash'
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of nvidia-glx-185:
 nvidia-glx-185 depends on nvidia-current; however:
  Package nvidia-current is not configured yet.
dpkg: error processing nvidia-glx-185 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-current
 nvidia-glx-185
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up nvidia-current (260.19.29-0ubuntu1~xup~maverick3) ...
update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-260.19.29 DKMS files...

------------------------------
Deleting module version: 260.19.29
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-260.19.29 DKMS files...
Building only for 2.6.35-24-generic
Building for architecture x86_64
Building initial module for 2.6.35-24-generic

Error! Bad return status for module build on kernel: 2.6.35-24-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/260.19.29/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidia-current.0.crash'
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of nvidia-glx-185:
 nvidia-glx-185 depends on nvidia-current; however:
  Package nvidia-current is not configured yet.
dpkg: error processing nvidia-glx-185 (--configure):
 dependency problems - leaving unconfigured

The make log reports:

/var/lib/dkms/nvidia-current/260.19.29/build/nv.c:550: internal compiler error: in label_rtx, at stmt.c:134
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[3]: *** [/var/lib/dkms/nvidia-current/260.19.29/build/nv.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia-current/260.19.29/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
(END) 


What should I do?

---

### Post by dino99 on 2010-12-28
you might not have dependencies issues, are you only running maverick ?

32/64 bits ?
which card ?

at that point, open synaptic then :

- deselect the nvidia ppa repo (third repo tab)
- remove/purge ALL the installed nvidia packages
- update
- reinstall nvidia-current

---

### Post by gbritton on 2010-12-28
I'm running 64 bit.  Card is:

VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)

No Nvidia PPAs in sight.  

I don't understand the question about running only Maverick.  Why would I run more than Maverick?

---

### Post by dino99 on 2010-12-28
> **gbritton said:**
> I'm running 64 bit.  Card is:

VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)

I don't understand the question about running only Maverick.  Why would I run more than Maverick?

No Nvidia PPAs in sight.: ******* Setting up nvidia-current (260.19.29-0ubuntu1~xup~maverick3) ... *****
how this one have come here ?

---

### Post by gbritton on 2010-12-28
> **dino99 said:**
> No Nvidia PPAs in sight.: ******* Setting up nvidia-current (260.19.29-0ubuntu1~xup~maverick3) ... *****
how this one have come here ?

From the installation of nvidia-current

---

### Post by gbritton on 2010-12-28
> **gbritton said:**
> From the installation of nvidia-current

Here is my list of sources:


$grep deb  /etc/apt/sources.list
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free

---

### Post by dino99 on 2010-12-28
> **gbritton said:**
> From the installation of nvidia-current

~xup-maverick is from x-swat ppa, so it has been removed, but not the installed package 

so, have you do these previous tasks:

- remove/purge ALL the installed nvidia packages
- update
- reinstall nvidia-current

this might remove what is causing these dependencies issues (modaliases)

---

### Post by gbritton on 2010-12-28
> **dino99 said:**
> ~xup-maverick is from x-swat ppa, so it has been removed, but not the installed package 

so, have you do these previous tasks:

- remove/purge ALL the installed nvidia packages
- update
- reinstall nvidia-current

this might remove what is causing these dependencies issues (modaliases)

Did that. No joy.  Actually, the last step still pulled from x-swat ppa

---

