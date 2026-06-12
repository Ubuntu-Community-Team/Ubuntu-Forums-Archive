---
title: "Problems installing Java 6.0"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by _Stefan_3_ on 2008-10-10
hey,

i have some problems installing Java 6 on my Ubuntu Dapper Server.
Java 6 could not completely be installed.

Another apt-get install sun-java6-bin results into:

Reading package lists... Done
Building dependency tree... Done
sun-java6-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java6-bin (6-00-0ubuntu1~dapper1) ...
Could not create the Java virtual machine.
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

A deinstallation is not possible either. (Same error)

It seems to be depending on the JVM because of "Could not create the Java virtual machine."


Anyone who has an idea?

---

### Post by forger on 2008-10-10
dapper? hm.. try the following to remove it:
[COLOR="Red"]**WARNING! Use at your own risk!**[/COLOR]
```
dpkg -P --force-all sun-java6-bin
```

then try:
```
apt-get install --reinstall sun-java6-jre sun-java6-bin
```

---

### Post by _Stefan_3_ on 2008-10-10
ok, the first helped me to remove it.

But a new installation results in the same error.

Setting up sun-java6-bin (6-00-0ubuntu1~dapper1) ...
Could not create the Java virtual machine.
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)

I think it may be a problem when starting the JVM.
Is there enough free memory to start the jvm?
I have an v-server with 256 mb ram. That should be enough?!

I have a simple Webservice:
if a start the server an then try to start the client i am told:
Error occurred during initialization of VM
Could not reserve enough space for object heap
Could not create the Java virtual machine.

So the problem could be -Xmx<size>

Addon:
When setting xmx to 32m it works
But how can I pass this to the installation process???

---

