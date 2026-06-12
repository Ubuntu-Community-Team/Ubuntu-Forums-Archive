---
title: "Install wireless driver"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by Badgermc on 2007-01-15
I found a Broadcom Linux driver. I got it all unpacked and installed I think. The instructions that came with it are as follows:

Building Driver From TAR File
=============================

The following are general guidelines for installing the driver.

1. Create a directory and extract the files:

   tar xvzf b44-<version>.tar.gz

2. Build the driver b44.o (or b44.ko) as a loadable module for the
running kernel:

   cd src
   make

3. Test the driver by loading it: 

   insmod b44.o
or
   insmod b44.ko (on 2.6.x kernels)
or
   insmod b44

4. Install the driver:

   make install

See RPM instructions above for the location of the installed driver.

5. To configure network protocol and address, refer to various Linux
documentations.

As I went in to Networking and turned the wireless card on it went through a configuration process but it still doesn't work. When I run lshw I get a DISABLED by the etho1.

What can I do?

Thanks for any help

---

### Post by teaker1s on 2007-01-15
remove it cd into directory
[COLOR="Red"]sudo make uninstall[/COLOR]
keep typing command until you get nothing more to remove
 follow the link in my signature for a broadcom setup that will work

---

