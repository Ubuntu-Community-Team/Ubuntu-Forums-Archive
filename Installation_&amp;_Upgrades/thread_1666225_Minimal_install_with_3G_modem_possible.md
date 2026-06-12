---
title: "Minimal install with 3G modem possible?"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by LinUxaliVe on 2011-01-13
Hello.

I recently downloaded the latest minimal Ubuntu ISO from the official download page.

Is it possible to do a minimal install if I do not have Ethernet capable internet?

I use one of those 3G (cellular) USB modems from companies like Verizon. Basically, it's a cell-phone, with the phone component taken out.

I did something similar with Debian recently, but I had to install the kernel along with the 'dpkg' package, to the HDD. From there, I had to reboot into the core system, install the packages like ppp, wvdial, etc, and then continue with a fresh install of the rest of the system.

There doesn't seem to be a way for me to either install the core files to HDD, or install the internet connectivity packages in the live environment for my modem.

---

### Post by ottosykora on 2011-01-13
well this will be complex, since you can install the minimal , but this might not contain the components for the usb connected 3g.
Beside this, all this will be time consuming and depending on your provider also expensive fun.

I could be cheaper in that case to get the full version and install this, if this will operate the 3g out of the box I have also no idea.
I am fighting for moths with one of those 3g modems under ubuntu, not so easy task to make it work. Those gadgets are simply designed for windows and need to be fed with some files for each provider separate, so unless you have all infos and firmware files for that, don't know, but this might be an adventure.

---

### Post by LinUxaliVe on 2011-01-13
Well, I have done this with a couple other distros.

Debian involved installing the core files only, ie - kernel, libraries, disk modules, etc.. That then let me install the packages I needed, but only after I rebooted into the system.

Another one would be Arch Linux. Since the package manager was available from the live install disc, I temporarily installed the needed packages to the live RAM, and installed the system straight from the net.

As far as I can tell the minimal Ubuntu disc doesn't let me install a core system first, and the disc's live environment doesn't contain a package manager+installer like 'dpkg'.

The basic packages that I need across Linuxes would be something like 'ppp(d)', 'wvdial', 'usb serial something', 'usb-modeswitch', and their dependencies.

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
*deleted duplicate post

---

### Post by LinUxaliVe on 2011-01-14
After digging around for a bit, I found out that the minimal install disc includes an app name 'udpkg' (dpkg renamed?). I did this for a i386 arch PC, so I can't say what you'd need on a 64bit.

I downloaded these packages to a USB drive from the Ubuntu site [HERE](http://packages.ubuntu.com/maverick/):

-- For dial-out
ppp
libc6
libpam0g
libpcap0
libuniconf4.6
wvdial
libwvstreams4.6-base
libwvstreams4.6-extra
libstdc++6
libgcc1
libssl
-- For USB dongles recognized as a cd-rom drive
usb-modeswitch
usb-modeswitch-data
libusb

I then booted the PC with the minimal live disc.

I chose the advanced CLI installer option.

I pressed CTL+ALT+F2 to move to the second virtual terminal, and hit enter.

I typed in 'mkdir /mnt/sdc1', without quotes.

I typed in 'nano /etc/fstab', without quotes, and added this line at the bottom, and exited after saving.
```
/dev/sdc1   /mnt/sdc1   vfat   defaults   0   0
```
I typed 'mount /dev/sdc1 && cd /mnt/sdc1'.

I typed in 'udpkg -i *.deb' to install all of the downloaded packages.

The results?

Well... after running 'wvdialconf', the modem wasn't recognized as either 'ttyACM0', 'ttyUSB0', or as anything else.

So, I went and checked an important module with the 'modprobe' command.
```
modprobe usbserial
```
This was the output.
```
FATAL: Module usbserial not found
```
That's it, end of story. Apparently, the live disc's busybox environment of the minimal install doesn't load the 'usbserial' module.

I guess it isn't currently possible to achieve the OT.

Peace.

---

