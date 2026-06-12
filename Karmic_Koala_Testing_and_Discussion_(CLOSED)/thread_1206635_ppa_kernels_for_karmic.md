---
title: "ppa kernels for karmic"
date: 2009-07-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dc2447 on 2009-07-07
Hi - I have this bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/385293](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/385293)

So no wireless

Anyone suggest any ppa kernels worth investigating?

---

### Post by rudenko_ruslan on 2009-07-07
What about this: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

?

---

### Post by taavikko on 2009-07-07
> **dc2447 said:**
> Hi - I have this bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/385293](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/385293)

So no wireless

Anyone suggest any ppa kernels worth investigating?

Since you have the bcmwl-kernel-source installed
Check that the dkms has indeed build the module
"dkms status"
if not, then reinstall the bcmwl-kernel-source, if it fails
"man dkms" to find out how to build it yourself, after that, seek help on newer kernels.

Whups, you didn't have it installed?* read more carefully the bug report.
Then install "bcmwl-kernel-source"

---

### Post by dc2447 on 2009-07-07
> **taavikko said:**
> Since you have the bcmwl-kernel-source installed
Check that the dkms has indeed build the module
"dkms status"
if not, then reinstall the bcmwl-kernel-source, if it fails
"man dkms" to find out how to build it yourself, after that, seek help on newer kernels.

Whups, you didn't have it installed?* read more carefully the bug report.
Then install "bcmwl-kernel-source"

I had bcmwl-kernel-source installed, dkms status looked ok.  I removed bcmwl-kernel-source, reinstalled, rebooted

still have

> Jul  7 16:52:29 d420 kernel: [   15.943722] wl: module license 'MIXED/Proprietary' taints kernel.
Jul  7 16:52:29 d420 kernel: [   15.943731] Disabling lock debugging due to kernel taint


and no working wireless

Isn't that was the launchpad bugs says?

---

### Post by xebian on 2009-07-07
> **dc2447 said:**
> I had bcmwl-kernel-source installed, dkms status looked ok.  I removed bcmwl-kernel-source, reinstalled, rebooted

still have



and no working wireless

Isn't that was the launchpad bugs says?

Not sure which kernel you are using but why use the ppa when the repo has the ubuntu patched kernels?  The latest is now 31-2.

I have the 30-8 from the repo which was working for my BCM4318 in Jaunty.  I just installed 31-2 also and it's working fine.  No need for compiling source.  I don't even have dkms installed.

---

### Post by dc2447 on 2009-07-07
> **xebian said:**
> Not sure which kernel you are using but why use the ppa when the repo has the ubuntu patched kernels?  The latest is now 31-2.

I have the 30-8 from the repo which was working for my BCM4318 in Jaunty.  I just installed 31-2 also and it's working fine.  No need for compiling source.  I don't even have dkms installed.

I wasn't clear, wireless worked in Jaunty but not Karmic.

Kernel version to follow

---

### Post by jfernyhough on 2009-07-08
Is there a wireless on-off switch on your laptop?

At the moment my Acer (under both 31-1 and 31-2) defaults to wireless off, and I have to press the button to turn on once I've booted.

The other workaround I found for my Intel 5100agn under 30-10 was to do

$ sudo rmmod iwlagn
$ sudo modprobe iwlagn

It then brought wireless up; this hasn't been necessary (yet) in 31-2.

---

### Post by dc2447 on 2009-07-08
> **jfernyhough said:**
> Is there a wireless on-off switch on your laptop?

At the moment my Acer (under both 31-1 and 31-2) defaults to wireless off, and I have to press the button to turn on once I've booted.

The other workaround I found for my Intel 5100agn under 30-10 was to do

$ sudo rmmod iwlagn
$ sudo modprobe iwlagn

It then brought wireless up; this hasn't been necessary (yet) in 31-2.

Jeremy  fairly sure wireless is activated as I can see *some* access points, although I can't see my own, even though it has no ssid

iwconfig shows eth1 exists but is not associated with any access points

So in summary - in work, I can see all the ssid but can't authenticate


At home, I can't see my own ssid but can see others

This broadcom card worked fine in jaunty

---

### Post by dc2447 on 2009-08-01
Just wanted to bump my old thread as I am no closer to a fix.

In summary, my broadcom wirless is recognised, can scan networks but not join.

At home my WPA only network doesn't show up in network-manager.

I have no wireless issues since hardy

>  sudo lshw -c network
  *-network
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1c:26:49:65:44
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:efdfc000-efdfffff


> wconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received

pan0      no wireless extensions.

ppp0      no wireless extensions.



> 
lspci -v -s 0c:00.0
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
        Subsystem: Dell Device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at efdfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: wl
        Kernel modules: wl, ssb


syslog

> Jul  7 15:05:01 d420 kernel: [   16.158999] lib80211: common routines for IEEE802.11 drivers
Jul  7 15:05:01 d420 kernel: [   16.512726] wl: module license 'MIXED/Proprietary' taints kernel.
Jul  7 15:05:01 d420 kernel: [   16.512734] Disabling lock debugging due to kernel taint
Jul  7 15:05:01 d420 kernel: [   16.516833] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17


---

### Post by jfernyhough on 2009-08-01
$ sudo rmmod wl
$ sudo modprobe b43

---

### Post by dc2447 on 2009-08-02
> **jfernyhough said:**
> $ sudo rmmod wl
$ sudo modprobe b43

when I do this I can't even scan networks at all.

I should be using wl for the BCM4312, right?

---

