---
title: "Upgrading the hardy kernel to the intrepid kernel"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by comandrei on 2008-08-31
My wireless is pretty bad with the Hardy kernel (i'm using a rt73usb driver) and I tried out the Intrepid kernel. I now get full speed and the device is finally working properly. I posted a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/262743") report, asking the guys to backport the driver to the Hardy Kernel, but in the meantime (is this ever gets fixed) is there a way that i could use the Intrepid kernel in Hardy?
I manually installed the latest intrepid kernel, but i'm having problems with the brightness of my laptop display. I think the kernel is missing some modules ( i saw that acpi was compiled in a separat package ([http://packages.ubuntu.com/intrepid/main/acpi-modules-2.6.27-2-generic-di](http://packages.ubuntu.com/intrepid/main/acpi-modules-2.6.27-2-generic-di)) and I have no idea how to install this package.

---

### Post by chronographer on 2008-08-31
you can install serial monkeys rt73 driver in hardy... instructions are attached (i used to follow these every time, this will save you from installing intrepid) But I would also like to install intrepid, for the hdd controller support for my new motherboard.

If anyone knows if it is possible to boot up hardy live cd with an intrepid kernel, and then install hardy (and the intrepid kernel) I would love to know! Otherwise, I am using intrepid now, and many applications are buggy, luckily I can send those automatic bug reports off and feel like I'm helping!

```
1.  (remove old drivers)
2. sudo gedit /etc/modprobe.d/blacklist (add the following lines at the end of the file):
blacklist rt73usb
blacklist rt2570
blacklist rt2x00lib
3.sudo apt-get install build-essential
4.sudo apt-get install linux-headers-`uname –r`
5.get the latest version of the driver source from the serialmonkey site. The name is rt73-cvs-daily.tar.gz. I saved it in /usr/src.
6.sudo wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz -O /usr/src/rt73-cvs-daily.tar.gz
7.sudo tar -zxvf rt73-cvs-daily.tar.gz
8.cd /usr/src/rt73*/Module
9.sudo make
10.sudo strip -S rt73.ko (if it’s 2Mb instead of 250Kb ish)
11.sudo make install
12.sudo modprobe rt73
13.sudo gedit /etc/modules – add the text rt73 at the end
14.create text file called rt73 in /etc/modprobe.d  sudo gedit /etc/modprobe.d/rt73
15.put the text “alias wlan0 rt73” in this file
16.rm /etc/modprobe.conf as it’s no longer needed
17.add the following to /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "yourESSID"
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set Channel=11
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="your key"
18.reboot/restart network

(note.. I use different /etc/network/interfaces config...)
Hope this helps you get the old wireless up and running
Oh another thing: if you want a link monitor I rate rutilt - it works a treat with ralink stuff and you can set it to run minimized at startup which gives you a nice little transmitter logo next to the clock
```

---

### Post by comandrei on 2008-08-31
I just want to use Intrepid kernel over Hardy... 
I tried the serial monkey drivers, but i don't think they are API compatible with hardy kernel.
LE: I tried the method above and It didn't work + I want roaming mode, just like the native driver in the hardy kernel.

---

### Post by chronographer on 2008-09-23
use the above method + wicd to configure the connection and you are all go! It is a nice little application. An issue with rt73 is that the network manager doesn't work properly with the drivers, so using wicd as an alternative ( and removing network-manager ) does the trick. I am having some issues wit the inttepid kernel (2.6.27-4) and rt73 so I don't think using it will solve your problems.

---

