---
title: "Wlan0 wireless is renamed to Wlan3"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by aixroot on 2010-05-12
FIRST POST

Dear all,

I have a -very snazzy- Samsung N510 with Ubuntu 10.04.

I had the Wireless working. After an recent update the wireless icon was gone.

I cannot tell if the wireless hardware has a driver.
1: which command will show me the associated driver?

I got a Rtl8192se driver. That has a Wlan0up script with it.
I dmesged the Wlan0. That told me that the Wlan0 was renamed to Wlan3 by UDEV.
2 How do I get the wireless to work again?
3 Can I rename the wireless Wlan3 to Wlan0? I -in my innocence- expect the wireless Realtek to work again.
If so, which wlan3 do I rename where?

---

### Post by aixroot on 2010-05-12
ferdinand@ferdinand-netbook:/etc/udev/rules.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan3     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

@@@@@@@@@@@@@@@
ferdinand@ferdinand-netbook:~/rtl8192se_linux_2.6.0015.0127.2010$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan3
       version: 01
       serial: b4:82:fe:8a:6a:65
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:5000(size=256) memory:c2000000-c2003fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 13
       serial: 00:24:54:60:fb:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.8 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:c2100000-c2103fff ioport:6000(size=256)

---

### Post by yota on 2010-05-12
launch this command:

```

sudo gedit /etc/udev/rules.d/70-persistent-net.rules

```

it will open a text editor on the /etc/udev/rules.d/70-persistent-net.rules, asking your password since is a system configuration file.

The "NAME" tag is what you are searching, mine is like this:
```

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:90:2c:9c:a5", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

change it as you please (but double check to avoid conflicts between multiple interfaces with the same name!), and save once you are done.
To apply changes you have to reboot, plese note that then you'll have to configure network from scratch.

---

### Post by aixroot on 2010-05-13
Thanks Yota,

But alas no relief. 

iwconfig now shows wlan0.

I reinstalled the driver (make, make install) 
but now after that this fault code is returned by the terminal
insmod: error inserting 'r8192se_pci.ko': -1 Operation not permitted

---

### Post by aixroot on 2010-05-13
Still no luck, I think it must be something simple.


SIOCSIFFLAGS: Permission denied
ferdinand@ferdinand-netbook:~$ sudo ifconfig wlan up
[sudo] password for ferdinand: 
wlan: ERROR while getting interface flags: No such device
ferdinand@ferdinand-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ferdinand@ferdinand-netbook:~$

---

### Post by yota on 2010-05-14
> **aixroot said:**
> Still no luck, I think it must be something simple.

ferdinand@ferdinand-netbook:~$ sudo ifconfig wlan up
[sudo] password for ferdinand: 
wlan: ERROR while getting interface flags: No such device


The interface name is "wlan0" and not "wlan", but why are trying to configure it under command line instead of using networkmanager (or the gui tool of your choice)?

Also AFAIK the card should be supported by 10.04 and the presence of wlan0 when you launch iwconfig seems to indicate that it's already working (but I can't tell for sure... il largely depends on the specific model/revision).
Anyway are you sure that you need to compile a driver to make it work?

Hope this helps!

---

### Post by aixroot on 2010-05-14
Hi Yota,

I don't know whick gui program lets me talk to my wireless. If I reboot without my lan cable. I have no internet connection.


02:00.0 VGA compatible controller: nVidia Corporation C79 [Quadro FX 470M] (rev b1)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
ferdinand@ferdinand-netbook:~/rtl8192se_linux_2.6.0015.0127.2010$ ./wlan0upcp: cannot create regular file `/etc/acpi/events/RadioPower.sh': Permission denied
insmod: error inserting 'r8192se_pci.ko': -1 Operation not permitted

---

### Post by yota on 2010-05-14
Which version of ubuntu are you using? (stock ubuntu, kubuntu, xubuntu...)

If you are using the standard gnome-based one NetworkManager ([http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)) should be sitting in the tray near the clock.

If you do search on google there are many howtos, but the tool is pretty self explanatory.

Hope this helps!

p.s. you still have not told me why you are trying to install a driver. Please note that I'm not saying that it's surely wrong... I'm asking if you are **sure** that it's absolutely needed!

---

### Post by 09sparky on 2010-08-03
If you are unable to connect, you may be missing " linux-backports-modules-wireless-".  Make sure you select the correct one for your kernel (uname -r).  I run into the problem of loosing my wireless connection each time I do a kernel upgrade.

---

