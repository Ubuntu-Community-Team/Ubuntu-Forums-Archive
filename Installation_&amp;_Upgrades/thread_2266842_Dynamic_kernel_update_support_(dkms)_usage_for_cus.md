---
title: "Dynamic kernel update support (dkms) usage for custom wifi driver?"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by chihwah_li on 2015-02-25
I use the following Ae6000 driver made by a linux programmer:
[http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/](http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/)

But I noticed that Linux kernel updates remove the AE6000 kernel module. Everytime I have to compile and re-install it.
After googling, I found that DKMS could help, but I noticed that some packages (Grpahics drivers) can be installed with the option --dkms.

Can I install above driver with DKMS? And how?

I found this: [https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS) hope this explains it well, otherwise I will reply ...

---

### Post by chihwah_li on 2015-02-25
I tried but I don get it. What am I doing wrong?

> chihwahli@chihwahli-MS-7641:~/mediatek_mt7610u_sta_driver_linux-64bit$ README dkms.conf lib src
README: command not found
chihwahli@chihwahli-MS-7641:~/mediatek_mt7610u_sta_driver_linux-64bit$ sudo cp -R . /usr/src/AE6000
[sudo] password for chihwahli: 
chihwahli@chihwahli-MS-7641:~/mediatek_mt7610u_sta_driver_linux-64bit$ sudo dkms add -m AE6000 -v 1.1
Error! Could not find module source directory.
Directory: /usr/src/AE6000-1.1 does not exist.
chihwahli@chihwahli-MS-7641:~/mediatek_mt7610u_sta_driver_linux-64bit$ sudo dkms add -m AE6000
Error! Invalid number of arguments passed.
Usage: add <module>/<module-version> or
       add -m <module>/<module-version> or
       add -m <module> -v <module-version>



Edit I copied the whole directory /mediatek_mt7610u_sta_driver_linux-64bit under /usr/src
As /usr/src/mediatek_mt7610u_sta_driver_linux-64bit

---

### Post by chihwah_li on 2015-02-25
Renamed the folder in usr/src --> /usr/src/AE6000-1.0
Now the command I get the following error:

> /usr/src$ sudo dkms add -m AE6000 -v 1.0
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified for record #0.
dkms.conf: Error! Directive 'DEST_MODULE_LOCATION' does not begin with
'/kernel', '/updates', or '/extra' in record #0.
Error! Bad conf file.
File: /usr/src/AE6000-1.0/dkms.conf
does not represent a valid dkms.conf file.




Edit: Above error is fixed by adding DEST_Module_location="/updates" to the dkms.conf file.

New error:
> chihwahli@chihwahli-MS-7641:/usr/src/AE6000-1.0$ sudo dkms install -m AE6000 -v 1.0

Creating symlink /var/lib/dkms/AE6000/1.0/source ->
                 /usr/src/AE6000-1.0

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....(bad exit status: 2)
MAKE=make -C src/ KERNELDIR=/lib/modules/3.13.0-46-generic/build....(bad exit status: 127)
ERROR (dkms apport): binary package for AE6000: 1.0 not found
Error! Bad return status for module build on kernel: 3.13.0-46-generic (x86_64)
Consult /var/lib/dkms/AE6000/1.0/build/make.log for more information.
chihwahli@chihwahli-MS-7641:/usr/src/AE6000-1.0$ 


---

### Post by chihwah_li on 2015-03-02
the following website has very good instructions about installing a hello world Kernel module, how to create, install and removw:
[http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html)

Instruction about creating a Makefile (not read yet, but required because the driver has many c files, header files, etc)
[http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/](http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/)

Website about using DKMS with clear instructions:
[https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging](https://wiki.kubuntu.org/Kernel/Dev/DKMSPackaging)
I was able to create the hello world kernel module, install it, access my custom module by letting it type hello world onto the screen, and remove the kernel module from DKMS again.

Hope it's usefull for you as it was for me!

---

