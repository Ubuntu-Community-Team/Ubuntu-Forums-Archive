---
title: "Error in Backporting libitext-java for dapper"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by raghaven.kumar on 2008-05-13
Hi guys,

I am trying to backport libitext-java for dapper 6.06
from the source packages in the ubuntu repository :
[Ubuntu -- Details of source package libitext-java in dapper](http://packages.ubuntu.com/source/dapper/libitext-java)

I am using prevu to do that.
The thing is i dont want deps to be j2sdk1.4 but sun-java6-jdk, which i changed in the
*control* file. 
but then while writing the deb file prevu doesnt accept the java license and thus resulting in a error
```
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-00-0ubuntu1~dapper1_i386.deb) ...

sun-dlj-v1-1 license could not be presented
try 'dpkg-reconfigure debconf' to select a frontend other than noninteractive

dpkg: error processing /var/cache/apt/archives/sun-java6-jdk_6-00-0ubuntu1~dapper1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2

```

Can anyone tell me how to make prevu accept the license
or another way to install libitext-java while keeping java dep as sun-java6-jdk ?
PS:in debconf it is set to Dialog

---

### Post by raghaven.kumar on 2008-05-16
Thanks for Help
my colleague found the deb in [Index of /ubuntu/pool/universe/libi/libitext-java](http://archive.ubuntu.com/ubuntu/pool/universe/libi/libitext-java/)

---

