---
title: "things i did to get ubuntu on a HP Probook 4330s"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by trikke on 2012-11-29
Here is a collection of things i did on my hp ProBook 4330s to get things working properly. Hopefully u can use the same fixes on the other ProBooks aswel.


- Go to [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) [http://www.ralinktech.com/en/04_support/license.php?sn=5019](http://www.ralinktech.com/en/04_support/license.php?sn=5019) and download the RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592) drivers.

Extract the package and cd to the directory.

U need to make a slight modification to the configuration for the driver:

vim os/linux/config.mk

And set:

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Manager
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

By default they are both set to ‘n’. Save and close the file.

From the top level directory, compile and install the driver:

sudo su
make && make install


- After compilation, and while still root, modprobe the driver:

modprobe rt3562sta


You should get no output signalling success.

- Now an important step. We need to blacklist a conflicting driver that will be loaded preferentially for this network card.

sudo vim /etc/modprobe.d/blacklist.conf

enter the following line at the bottom of the file:

blacklist rt2800pci

Save and close. ( :wq! )

- reboot


- Now wireless was working but with alot of messages in my dmesg so i had to deactivate logging.

sudo iwpriv ra0 set Debug=0

still i was getting error messages in my log file about evbug
so if u get them to, go back to the blacklist.conf and add this line at the bottom.

blacklist evbug


hope this helped :)

---

