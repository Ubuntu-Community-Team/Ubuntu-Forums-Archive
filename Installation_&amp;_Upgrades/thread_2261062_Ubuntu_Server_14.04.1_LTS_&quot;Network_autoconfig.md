---
title: "Ubuntu Server 14.04.1 LTS &quot;Network autoconfiguration failed&quot;"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by kieran6 on 2015-01-16
Hi there!

Just downloaded Ubuntu Server 14.04.1 LTS from the official website and created a bootable USB drive.

I boot from this drive and get to the Ubuntu Installation menu fine. It asks me to choose my language, keyboard layout etc.
Then it starts trying to configure the network, and gets stuck trying to configure DHCP giving the message:

"Network autoconfiguration failed. Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.
To narrow it down, DHCP is enabled on the network, and the server is working fine. There are many other computers currently on the network with no problem using DHCP.
The computer is plugged in via ethernet cable.
The network hardware is onboard, there are no extra network cards plugged in.

If it helps at all, the system specs are:

3.3ghz intel i5 processor
16gb DDR3 RAM
120gb SSD

I'm guessing the problem is that the installer doesn't know how to use the network adapter. I've only really dealt with windows in the past, and I was unable to get internet connection until the operating system was installed and network drivers installed.

EDIT: The installer also never asked where to install the operating system, does this mean it's trying to install on the flash drive?

Any help on this matter would be greatly appreciated.

Thanks in advance.

---

### Post by TheFu on 2015-01-16
Disconnect the network and install without it.
After the install goes through and reboots, connect up the network and we can troubleshoot.

BTW - can you boot a liveCD and test the networking? Don't think server supports this - perhaps a desktop liveCD can be used for this?

---

### Post by kieran6 on 2015-01-16
Thank you for the response. It's not possible to install without the network as it requires files from a mirror to continue.
However, I updated the BIOS for my motherboard and that has solved the problem and allowed me to continue. Go figure.

---

### Post by TheFu on 2015-01-16
> **kieran6 said:**
> Thank you for the response. It's not possible to install without the network as it requires files from a mirror to continue.
However, I updated the BIOS for my motherboard and that has solved the problem and allowed me to continue. Go figure.

Odd - I **always** install without any network configuration and don't have any issue. Plus it is much faster since time isn't spent downloading anything. I only install a base server + ssh - nothing else.

---

### Post by kieran6 on 2015-01-16
Hmm, I dunno then. I tried to continue with the installation without the network but I couldn't find a way to do it as it would always end up redirecting me to the "select a mirror" page after a few steps.

---

### Post by MAFoElffen on 2015-01-16
At what step of the install does it ask you for that?

I'm with Fu... But you are not wrong either. See attached. At "Detect Network Hardware" and "Configure Network", it hits the NIC and tries to autoconfigure... You have the option to go on and install without.

At install and configure software, 

If you select "SSH Sever" as your only option, it will install that from the CD and finish. 

If you pick any other option, it will try to get a network connection, use DNS to hit a mirror to download packages. So, in that point of the Install, for you, select "only" ssh sevrer and go on... IOt can get that off the disk and not have to download anything... Do not worry, you can always do this from a CLI prompt
```

sudo tasksel

```
... and it will that you back to the same tasksel software install mene that is on the install disk.

Once the install is complete, then Fu (or someone else) can help you to resolve the networking issue. Easier to diagnose that with a working system seeing what it's interpreting the hardware as, and such.

---

