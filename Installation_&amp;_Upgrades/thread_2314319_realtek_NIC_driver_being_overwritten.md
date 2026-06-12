---
title: "realtek NIC driver being overwritten?"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by wbloos on 2016-02-20
Hi,

I bought my father a toshiba Satellite c55d-c-169 and installed ubuntu 14.04 on it.
He had problems with the network, so found out what NIC it has (RTL8101/2/6E), downloaded the driver from realtek and installed it.
He also had problems with random crashes under the fglrx drivers, and with the help of [this]("http://ubuntuforums.org/showthread.php?t=2276537") post i managed to revert to the nouveau drivers, though it was a bit cumbersome to get the realtek drivers working in combination with nouveau and i'm not quite sure why it worked in the end.

Now, 2 weeks later, there have been some ubuntu updates and:
[LIST]
[*]the wifi is unstable
[*]there have been no more random crashes
[*]the additional drivers dialog says that we've installed drivers manually (but it seems to refer to the GPU drivers)
[*]
[/LIST]

Now, i can (try to) revert to nouveau agin and reinstall the Realtek drivers, but something seems to be interfering.
I've thought about chaning the name of the new r8101 driver and blacklisting the old one, but that would be guesswork really, so i figured that i need some help.

I've checked the drivers in use for the NIC, and i get different answers:
lspci says that the  RTL8101 driver that i installed is being used:
```
root@me:~/manual_installs/r8101-1.028.00# lspci | awk '/net/ {print $1}' | xargs -i% lspci -ks%
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
    Subsystem: Toshiba America Info Systems Device f840
    Kernel driver in use: r8101

```

But the /sys files tell me that another driver is in use:
```
ls /sys/class/net/wlan0/device/driver/module/drivers
pci: rtl8821ae

```


What can i do to get this laptop running well?

Thanks for any help.

---

### Post by wbloos on 2016-02-21
OK, so i found out that the r8101 is the Ethernet controller, so for the wired internet
And the wireless controller is the other one: rtl8821ae. That one seems to have a lot of problems, i'm now following [this thread]("http://ubuntuforums.org/showthread.php?t=2258969").

---

