---
title: "Fail 12.04 install, no network found, but ethernet is connected"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by verwirrt on 2013-08-28
I am trying to install kubuntu 12.04 on a new quadcore, 4th generation Intel desktop with an ethernet internet connection.

I created a bootable USB flash drive from the kubuntu-12.04.3-desktop-amd64.iso file.

I can now boot into kubuntu from the flash drive, but I cannot install kubuntu on the machine, because the ethernet wire network connection is not found.  The network connection works fine in the already installed Windows 7 Pro operating system.

Does anyone know how I can cause the connection to be found by the kubuntu installer?

---

### Post by Feathers McGraw on 2013-08-28
Hi,

That's strange, I don't think problems with ethernet are very common on *buntu.

Couple of approaches here:

1) If you also have a wireless card in the machine (or a USB WiFi card that you can plug in) you can click "Try Kubuntu" and then put in your wireless info by clicking the WiFi symbol in the bottom right of the desktop. If that gets you online, you should be able to install properly by clicking the "install Kubuntu" shortcut in the desktop folder widget (you'll know what I mean when you see it).

Once you have installed, you have the option to enable additional drivers and get your ethernet working.

2) It is possible that your particular ethernet controller has a dodgy driver. "Try Kubuntu", and then click the Kickoff icon (like the start button on Windows), search for "konsole", open konsole, and type:

```
sudo lshw -c network
```

This will give us some information on your ethernet controller, so we can see if other people have had the same problem.

Feathers

---

### Post by verwirrt on 2013-08-28
I get the following:

sudo lshw -c network
  *-network UNCLAIMED
         description:  Ethernet controller
         product:  Intel Corporation
         vendor:  Intel Corporation
        physical id:  19
         bus info:  pci@0000:00:19.0
         version:  04
         width:  32 bits
         clock:  33 MHz
         capabilities:  pm  msi  bus_master cap_list
        configuration:  latency=0
        resources:  memory:  f7c00000-f7c1ffff    memory: f7c3d000-f7c3dfff   ioport:  f080(size=32)

---

### Post by verwirrt on 2013-08-28
Forgot to mention,  this is a desktop machine without WIFI, so I can't try your first option unless I get a USB WIFI card.

---

### Post by mastablasta on 2013-08-29
intel? intel should work they have mostly opensource drivers. though sometimes intel chips need firmware, but i though that one is inlcuded in the image.

by the way you can install without internet connection. as long as you don't mark to download anything additionally.

---

### Post by Feathers McGraw on 2013-08-30
Hmm..

That wasn't quite what I was expecting - usually you get more detail on the exact model of card - for example:

```

feathers-mcgraw@62-West-Wallaby-Street:~$ sudo lshw -class network
  *-network               
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f0100000-f0103fff
**  *-network**
**       description: Ethernet interface**
**       product: RTL8111/8168 PCI Express Gigabit Ethernet controller**
**       vendor: Realtek Semiconductor Co., Ltd.**
**       physical id: 0**
**       bus info: pci@0000:04:00.0**
**       logical name: eth0**
**       version: 03**
**       serial: 64:31:50:64:99:3b**
**       size: 10Mbit/s**
**       capacity: 1Gbit/s**
**       width: 64 bits**
**       clock: 33MHz**
**       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation**
**       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s**
**       resources: irq:43 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0010000-f001ffff**
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: cc:52:af:93:cb:4a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.0-19-generic firmware=N/A ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11bgn

```

Try ```
sudo lspci | egrep -i --color 'network|ethernet'
``` instead. For me, the output is:

```
feathers-mcgraw@62-West-Wallaby-Street:~$ sudo lspci | egrep -i --color
'network|ethernet'03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 03)
```

Feathers

---

### Post by grahammechanical on 2013-08-31
You have Kubuntu 12.04.3 which is the recently released .3 upgrade to 12.04 LTS. It should contain the latest Linux firmware for new hardware. So, why the problem? Could it be such a simple reason of not having Networking enabled? In the live session click on the Network icon. Without any connections it will look like an upside down cone. See if Enable Networking is ticked. If it is not ticked then  ethernet is switched off in the OS.

You can also open a terminal and run
```
nm-tool
```

this is what I see on my machine

> State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            skge
  State:             unavailable
  Default:           no
  HW Address:        00:1A:92:82:D4:32

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:1A:92:82:DB:59

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

I have two ethernet ports but I am only connected to one of them - eth0 (wired connection 1) and that is because it is the fastest of the two. You could also try
```
ifup eth0
```

I have never run that from a Live session. So, I do not know if it will need sudo in front. But in an existing hard disk install of Ubuntu that command will switch on an ethernet adapter. Sometimes switching the adpter off before switching it on works better.
```
ifdown eth0
```

It should be possible to do all of this on a live session.

Regards.

---

### Post by varunendra on 2013-08-31
Since you have posted in "Installation & Upgrades" section, I assume your prime target is to install Kubuntu.

Like mastablasta already said, network connection is absolutely not needed to install Ubuntu (or Kubuntu). Since you are able to boot with the Live USB, I don't see a reason why you can't install in on the machine from the same USB.

If I'm misunderstanding something, please elaborate your problem.

For the ethernet issue, I'd suggest to start a new thread in [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") section, since mixing different issues in the same thread is not a good idea. Feel free to post here a link to that thread though, so we all can follow.

By the way, the command to determine exact chip-id of your card is -
```
lspci -nn | grep 0200
```

---

### Post by verwirrt on 2013-09-08
Thanks for all your responses.  You are of course correct that one can install without a network connection, which I later did.  But, although I enabled networking after booting into Ubuntu, I still couldn't establish an ethernet connection.  So, since I have new hardware, I thought perhaps it might work with a more recent Ubuntu release.  When I tried 13.04, it "found" the ethernet connection and installed.  Now, however, I have a problem booting up into the installed Linux.  I'll post later about that in another forum.

---

