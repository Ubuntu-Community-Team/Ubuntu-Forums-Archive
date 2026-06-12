---
title: "Belkin Wireless N Dongle, no networks listed"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by daverab on 2009-08-17
Hey everyone,

I have a F5D8053 v4 usb dongle for wireless n. It worked fine in 9.04, but I just dist-upgraded to karmic.

nm-applet sees it, but it doesn't pick up any networks. Attempting to manually force it to connect ends up with a very long timeout.

The dongle uses the Ralink RT2870 chipset. lsusb lists the device, rfkill confirms it isn't blocked in the new kernel (everything up to date as of 8/17/09), and nm-tool shows that the rt2800usb driver is in use.

Anyone with any info on solutions would be appreciated. I'm going to try wicd soon as a potential solution (since one forum said something to that effect worked for him).

---

### Post by jfernyhough on 2009-08-17
Are there any drivers enabled in Hardware Drivers? Possibly there's an old driver hanging around that needs removing and a new version installing.

---

### Post by daverab on 2009-08-17
I'm not too sure. It was 'baked' into the kernel back with 9.04. I'll dig around in synaptic and see if anything pops up. The driver supplied on the RA site only works up to a kernel two versions prior to karmic.

---

### Post by daverab on 2009-08-18
Well, no such luck. Wicd has the same issue.

---

### Post by jfernyhough on 2009-08-18
Hmm... if the drivers are in the kernel then maybe that is what is at fault. There is 2.6.30-9 in the repo; try that instead of the default 2.6.31-rc6. If it's a kernel issue in 2.6.31 I imagine it will be fixed in the next rc release or two.

---

### Post by daverab on 2009-08-21
Well, looks like it's something with wireless in the kernel. I tried using a different adapter, an old linksys usb g one. It gets to the point of trying to connect to a network and fails. I'm sure once the kernel is finalized it'll be fixed. For now I'm on a wired connection.

---

### Post by bacardiandwatermelon on 2009-08-21
Are you using gnome or kde? Kde have just fixed plasma-widget-network-manager i've been using wicd for the last couple of weeks, works really well.

---

### Post by hexsel on 2009-08-21
I had problems with usb wireless thingie as well.  There's a known bug marked somewhere (I'm subscribed to it, but I don't know how to list my subscriptions, Launchpad is simpler than other bug trackers... A BIT MUCH).

I keep an older .28 kernel from Jaunty to be able to connect.

---

### Post by daverab on 2009-08-22
I'm using Gnome.

---

### Post by taavikko on 2009-08-22
> **hexsel said:**
> There's a known bug marked somewhere (I'm subscribed to it, but I don't know how to list my subscriptions,

Click your name on the top right corner, then select the "bugs" tab in the center.

Or
[https://bugs.edge.launchpad.net/~username](https://bugs.edge.launchpad.net/~username)

---

### Post by nickmcg on 2009-08-29
Jaunty used rt2870sta, karmic uses rt2800usb which doesn't work on my system

Nick

---

