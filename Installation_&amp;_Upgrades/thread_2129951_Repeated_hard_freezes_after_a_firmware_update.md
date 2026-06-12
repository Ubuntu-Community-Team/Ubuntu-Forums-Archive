---
title: "Repeated hard freezes after a firmware update"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by Morande80 on 2013-03-27
Hello!

I'm new to the forum; for the past few months, I've been using a hand-me-down Toshiba Satellite laptop from roughly 2006 with Ubuntu 10.04 installed on it. After spending all of last night trying to get a wireless USB adapter working, I finally managed to get it working today after finding the following thread: [http://ubuntuforums.org/showthread.php?t=1667140](http://ubuntuforums.org/showthread.php?t=1667140)

I was apparently missing firmware and upon installation of it, my wireless USB adapter started working like a charm. However, since that update, my computer experiences hard freezes after being online (on either Firefox or Google Chrome) for approximately 45 minutes after starting up the computer. The mouse does not move; the keyboard does not work; the screen just goes to black as if it were about to load a DOS prompt and the mouse stays on the screen, but again, it won't move at all and so I just hold down the power button to switch it off.

I Googled old threads in cursory fashion but didn't seem to find anything that related to my problem; after spending ten hours yesterday trying to find a solution to the WiFi adapter problem that turned out to be head-smackingly simple, I really don't want to be up half the night figuring it out, so I thought I'd go ahead and ask. I just hope that it's not an issue that my computer could be too old to handle.

---

### Post by Morande80 on 2013-03-27
Okay, it crashed three times in a row, the first two times after trying to pull up Google, the third time when I tried to go straight to Facebook after pulling up Firefox. That's not good. When it did, it just went to that black DOS prompt screen and the cursor turned into a pointing hand and froze.

---

### Post by Morande80 on 2013-03-27
And now it just freezes arbitrarily. I was in the middle of another thread in this forum, and when I started moving the mouse it froze as usual. I thought it might have been the Nvidia driver since I read a lot of complaints about how it freezes up Ubuntu, but I do not have one installed.

---

### Post by Morande80 on 2013-04-01
Bump. I still can't access the Internet without it crashing.

---

### Post by ahallubuntu on 2013-04-01
~

---

### Post by Morande80 on 2013-04-01
Good to know. I hope to install 12.04 if I can get this smoothed out!

[TABLE="width: 500"]
[TR]
[TD]*-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 01
       serial: 00:11:f5:7b:93:3f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.0.17 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:c0200000-c020ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:24:3a:23
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:18 ioport:a000(size=256) memory:c0211000-c02110ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:0d:81:a2:91:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.3 multicast=yes wireless=802.11b/g/n  li
[/TD]
[/TR]
[/TABLE]

---

