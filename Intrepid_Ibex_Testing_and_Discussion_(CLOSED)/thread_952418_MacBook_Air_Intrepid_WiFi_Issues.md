---
title: "MacBook Air Intrepid WiFi Issues"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mikeyur on 2008-10-19
//Note, I am totally new to linux// 

So I've been tinkering for the last few hours trying to get WiFi to work on my MacBook Air (1.6/80gb) running the latest Intrepid release.

Many people are saying the wl drivers work, but I just can't seem to get anything working. I've gone to System > Administration > Hardware Drivers and it just hangs at 0% doing nothing (I am guessing it needs an internet connection, which I don't have).

I have followed the MacBook Air Intrepid guide and added the 2 lines of code req'd to the rc.local file, still no luck.

```
rmmod ssb
modprobe wl
```

The device isn't showing up at all so I have no idea where to go from here. Any help would be appreciated.

Thanks
-Mike

---

### Post by kosumi68 on 2008-10-19
Hello mikeyur,

just to make sure: did you reboot the machine after adding the lines to /etc/rc.local?

---

### Post by mikeyur on 2008-10-19
Yep, multiple times. Being the noob that I am, I also tried it before and after the 'exit 0' line that's in there.

---

### Post by kosumi68 on 2008-10-19
What is the output of
```

lsmod | grep ssb
lsmod | grep wl
modprobe -l wl

```

---

### Post by mikeyur on 2008-10-19
looks like

```
/lib/modules/2.6.27-4-generic/volatile/wl.ko
```

---

### Post by kosumi68 on 2008-10-19
> **mikeyur said:**
> looks like

```
/lib/modules/2.6.27-4-generic/volatile/wl.ko
```

Oh. That is an "old" kernel, i.e, surpassed during the beta releases. Also the wl driver is so new it only works well with the very latest stuff. Sounds like all you need to do is update your distribution, and it should work. Hopefully you have an ethernet cable...

---

### Post by mikeyur on 2008-10-19
looks like I'll be going out to buy the MacBook air Ethernet adapter tomorrow. Thanks for your help!

---

### Post by kosumi68 on 2008-10-19
Although the older releases did have problems, thinking back I get the feeling the wl driver did work around 2.6.27-4... Since your output indicated absence of both the ssb and wl driver, what do you get from these commands:
```

sudo modprobe wl
dmesg | tail -25

```

---

### Post by mikeyur on 2008-10-19
sudo modprobe wl

FATAL: Error inserting wl (/lib/modules/2.6.27-4-generic/volatile/wl.ko): Invalid module format

FATAL: Error running install command for wl

I'll give you the other output in a bit. I'm currently writing this out by hand on my iPhone (can't find thumbdrive and no wifi)

---

### Post by mikeyur on 2008-10-19
Ok, found my other thumb drive. Here's what it spit out:

```
michael@-----:~$ sudo modprobe wl
FATAL: Error inserting wl (/lib/modules/2.6.27-4-generic/volatile/wl.ko): Invalid module format
FATAL: Error running install command for wl

michael@-----:~$ dmesg | tail -25
[   35.037320] input: Mouseemu virtual keyboard as /class/input/input11
[   35.104380] input: Mouseemu virtual mouse as /class/input/input12
[   37.141982] Bluetooth: L2CAP ver 2.11
[   37.141999] Bluetooth: L2CAP socket layer initialized
[   37.210369] Bluetooth: RFCOMM socket layer initialized
[   37.210746] Bluetooth: RFCOMM TTY layer initialized
[   37.210759] Bluetooth: RFCOMM ver 1.10
[   37.271401] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   37.271417] Bluetooth: BNEP filters: protocol multicast
[   37.366235] Bridge firewalling registered
[   37.368697] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   41.536685] [drm] Initialized drm 1.1.0 20060810
[   41.542413] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   41.542428] pci 0000:00:02.0: setting latency timer to 64
[   41.544096] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   52.732822] NET: Registered protocol family 10
[   52.737061] lo: Disabled Privacy Extensions
[  124.204370] CPU0 attaching NULL sched-domain.
[  124.204389] CPU1 attaching NULL sched-domain.
[  124.204568] CPU0 attaching sched-domain:
[  124.204574]  domain 0: span 0-1 level MC
[  124.204581]   groups: 0 1
[  124.204597] CPU1 attaching sched-domain:
[  124.204602]  domain 0: span 0-1 level MC
[  124.204607]   groups: 1 0
```

---

### Post by mikeyur on 2008-10-20
Quick bump. Wondering if anyone else is experiencing this problem/found a fix?

---

### Post by kosumi68 on 2008-10-20
Sounds like upgrading is a good idea, then :-)

On a side note: the mouseemu package is likely to bring you problems, and is not needed on this machine. Suggesting removal.

---

### Post by mikeyur on 2008-10-20
Is there any way I could just download the latest beta (with latest kernel, etc) without upgrading over the internet?

I didn't have time to pickup the ethernet adapter today, and would rather save $30 because I'm just going to use it once. I have a bunch of blank cds and time so I don't mind re-burning the latest iso and re-installing (I hadn't done anything to the OS yet), just not sure if the releases on the main 8.10 release page are the freshest possible.

---

### Post by aethralis on 2008-10-20
The daily builds are located here:
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by mikeyur on 2008-10-20
Thanks. I just finished installing the latest daily and my wifi works perfectly now.

---

