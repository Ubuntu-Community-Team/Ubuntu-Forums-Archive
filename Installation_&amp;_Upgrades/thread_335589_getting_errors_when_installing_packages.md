---
title: "getting errors when installing packages"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by presbp on 2007-01-10
here are the details of the error 

(Reading database ... 108950 files and directories currently installed.)
Unpacking libungif4g (from .../libungf4g_4.1.4-2_i386.deb) ...
Selecting previously deselected package libimlib2.
Unpacking libimlib2 (from .../libimlib2_1.2.1-2ubuntu1.2_i386.deb) ...
Selecting previously deselected package 3ddesktop.
Unpacking 3ddesktop (from .../3ddesktop_0.2.9-5.1ubuntu1_i386.deb) ...
Setting up clamav-base (0.88.4-lubuntu2.1) ...
chown: cannot access ` /var/run/clamav' : No such file or directory
dpkg: error processing clamav-base (--configure) ;
 subprocess post-installation script returned error exit status 1
Setting up libungif4g (4.1.4-2) ...

Setting up libimlib2 (1.2.1-2ubuntu1.2) ...

Setting up 3ddesktop (0.2.9-5.1ubuntu1) ...
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting yp clamav-base (0.88.4-1ubuntu12.1) ...
chown: cannot access ` /var/run/clamav' : No such file or directory
dpkg: error processing clamav-base (--configure) :
 subprocess post-installation script returned error exit status 1

Does that mean that the packages are partially installed, or are they installed but not working correctly and if so I think 2 programs did this before 3d desktop.  Is there any way I can find those that got these errors, uninstall them and reinstall them after the error is corrected.  Thank you very much.  I am starting to like Ubuntu and I just want to get it up and working.  I have installed automatix2, and downloaded a few package files, I am not sure but I think the google picasa and the backup and restore packages also gave me this error.  I have the video card and sound card working.   Thank you for your help.

---

### Post by arnieboy on 2007-01-10
> **presbp said:**
> here are the details of the error 

(Reading database ... 108950 files and directories currently installed.)
Unpacking libungif4g (from .../libungf4g_4.1.4-2_i386.deb) ...
Selecting previously deselected package libimlib2.
Unpacking libimlib2 (from .../libimlib2_1.2.1-2ubuntu1.2_i386.deb) ...
Selecting previously deselected package 3ddesktop.
Unpacking 3ddesktop (from .../3ddesktop_0.2.9-5.1ubuntu1_i386.deb) ...
Setting up clamav-base (0.88.4-lubuntu2.1) ...
chown: cannot access ` /var/run/clamav' : No such file or directory
dpkg: error processing clamav-base (--configure) ;
 subprocess post-installation script returned error exit status 1
Setting up libungif4g (4.1.4-2) ...

Setting up libimlib2 (1.2.1-2ubuntu1.2) ...

Setting up 3ddesktop (0.2.9-5.1ubuntu1) ...
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting yp clamav-base (0.88.4-1ubuntu12.1) ...
chown: cannot access ` /var/run/clamav' : No such file or directory
dpkg: error processing clamav-base (--configure) :
 subprocess post-installation script returned error exit status 1

Does that mean that the packages are partially installed, or are they installed but not working correctly and if so I think 2 programs did this before 3d desktop.  Is there any way I can find those that got these errors, uninstall them and reinstall them after the error is corrected.  Thank you very much.  I am starting to like Ubuntu and I just want to get it up and working.  I have installed automatix2, and downloaded a few package files, I am not sure but I think the google picasa and the backup and restore packages also gave me this error.  I have the video card and sound card working.   Thank you for your help.

The above is a known bug in the clamav packages in Universe. To fix it, install clamav again as follows:
```
sudo apt-get install clamav-base
```

---

