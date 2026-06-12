---
title: "Easyubuntu install errors"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by frprinterwiz on 2006-09-17
error when trying to install easyubuntu
> 
System sanity check: Failed!
Errors:
--------
ln: creating symbolic link `/Reader/intellinux/lib/libORBit-2.so' to `/usr/lib/libORBit-2.so.0': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libbonobo-2.so' to `/usr/lib/libbonobo-2.so.0': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libbonobo-activation.so' to `/usr/lib/libbonobo-activation.so.4': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libgnomespeech.so' to `/usr/lib/libgnomespeech.so.7': No such file or directory
dpkg: error processing adobereader-enu (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 adobereader-enu
E: Sub-process /usr/bin/dpkg returned an error code (1)

EasyUbuntu is now trying to run 'dpkg --configure -a'
System sanity check: Failed!
Errors:
--------
ln: creating symbolic link `/Reader/intellinux/lib/libORBit-2.so' to `/usr/lib/libORBit-2.so.0': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libbonobo-2.so' to `/usr/lib/libbonobo-2.so.0': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libbonobo-activation.so' to `/usr/lib/libbonobo-activation.so.4': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libgnomespeech.so' to `/usr/lib/libgnomespeech.so.7': No such file or directory
dpkg: error processing adobereader-enu (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 adobereader-enu

EasyUbuntu will not run before these errors are fixed. Please fix them and try again


I tried finding the mentioned files/libraries in the repositories but no luck - am I using the wrong version of the program?  Please help!  Any suggestions are welcome

TIA

---

