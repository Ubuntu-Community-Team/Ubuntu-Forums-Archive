---
title: "Help with installing ndiswrapper and WUSB54GC onto Ubuntu"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by Breakthrough on 2008-01-27
Okay, so I am literally brand new to this and was hoping that someone could help me install either of these with howto's.  I've searched around for the pat 2 hour and literally can't even get ndiswrapper working. =/.  Btw this isn't on that computr, this is another computer running Windows XP <.<

---

### Post by Mikecore on 2008-01-27
I will assume your using Gusty and if you are here is the official guide for using windows drivers.

```

https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html

```

here is another guide if that not what you need.

```

https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29

```

either should work.

please use the community or official documentations when you have issues.


here is a link
```

https://help.ubuntu.com/community/TitleIndex

```

---

### Post by Breakthrough on 2008-02-12
Disregard what I asked earlier.
Okay so I finished one of the tutorials, and tried to plug in my thing after ```
ndiswrapper -l
``` said it was installed.  Still no internet :(.  Help?

---

### Post by wwwgong on 2008-02-17
I have 
[LIST]
[*]Desktop: Ubuntu 7.10 - i386 version
[*]Linux kernel: 2.6.22-14-generic
[*]Wireless USB Adapter: Linksys WUSB54GC
[/LIST]

and install WUSB54GC today (2008-02-17)
The following are my steps to success.
Hope it helps!
=======================================================================================

# get linux driver for WUSB54GC adapter from RaLink web site

wget [http://www.ralinktech.com.tw/data/drivers/2008_0117_RT73_Linux_STA_Drv1.1.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0117_RT73_Linux_STA_Drv1.1.0.0.tar.bz2)

# compile driver

su - root
tar -xvjf 2008_0117_RT73_Linux_STA_Drv1.1.0.0.tar.bz2 
mv 2008_0117_RT73_Linux_STA_Drv1.1.0.0 /usr/src
cd /usr/src
cd 2008_0117_RT73_Linux_STA_Drv1.1.0.0/Module/
cp Makefile Makefile.orig
cp Makefile.6 Makefile
vi rtmp_def.h
# verified that already defined as
{USB_DEVICE(0x13b1,0x0020)}, /* Linksys WUS54GC */ \

# if missing, enter one entry as above

!q

make

# load driver

cp rt73.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless
insmod /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/rt73.ko
depmod -a
modprobe rt73

#check driver is loaded

root@albert:/etc/network# lsmod | grep rt73
rt73                  239744  0 
usbcore               138632  6 rt73,usb_storage,libusual,ehci_hcd,ohci_hcd

# restart the machine

# set wireless network name and encryption key

goto System > Administration > Network
enter root password

# make sure that Wireless connection device is present

press "Properties" button, 
set rausb0 Properties as follows:
uncheck "Enable roaming mode"
Under "Wireless Settings"
select "Network name (ESSID)" (my ESSID=wong)
select "Password type" to be "WEP key (hexadecimal)" (choose the one appropriate for you)
enter "Network password" (or WEP key in hex, e.g. my key is f5375fbdd4)

Under Connection Settings"
select "Configuration" to be "Automatic configuration (DHCP)" (since I have a wireless router)
press OK button

# verify network settings

less /etc/network/interfaces
auto lo
iface lo inet loopback

iface rausb0 inet dhcp
wireless-key f5375fbdd4
wireless-essid wong
auto rausb0

# make sure that above file has settings consistent with settings entered 
thru System > Administration > Network GUI

# test connection
After that, I test network connection either by pinging [www.ubuntu.com](www.ubuntu.com)
or opening your browser to "http://www.ubuntu.com"

---

### Post by branque on 2008-03-22
Thanks wwwgong for the tutorial,

I am using Ubuntu 7.10 desktop with kernel 2.6.22-14-generic and Linksys  WUSB54GC adapter, followed your tutorial and compiled the new drivers and it seems to be working fine, no more lost connection or strange behavior. Have just used it for few hours, maybe to earlies to say anything, but it looks promising.

Did a check with dmesg and got this message...

[   78.684000] usbcore: registered new interface driver rt73usb
[   78.764000] rt73: module license 'unspecified' taints kernel.
[   78.764000] Symbol usb_register_driver is being used by a non-GPL module, which will not be allowed in the future
[   78.764000] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
[   78.768000] Symbol usb_deregister is being used by a non-GPL module, which will not be allowed in the future
[   78.768000] Please see the file Documentation/feature-removal-schedule.txt in the kernel source tree for more details.
[   78.772000] usbcore: registered new interface driver rt73

'lsmod | grep rt73' gives me...

rt73                      239744  0 
rt73usb                25344  0 
rt2x00usb            12032  1 rt73usb
rt2x00lib              19584  2 rt73usb,rt2x00usb
usbcore               138632  7 rt73,rt73usb,rt2x00usb,usbhid,ehci_hcd,ohci_hcd

Regards, Branque.

---

