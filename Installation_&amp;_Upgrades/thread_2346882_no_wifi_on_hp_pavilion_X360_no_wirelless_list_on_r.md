---
title: "no wifi on hp pavilion X360 no wirelless list on rfkill"
date: 2016-12-19
forum: Installation &amp; Upgrades
---

### Post by rsmpereira89 on 2016-12-19
Hi all 
I installed recently 14.04 on a HP pavilion. I have tried other solutions without success, and I never seen such error in any other forum/post.

The wireless LAN is NOT listed with rfkill 

```

~$ rfkill list all 

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````

 ~$ iwconfig
lo        no wireless extensions.

eno1      no wireless extensions.


``````

~$  ifconfig

eno1      Link encap:Ethernet  HWaddr d0:bf:9c:8f:0a:11  
          inet addr:192.168.1.79  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8ce6:86f3:e835:4013/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:158684814 (158.6 MB)  TX bytes:4662828 (4.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:159936 (159.9 KB)  TX bytes:159936 (159.9 KB)

```
I am 0 at linux, and I would appreciate amy possible help to understand, at least, where is the problem

Thanks

---

### Post by jeremy31 on 2016-12-19
Welcome to the forums
Please post results for ```
lspci -nnk | grep -iA2 net; lsusb
```

But since you appear to be connected via ethernet see the wireless script link in my signature and post results

---

### Post by rsmpereira89 on 2016-12-20
```


01:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    DeviceName: Broadcom Harrier 802.11ac Wi-Fi and Bluetooth Combo Adapter
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:2230]
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:22b3]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 002 Device 004: ID 064e:c342 Suyin Corp. 
Bus 002 Device 003: ID 06cb:014f Synaptics, Inc. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 003: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by rsmpereira89 on 2016-12-20
and for the script
```

-2016-12-20 09:13:23--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.253.112, 192.30.253.113
Connecting to github.com (github.com)|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2016-12-20 09:13:24--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.84.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.84.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16156 (16K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

wireless-info                        100%[===================================================================>]  15,78K  --.-KB/s    in 0,001s  

Last-modified header missing -- time-stamps turned off.
2016-12-20 09:13:24 (17,0 MB/s) - &#8216;wireless-info&#8217; saved [16156/16156]


Results saved in "/home/raquel/wireless-info.txt".


```

After reboot no wifi**,** it is like the machine doesn't even has the hardware

---

### Post by wildmanne39 on 2016-12-20
Hi, you posted the script we need the file > Results saved in "/home/raquel/wireless-info.txt"..

---

### Post by rsmpereira89 on 2016-12-20
> **wildmanne39 said:**
> Hi, you posted the script we need the file .

should I take it out?

---

### Post by wildmanne39 on 2016-12-20
> **rsmpereira89 said:**
> should I take it out?
Sure you can take it out and paste the file in its place.
Thanks

---

### Post by rsmpereira89 on 2016-12-20
Ok, any way 

no wifi wet, does anyone knows if this was also a issue on ubuntu 15, I can simply downgrade my pc

---

### Post by jeremy31 on 2016-12-20
For that chip you need to have Secure Boot disabled in BIOS, then
```
sudo apt-get install bcmwl-kernel-source
```

Reboot

---

### Post by rsmpereira89 on 2016-12-20
> **jeremy31 said:**
> For that chip you need to have Secure Boot disabled in BIOS, then
```
sudo apt-get install bcmwl-kernel-source
```

Reboot

How do I disable it, plus I have done the referent code before

---

### Post by jeremy31 on 2016-12-20
Restart and the manual says to press the ESC and then F10 to get into BIOS, then search through the pages for Secure Boot settings, it may be in security or the boot page.

On my 16.04 computer I was able to enable secure boot with ```
sudo update-secureboot-policy --enable
```
So it may be possible to disable using terminal with ```
sudo update-secureboot-policy --disable
```
But since you have 14.04 it may not be possible

---

### Post by rsmpereira89 on 2016-12-20
Good morning 

Sorry It did not worked

Failed to request new MokSB state

---

### Post by rsmpereira89 on 2017-01-17
Apparently I cannot disable security boot, no matter how many times I say yes. Any ideas?

---

### Post by jeremy31 on 2017-01-18
You might be able to use mokutil to bypass the module verification
[http://askubuntu.com/a/867114/300665](http://askubuntu.com/a/867114/300665)
[http://askubuntu.com/a/762255/300665](http://askubuntu.com/a/762255/300665)

---

