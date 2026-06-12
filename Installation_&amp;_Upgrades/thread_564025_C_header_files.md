---
title: "C header files"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by tbrothers on 2007-09-30
I've installed VMWare and am now trying to configure it.  I get to the point where ot's asking the following.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

I cannot seem to find what it's looking for.  The only directoriers under /usr/src are

linux-headers-2.6.20-16
linux-headers-2.6.20-16-generic
linux-source-2.6.20
rpm

I have pointed the config toward each of these folders but I get the following message.

The path "/usr/src/linux-source-2.6.20/include" is a kernel header file 
directory, but it does not contain the file "linux/version.h" as expected. 

When I CAT the file /prc/version I get the following

The path "/usr/src/linux-source-2.6.20/include" is a kernel header file 
directory, but it does not contain the file "linux/version.h" as expected. 

Can someone point me in the right direction.

Thanks,
Terry

---

### Post by snickers295 on 2007-10-01
> **tbrothers said:**
> I've installed VMWare and am now trying to configure it.  I get to the point where ot's asking the following.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

I cannot seem to find what it's looking for.  The only directoriers under /usr/src are

linux-headers-2.6.20-16
linux-headers-2.6.20-16-generic
linux-source-2.6.20
rpm

I have pointed the config toward each of these folders but I get the following message.

The path "/usr/src/linux-source-2.6.20/include" is a kernel header file 
directory, but it does not contain the file "linux/version.h" as expected. 

When I CAT the file /prc/version I get the following

The path "/usr/src/linux-source-2.6.20/include" is a kernel header file 
directory, but it does not contain the file "linux/version.h" as expected. 

Can someone point me in the right direction.

Thanks,
Terry
In the terminal type: sudo apt-get install  build-essential
then the directory its looking for is  /lib/modules/<kernelversion>/build/include

---

