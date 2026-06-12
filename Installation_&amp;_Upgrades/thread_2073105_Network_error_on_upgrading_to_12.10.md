---
title: "Network error on upgrading to 12.10"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by vaibhav on 2012-10-19
Greetings.. I upgraded to Ubuntu 12.10 yesterday. On reboot, I started facing networking issues on my laptop. Here are the symptoms:
1. On trying to connect to WiFi, it keeps showing the rotating circle (apparently showing that it is trying to connect), but the WiFi connection never establishes.
2. On plugging in Ethernet cable, the LEDs that blink near the socket, don't glow at all.
3. Then I rebooted to older 3.2 kernel. WiFi is connected (thank god, so that I can post this), but Ethernet cable LEDs not blinking issue is still there.
4. Note: the LEDs are blinking when I'm at GRUB. They suddenly stop glowing half way thru the boot process.

Any hints what could be wrong here?
Where do I look to trace the issue?

Thanks.

---

### Post by 2F4U on 2012-10-19
What is your hardware? On my installation WiFi works without any issues.

---

### Post by vaibhav on 2012-10-19
lspci | egrep 'Network|Ethernet'
```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```
Anything else you want to know?

---

### Post by vaibhav on 2012-10-19
Hi,
The error seems to have solved by changing the /etc/network/interfaces file.

Earlier it was:
```
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```

Now it reads:
```
auto lo
iface lo inet loopback
```

It's a puzzle to me, why with the same setting it worked in 12.04. Anyway, good that I've found a solution to make it working!

---

### Post by vaibhav on 2012-10-19
OK, while the wired issue is solved, I still can't seem to get WiFi to connect on the 3.5 kernel. Any help on that will be appreciated.
Thanks.

---

