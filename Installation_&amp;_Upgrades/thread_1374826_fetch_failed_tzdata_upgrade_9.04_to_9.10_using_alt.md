---
title: "fetch failed tzdata upgrade 9.04 to 9.10 using alternate CD"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by tbink1 on 2010-01-07
Currently have 9.04 installed. Wanted to upgrade to 9.10.   Down loaded and burned alternate CD.   The desktop doesn't have internet access.  The upgrade failed and generated an error:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009s-0ubuntu0.9.10_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009s-0ubuntu0.9.10_all.deb) 404 Not Found [IP: 91.189.88.40 80]

I accessed: [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/) and don't see tzdata_2009s-0ubuntu0.9.10_all.deb

Is it possible edit/alter a script to point to correct file and get by this error? 
Thanks.

---

### Post by slakkie on 2010-01-07
run cdromupgrade with the --no-network option. For the correct syntax run:

./cdromupgrade --help

See also the upgrade ubuntu link in my sig.

---

### Post by tbink1 on 2010-01-07
This what I did in terminal window:
tbink1@tbink1-desktop:~$ cd /media
tbink1@tbink1-desktop:/media$ cd cdrom
tbink1@tbink1-desktop:/media/cdrom$ sudo ./cdromupgrade --without-network
[sudo] password for tbink1: 
Installing libnspr4-dev as dep of adobe-flashplugin
Installing libnspr4-0d as dep of libnspr4-dev
Installing libnss3-dev as dep of adobe-flashplugin
Installing libnss3-1d as dep of libnss3-dev
Installing libsqlite3-0 as dep of libnss3-1d
Installing libcurl3 as dep of adobe-flashplugin
Installing libgssapi-krb5-2 as dep of libcurl3
Installing libk5crypto3 as dep of libgssapi-krb5-2
Installing libkrb5support0 as dep of libk5crypto3
Installing libkrb5-3 as dep of libgssapi-krb5-2
Starting
Starting 2
Done
gpgv: Signature made Tue 27 Oct 2009 01:19:01 PM EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"

The above actions started a upgrade wizard.  Unfortunately the previously reported error reoccurred.  

I welcome additional recommendations.  Thank you.

---

### Post by slakkie on 2010-01-07
mmm, could you run *aptitude install tzdata/jaunty* and redo the upgrade?

Ow, crap, you don't have a internet connection. Download the tzdata package from packages.ubuntu.com and install it by doing dpkg -i tzdata_something.deb (or download the karmic version while you are at it).

---

