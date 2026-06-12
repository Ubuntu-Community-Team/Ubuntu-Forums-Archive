---
title: "Networking Disabled After Sleep"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by danben on 2010-03-19
Last night I finally got Lynx 3 running on my Envy, but the victory seems to have been short-lived.  After I confirmed everything was working well, I decided to test the suspend functionality since I had heard of some users having problems with it.  Sleeping went off without a hitch, and the machine was cold in the morning.

Waking up proved more difficult, as I had to do a hard shutdown followed by a reboot to get it to come back on.  Now when I log in, the Network Manager icon is grayed out, and clicking on it gives me a message that says "Networking is disabled".  I tried restarting again, I searched for something useful in preferences, and I unloaded / reloaded the iwlagn module.  Nothing seems to be working.

Has anyone else experienced anything like this?  I found similar bug reports from a long time ago in Hardy, but nothing more recent.

---

### Post by dash86no on 2010-03-19
I have the same problem. I put my laptop into hibernate mode, and when I tried to resume, all that came up was a black screen. After messing around for a while pressing "Alt-crtl f2" and REISUB combos for a few minutes, I finally gave up and did a hard reboot. 

When the laptop came back up, I had "Networking Disabled" coming up when I clicked on the nm-applet. 

I have a realtek wireless, and had manually installed the driver from the realtek website, so I don't know if this has anything to do with things. 

When the problem first happened, I tried looking at the lshw output, and noticed something like "illegal device" or some such thing next to my wireless card. Now after attempting to reinstall the realtek driver and a couple of reboots, the wireless card is no longer even showing up in lshw. 

ifup wlan results in  Ignoring unknown interface wlan0=wlan0.
ifconfig wlan0 results in wlan0: error fetching interface information: Device not found

This seems to have happened since reinstalling the driver. When the problem initially happened, ifup wlan would result in  Ignoring unknown interface wlan0=wlan0 but ifconfig wlan0 would give me regular interface info. 

I can easily bring wired networking online by right clicking on nm-applet and clicking "enable networking" but this does noting for my wireless. 

Oh, also I tried uninstalling and reinstalling nm-applet. 

Thanks,

DA

---

### Post by dash86no on 2010-03-19
Wow, that was scary. I tried using a live CD, (2 in fact, 9.10 64 bit and 10.04 alpha), both of which had showed the wireless card being detected previously, and neither detected my wireless card. 

So with tears in my eyes, I opened up my recently purchased pride and joy, expecting to see the wireless card emitting smoke or something similar. I took the card out of the board, put it back, and when I rebooted into my installed OS, it seems that now my card is actually being detected. 

How weird is this? Does this suggest some kind of firmware error with the card? I mean, since the card was not being detected via the live CDs, this can't be a config issue, right?

lspci output:

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

lshw output:

000(size=16777216)
           *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 10
                serial: 00:0d:f0:7d:06:a4
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=192.168.1.168 latency=0 link=yes multicast=yes wireless=802.11bgn

---

### Post by QwUo173Hy on 2010-03-23
When I put my machine to sleep, I have no wireless networks when I resume. I'm using Intel hardware. I'll keep trying different combinations and see what I come up with.

/cancel that, the last two attempts were fine.

---

### Post by brettnak on 2010-04-17
I am unfortunately experiencing this problem right now.  Has anyone figured it out?  I'm using a completely different network card than the rest of the people in this thread.  Mine is a USB Netgear WN121.

Any help would be appreciated.

---

### Post by brettnak on 2010-04-17
I just figured out the problem.  To anyone else that might have this problem, you need to re-enable networking, for some reason, it gets turned off.  You can do that like so:

```

gksu gedit /var/lib/NetworkManager/NetworkManager.state

```

Find the line that says:

```

NetworkingEnabled=false

```

and, do the obvious, change it to true:

```

NetworkingEnabled=true

```

Then restart network-manager by doing one of the following:

```

sudo restart network-manager

```

-- or --

```

sudo /etc/init.d/network-manager restart

```

---

