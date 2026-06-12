---
title: "PCTV200e on Karmic (with DKMS)"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by se2009 on 2009-10-26
Hello,

before Ubuntu Karmic it was a tedious work for me to get the PCTV 200e module working. I had to compile the whole v4l-dvb source code tree with the additional PCTV 200e module from Jakob Steidl. For every kernel update on Ubuntu I had to repeat the whole thing again.
After problems with compiling v4l-dvb on Karmic I decided to give  the DKMS feature a try. With DKMS I have achieved my goal to compile  the PCTV 200e module directly and not the whole source tree and get it compiled automatically when there is a kernel update. 

These are my steps:

   **_1. Prerequisites_**

      As prerequisite you need two debian packages installed:

[LIST]
[*]       DKMS
[*]       Linux source
[/LIST]
 
      DKMS should be installed by default. When not then type into a terminal
      ```
sudo aptitude install dkms
```      The Linux source package get installed with the command
      ```
sudo aptitude install linux-source
```      Please change into  directory with the linux-source package and extract it:
      ```
cd /usr/src;
tar xfvj linux-source-2.6.31.tar.bz2
```**_2. Get the PCTV 200e source code_**

      Download the _**[PCTV 200e source]("http://www.student.tugraz.at/jsteidl/stuff/pctv200e-20080525.tar.bz2")**_ from Jakob Steidl into** /usr/src**. Then do following steps:
      ```
cd /usr/src;
tar xfvj pctv200e-20080525.tar.bz2
```_**3. Prepare the PCTV 200e module**_

      Add following files to the extracted PCTV 200e module directory **(/usr/src/pctv200e-20080520)**:
[B]  
dkms.conf[/B]

      ```
PACKAGE_NAME="pctv200e";
PACKAGE_VERSION="20080520";
BUILT_MODULE_NAME[0]="pctv200e";
DEST_MODULE_LOCATION[0]="/kernel/drivers/media/dvb/dvb-usb/";
AUTOINSTALL="yes";
```[B]
      Makefile[/B]

      ```
obj-m += pctv200e.o
KERNELSOURCE="/usr/src/linux-source-`uname -r | sed 's/-.*//'`/drivers/media";
EXTRA_CFLAGS += -I${KERNELSOURCE}/dvb/dvb-usb
EXTRA_CFLAGS += -I${KERNELSOURCE}/dvb/frontends
EXTRA_CFLAGS += -I${KERNELSOURCE}/common/tuners
EXTRA_CFLAGS += -I${KERNELSOURCE}/dvb/dvb-core
```[B]
      pctv200e_dkms.patch[/B]

      ```
--- pctv200e-20080520/pctv200e.c    2008-05-25 19:40:56.000000000 +0200
+++ ../pctv200e-20080520/pctv200e.c    2009-10-25 02:31:21.193950266 +0200
@@ -542,7 +542,7 @@
       
  static struct usb_device_id pctv200e_table [] = {
             { USB_DEVICE(USB_VID_PINNACLE, USB_PID_PCTV_200E) },
-        { USB_DEVICE(USB_VID_PINNACLE, USB_PID_PCTV_60E) },
+          //{ USB_DEVICE(USB_VID_PINNACLE, USB_PID_PCTV_60E) },
               { }        /* Terminating entry */
  };
  MODULE_DEVICE_TABLE (usb, pctv200e_table);
@@ -602,9 +602,9 @@
  };
       
  static struct usb_driver pctv200e_driver = {
-#if LINUX_VERSION_CODE <=  KERNEL_VERSION(2,6,15)
-    .owner        = THIS_MODULE,
-#endif
+//#if LINUX_VERSION_CODE <=  KERNEL_VERSION(2,6,15)
+//    .owner        = THIS_MODULE,
+//#endif
           .name        = "dvb_usb_pctv200e",
           .probe        = pctv200e_probe,
           .disconnect     = dvb_usb_device_exit,
```      To avoid errors during  the build process of the PCTV 200e module four lines of code have to be commented out in the file **pctv200e.c**. Therefore type following command into the terminal
      ```
patch < pctv200e_dkms.patch
```For the patch command you have to  be still in the directory of the extracted PCTV 200e module.

   _**4. Activate the PCTV 200e module**_

      Three commands are left until all is fine.

      ```
sudo dkms add -m pctv200e -v 20080520;
sudo dkms build -m pctv200e -v 20080520;
sudo dkms install -m pctv200e -v 20080520
```O.K. - That's it.

---

