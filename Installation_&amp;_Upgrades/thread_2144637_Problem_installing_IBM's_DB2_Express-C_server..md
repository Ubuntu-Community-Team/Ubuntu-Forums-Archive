---
title: "Problem installing IBM's DB2 Express-C server."
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by haramraj on 2013-05-13
When I tried installing DB2 Express-C server on my Ubuntu 12.04. and when I ran the 'db2prereqcheck' I got the error message 


**==========================================================================**

**Checking DB2 prerequisites for DB2 database version "10.1.0.2" on operating system "Linux" **

**Validating "Linux distribution " ... **
**   Requireed minimum "UBUNTU" version: "10.04" **
**   Actual version: "12.04" **
**   Requirement matched. **

**Validating "kernel level " ... **
**   Required minimum operating system kernel level: "2.6.16". **
**   Actual operating system kernel level: "3.5.0". **
**   Requirement matched. **

**Validating "C++ Library version " ... **
**   Required minimum C++ library: "libstdc++.so.6" **
**   Standard C++ library is located in the following directory: "/usr/lib/i386-linux-gnu/libstdc++.so.6.0.16". **
**   Actual C++ library: "CXXABI_1.3.1" **
**   Requirement matched. **

**Validating "/lib/libpam.so*" ... **
**   DBT3514W  The db2prereqcheck utility failed to find the following 32-bit library file: "/lib/libpam.so*". **
**   WARNING : Requirement not matched. **
**Requirement not matched for DB2 database "Server" "". Version: "10.1.0.2". **
**Summary of prerequisites that are not met on the current system: **
**   DBT3514W  The db2prereqcheck utility failed to find the following 32-bit library file: "/lib/libpam.so*". **



**==========================================================================**

**Checking DB2 prerequisites for DB2 database version "10.1.0.0" on operating system "Linux" **

**Validating "Linux distribution " ... **
**   Requireed minimum "UBUNTU" version: "10.04" **
**   Actual version: "12.04" **
**   Requirement matched. **

**Validating "kernel level " ... **
**   Required minimum operating system kernel level: "2.6.16". **
**   Actual operating system kernel level: "3.5.0". **
**   Requirement matched. **

**Validating "C++ Library version " ... **
**   Required minimum C++ library: "libstdc++.so.6" **
**   Standard C++ library is located in the following directory: "/usr/lib/i386-linux-gnu/libstdc++.so.6.0.16". **
**   Actual C++ library: "CXXABI_1.3.1" **
**   Requirement matched. **

**Validating "/lib/libpam.so*" ... **
**   DBT3514W  The db2prereqcheck utility failed to find the following 32-bit library file: "/lib/libpam.so*". **
**   WARNING : Requirement not matched. **
**Requirement not matched for DB2 database "Server" "". Version: "10.1.0.0". **
**Summary of prerequisites that are not met on the current system: **
**   DBT3514W  The db2prereqcheck utility failed to find the following 32-bit library file: "/lib/libpam.so*". **


**DBT3555E  The db2prereqcheck utility determined that the current platform is not supported by the following version of DB2 database: "9.8.0.4". **
**DBT3555E  The db2prereqcheck utility determined that the current platform is not supported by the following version of DB2 database: "9.8.0.3". **
**DBT3555E  The db2prereqcheck utility determined that the current platform is not supported by the following version of DB2 database: "9.8.0.2". **
[B]=================================================================================================
[/B]


I just want to ask, whether Ubuntu 12.04 is supported by IBM's DB2 server? and if yes, how to install DB2 properly?

---

### Post by dino99 on 2013-05-13
[http://edin.no-ip.com/blog/hswong3i/db2-express-c-10-1-ubuntu-12-04-howto](http://edin.no-ip.com/blog/hswong3i/db2-express-c-10-1-ubuntu-12-04-howto)

---

### Post by angryfirelord on 2013-06-01
The answer is shown in what was displayed from the tool.
```
DBT3514W The db2prereqcheck utility failed to find the following 32-bit library file: "/lib/libpam.so*". 
```
Install the 32-bit library.
```
sudo apt-get install libpam0g:i386
```

---

### Post by phlamingo on 2013-07-12
That's nice, but:

tommy@sabre - sudo apt-get install libpam0g:i386
[sudo] password for tommy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpam0g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So, why can't DB2 find the file?  Because I have libpam.so.0, in a subdirectory of /lib:

tommy@sabre - find /lib -name "*libpam*" -print
/lib/i386-linux-gnu/libpam.so.0.83.0
/lib/i386-linux-gnu/libpam.so.0
/lib/i386-linux-gnu/libpam_misc.so.0
/lib/i386-linux-gnu/libpamc.so.0.82.1
/lib/i386-linux-gnu/libpam_misc.so.0.82.0
/lib/i386-linux-gnu/libpamc.so.0

Linking libpam.so.0 still failed, but copying it to /lib worked.  It wouldn't surprise me if this causes a problem down the road, though.

Thank you.

---

### Post by ismaeliso on 2013-09-16
create a symlink to it


sudo ln -s /lib/i386-linux-gnu/libpam.so.0 /lib/libpam.so.0

---

