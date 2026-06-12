---
title: "xsane cant find scanner"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by cbob on 2010-05-16
Hello,

I cant find my scanner (Canon MP250). I have installed the printer and it works fine, this using the drivers from canon ([canon divers page]("http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP250%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&")) and installed the scanner drivers too. Im running:
```
$ uname -a
Linux ubuntu 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux

```Installed the drivers with
```
sudo dpkg --force-architecture -i package
```Have also installed the latest ***sane-backends***, built this from the source according to ([http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)).
```
$ scanimage -V
scanimage (sane-backends) 1.0.22git; backend version 1.0.22

```But scanner still cant be found using gives
```
$ sane-find-scanner -vv
This is sane-find-scanner from sane-backends 1.0.22git

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

searching for SCSI scanners:
checking /dev/scanner... failed to open (Invalid argument)
checking /dev/sg0... failed to open (Access to resource has been denied)
checking /dev/sg1... failed to open (Invalid argument)
checking /dev/sg2... failed to open (Invalid argument)
checking /dev/sg3... failed to open (Invalid argument)
checking /dev/sg4... failed to open (Invalid argument)
checking /dev/sg5... failed to open (Invalid argument)
checking /dev/sg6... failed to open (Invalid argument)
checking /dev/sg7... failed to open (Invalid argument)
checking /dev/sg8... failed to open (Invalid argument)
checking /dev/sg9... failed to open (Invalid argument)
checking /dev/sga... failed to open (Invalid argument)
checking /dev/sgb... failed to open (Invalid argument)
checking /dev/sgc... failed to open (Invalid argument)
checking /dev/sgd... failed to open (Invalid argument)
checking /dev/sge... failed to open (Invalid argument)
checking /dev/sgf... failed to open (Invalid argument)
checking /dev/sgg... failed to open (Invalid argument)
checking /dev/sgh... failed to open (Invalid argument)
checking /dev/sgi... failed to open (Invalid argument)
checking /dev/sgj... failed to open (Invalid argument)
checking /dev/sgk... failed to open (Invalid argument)
checking /dev/sgl... failed to open (Invalid argument)
checking /dev/sgm... failed to open (Invalid argument)
checking /dev/sgn... failed to open (Invalid argument)
checking /dev/sgo... failed to open (Invalid argument)
checking /dev/sgp... failed to open (Invalid argument)
checking /dev/sgq... failed to open (Invalid argument)
checking /dev/sgr... failed to open (Invalid argument)
checking /dev/sgs... failed to open (Invalid argument)
checking /dev/sgt... failed to open (Invalid argument)
checking /dev/sgu... failed to open (Invalid argument)
checking /dev/sgv... failed to open (Invalid argument)
checking /dev/sgw... failed to open (Invalid argument)
checking /dev/sgx... failed to open (Invalid argument)
checking /dev/sgy... failed to open (Invalid argument)
checking /dev/sgz... failed to open (Invalid argument)
  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

searching for USB scanners:
checking /dev/usb/scanner... failed to open (Invalid argument)
checking /dev/usb/scanner0... failed to open (Invalid argument)
checking /dev/usb/scanner1... failed to open (Invalid argument)
checking /dev/usb/scanner2... failed to open (Invalid argument)
checking /dev/usb/scanner3... failed to open (Invalid argument)
checking /dev/usb/scanner4... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner5... failed to open (Invalid argument)
checking /dev/usb/scanner7... failed to open (Invalid argument)
checking /dev/usb/scanner8... failed to open (Invalid argument)
checking /dev/usb/scanner9... failed to open (Invalid argument)
checking /dev/usb/scanner10... failed to open (Invalid argument)
checking /dev/usb/scanner11... failed to open (Invalid argument)
checking /dev/usb/scanner12... failed to open (Invalid argument)
checking /dev/usb/scanner13... failed to open (Invalid argument)
checking /dev/usb/scanner14... failed to open (Invalid argument)
checking /dev/usb/scanner15... failed to open (Invalid argument)
checking /dev/usbscanner... failed to open (Invalid argument)
checking /dev/usbscanner0... failed to open (Invalid argument)
checking /dev/usbscanner1... failed to open (Invalid argument)
checking /dev/usbscanner2... failed to open (Invalid argument)
checking /dev/usbscanner3... failed to open (Invalid argument)
checking /dev/usbscanner4... failed to open (Invalid argument)
checking /dev/usbscanner5... failed to open (Invalid argument)
checking /dev/usbscanner6... failed to open (Invalid argument)
checking /dev/usbscanner7... failed to open (Invalid argument)
checking /dev/usbscanner8... failed to open (Invalid argument)
checking /dev/usbscanner9... failed to open (Invalid argument)
checking /dev/usbscanner10... failed to open (Invalid argument)
checking /dev/usbscanner11... failed to open (Invalid argument)
checking /dev/usbscanner12... failed to open (Invalid argument)
checking /dev/usbscanner13... failed to open (Invalid argument)
checking /dev/usbscanner14... failed to open (Invalid argument)
checking /dev/usbscanner15... failed to open (Invalid argument)
libusb not available
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.
  # SANE has been built without libusb support. This may be a reason
  # for not detecting USB scanners. Read README for more details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
done
```I'm quite certaine that I have libusb installed (though not sure which one sane uses):
```
$ aptitude search libusb
p   libusb++-0.1-4c2                - userspace C++ USB programming library     
p   libusb++-dev                    - userspace C++ USB programming library deve
i   libusb-0.1-4                    - userspace USB programming library         
i   libusb-1.0-0                    - userspace USB programming library         
p   libusb-1.0-0-dev                - userspace USB programming library developm
i   libusb-dev                      - userspace USB programming library developm
p   libusbip-dev                    - USB device sharing system over IP network 
p   libusbip0                       - USB device sharing system over IP network 
p   libusbprog-dev                  - Development files for libusbprog          
p   libusbprog0                     - Library for programming the USBprog hardwa
```Well Im not sure how to proceed.. So any input would be much appreciated!

Regards, cbob

---

### Post by cbob on 2010-05-18
Bump?

---

### Post by Peter09 on 2010-05-18
try
```
sudo xsane
```
in a terminal.
 
Ignore the dire warnings as this is just testing.

---

### Post by cybrsaylr on 2010-05-18
> **Peter09 said:**
> try
```
sudo xsane
```
in a terminal.
 
Ignore the dire warnings as this is just testing.

I am having the same problem.

I put sudo xsane in terminal and still get the same results 
A box pops up saying 
> No devices available

Scanner is a UMAX Astra 1220P, which when I checked is supposed to be Linux  supported.
Scanner runs fine with XP Pro on my dual boot setup on an older PC I have.

---

### Post by cbob on 2010-05-18
> **cybrsaylr said:**
> I am having the same problem.

I put sudo xsane in terminal and still get the same results 
A box pops up saying 


Scanner is a UMAX Astra 1220P, which when I checked is supposed to be Linux  supported.
Scanner runs fine with XP Pro on my dual boot setup on an older PC I have.
Same here, still same problem remains after trying..
```
sudo xsane
```
Regards, cbob

---

