---
title: "no wireless, no fglrx"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by slugicide on 2008-10-18
I'm on a Dell E1505.
If I log into Intrepid with 2.6.27 I get all the desktop effects, but no wireless.  If I log into 2.6.24 I get wireless, but no desktop effect--it says DKMS auto installation fails at startup.

So, should I be asking how to get wireless with 2.6.27 or how to get fglrx with 2.6.24? Thanks.

---

### Post by sach on 2008-10-19
Similar problem with dell 1501 - wireless doesnt work with native drivers and with ndiswrapper I'm struggling to connect to WPA network (it only works once, thereafter I have to delete the wireless properties and retry numerous times)

Desktop effects work but are very slow - they worked perfectly in 7.10

---

### Post by dbeltran on 2008-10-19
Destokp effects not working for me in inspiron 1501 too. However, wireless is working after upgrading the firmware of the broadcom card and changing the properties in network manager. After reboot wireless is working without problems.

Instructions for upgrading can be found in:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Concretely i follow the next instructions:

You are using the b43 driver from linux-2.6.25 or newer

Follow these instructions if you are using the b43 driver from linux-2.6.25 and newer or compat-wireless-2.6, or from any current GIT tree.

Use version 011 of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

Use version 4.150.10.5 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

Before upgrading i've had the next log:

Oct 18 23:01:20 portatil kernel: [   46.559619] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
Oct 18 23:01:20 portatil kernel: [   46.559633] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.

Now i have:

Oct 19 12:50:47 portatil kernel: [   46.538043] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

I hope we will have a new version of the fglrx driver compatible with xorg 7.4 very soon like i have read in another post from a ubuntu developer.

Good Luck,

David

---

### Post by slugicide on 2008-10-22
So, I followed your instructions, but I still don't have wireless on the current kernel.  Any advice?

---

### Post by Teamgeist on 2008-10-22
Is the package ```
linux-firmware
``` installed on your system?
If not, install and reboot.

---

### Post by slugicide on 2008-10-22
It is, indeed on my system.  version 1.1 it says.

---

### Post by slugicide on 2008-10-23
Anyone have any advice?  I followed the instructions [here]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new"). Still no wireless.

---

### Post by outfaller on 2008-10-23
My laptop wireless(bcm4311) has always given me problems with Ubuntu until the release of a new driver: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

It's in Intrepid Ibex, didn't have to install anything additional. Only annoying thing is I have to do this after every boot:

sudo modprobe -r b43
sudo modprobe -r wl
sudo modprobe wl

Try that and disable ndiswrapper if you have it installed.

---

### Post by slugicide on 2008-10-23
When I try and do that I get:
FATAL: Module wl not found

---

### Post by slugicide on 2008-10-24
Bumpiddy.  Anyone got any new ideas for me?

Oh, yeah:
 *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

---

