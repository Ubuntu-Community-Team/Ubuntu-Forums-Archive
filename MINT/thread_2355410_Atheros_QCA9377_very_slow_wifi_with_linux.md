---
title: "Atheros QCA9377: very slow wifi with linux"
date: 2017-03-12
forum: MINT
---

### Post by bak&#305;r on 2017-03-12
In front of me sits an Acer Aspire E15 laptop with an Atheros  wireless interface. The connection is very smooth using the Win10, but  on the dual booted Linux Mint 18.1 or Ubuntu 16.04, the bandwidth fluctuates between a  few kbps and a few Mbps wildly. The overall performance is very low, as  even Google homepage takes about half a minute to load.


  I would appreciate if somebody could guide me how to approach this. I  kept reading many similar issues reported by Ubuntu 12-16 users,  but their solutions did not work as the drivers that they are referring  to do not exist at all or I already have those modules as part of my newer kernel.


    Here is what I have:

  ```
lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:01:00.1
       logical name: enp1s0f1
       version: 12
       serial: 54:ab:3a:d4:a9:58
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:233 ioport:4000(size=256) memory:d3504000-d3504fff memory:d3500000-d3503fff
  *-network
       description: Wireless interface
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 31
       serial: 58:00:e3:74:8b:ab
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-53-generic firmware=WLAN.TF.1.0-00267-1 ip=10.0.0.57 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:242 memory:d3000000-d31fffff

```  

I notice some firmware errors "ath10k_pci ... : Direct firmware load for ath10k/cal-pci failed with error -2." I also found copious reports of this in dmesg:
 ```
[175.512592] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!

```

Thank you very much

---

### Post by jeremy31 on 2017-03-12
I think this can be fixed by disabling power management to some extent
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Reboot, if problems persist, see the wireless script link in my signature and post your results

---

### Post by bak&#305;r on 2017-03-12
Thank you for your reply, but I regret to tell you that the requested output is here: [http://pastebin.com/fmtvj6Ci](http://pastebin.com/fmtvj6Ci). Power management trick did not work.

---

### Post by jeremy31 on 2017-03-12
Can you change the settings on the current access point so that it is on channel 9 and set the encryption to WPA2 only.  When the script was run it was on channel 11 with 6 other access point using mixed mode encryption involving TKIP

You may want to post script results from Ubuntu as some changes may be needed there

---

### Post by bak&#305;r on 2017-03-12
Hi, I unfortunately am not the one who controls the modem. It is owned by the company and I do not have access to the interface of the device. However, with the current settings of the modem, I can reach about 25Mbps bandwith with the dual-booted Win10.

I have tried so many things, and one of them was to try installing Ubuntu rather than Mint, but upon observing that it did not help, I erased Ubuntu and re-installed Mint.

---

### Post by bak&#305;r on 2017-03-12
By the way, some other symptoms, in case they help:

The wireless keyboard switch (Fn+F3) is dysfunctional.
Upload is significantly slower than download (10 kbps vs. 1Mbps).
And the overall performance of the network fluctuates wildly, download speed transiently reaching 15Mbps.

---

### Post by jeremy31 on 2017-03-12
*Thread moved to **MINT**.*

You could speak with the IT contact of the company as TKIP isn't very secure and there aren't many devices left that can't use WPA2 CCMP(AES) encryption

The wireless keyboard switch should toggle soft block results in ```
rfkill list all
```

It might be something enabled in the 4.8 kernel that you can install with the Mint Update Manager by clicking View/Linux Kernels.  With Mint I would also do ```
sudo apt-get install linux-firmware
```
So that the latest version is installed as Mint by default will not update the package with the Update Manager

---

### Post by bak&#305;r on 2017-03-12
No, it did not cause a flip. Both before and after, it says: "soft blocked: no, hard blocked: no".

I had already tried that, while searching the forums. It says that linux-firmware is already the newest version (1.157.8). Right now it has kernel 4.4, I had also tried switching to 4.8, but then it freezes during startup for which I could not find a solution.

---

### Post by jeremy31 on 2017-03-12
You might want to try WICD instead of network manager, praseodym posted this a few months ago
```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
systemctl disable NetworkManager.service
sudo killall wpa_supplicant
sudo service wicd restart
```

Reboot and see if WICD helps at all, if not make Network Manager work again ```
systemctl enable NetworkManager.service
``` ```
sudo apt-get remove wicd
```

Some instructions for using WICD say to uninstall Network Manager but that ends badly for Linux Mint users as it will remove your DE and all you have after a reboot is terminal, the systemctl command fixes that issue

---

### Post by bak&#305;r on 2017-03-12
Thanks a lot for this, it (or accumulation of all the small changes since this morning) seems to have solved the problem. Now download is 10Mbps, and upload is 11Mbps. There probably is still some room to go, but I am satisfied with what I have, as I do not do large data FTP.

---

### Post by bak&#305;r on 2017-03-13
Unfortunately, after a day with good performance, I am all of a sudden back to where I started: dial-up speed wifi. And repeating the above sequel does not help, I also tried purging wicd beforehand. Any ideas?

---

