---
title: "Ubuntu Hoary Davicom Ethernet Adapter"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by audax321 on 2005-04-01
Hello everyone,

I tried running the Hoary LiveCD a while back and my Davicom ethernet controller (integrated in my Soyo Dragon2 Plus motherboard) wouldn't work.  Does anyone have a Davicom ethernet card now and can confirm that it works in Hoary.  I want to upgrade from Warty, but not lose my internet connection. Also, how often is the LiveCD updated, because I could just burn that and give it another try, but I just want to make sure its not the same one I tried before.

Thanks :)

---

### Post by alastair on 2005-04-01
I did a really cursory search for "davicom soyo linux" (etc.) and didn't come up with much. Perhaps you can do a better search for linux driver support? You might want to get booted and :

 - look at /var/log/syslog (see any "eth"/ethernet messages)
 - look at the output of "lspci -v" for ethernet chipset information

This might help you do a search for the chipset and any linux support. Unfortunately, there is always a chance that the manufacturer does not support linux. I hope this is not true. Good luck - and come back if you get anywhere and need any help.

---

### Post by audax321 on 2005-04-01
I know it's supported because I'm using it on warty, but the last time I tried Hoary the davicom card wasn't working. This was a while ago. I'm just wondering if anyone with the davicom has upgraded to hoary recently and can confirm that it is working now...

BTW, I was wrong in my first post, I had actually done a full upgrade to Hoary and found that the network card wasn't working and had to format to reinstall Warty. I was mistaking the Ubuntu livecd for the Kubuntu one. I'm going to burn the ubuntu livecd and see if I still have internet access.

But, if in the mean time, someone can confirm that an upgrade from Warty to Hoary won't keep the Davicom ethernet adapter from working, I'd appreciate it. Thanks again.

---

### Post by kleeman on 2005-04-01
I had exactly the same problem as you with a Yukon Gigabit on board ethernet which is handled by a sk98lin module. Worked in Warty but failed in all Hoary releases. I solved the problem by downloading the vendors latest driver which had a very user friendly install script. I notice your vendor has Linux driver downloads. Maybe you could try them out on a test partition (this was my route to success).

---

### Post by audax321 on 2005-04-01
Hmm, just checked but it seems the drivers are only for kernels 2.2.x and 2.4.x, I think the later kernels are supposed to support it directly?

Unfortunately, I don't have another partition I can set this up on.. small HD. Anyway, the livecd just finished so I'm going to give that a try and see what happens.

---

### Post by kleeman on 2005-04-01
One other thing worth checking is whether the latest Knoppix works. It has a 2.6.10 kernel and the sk98lin module did not work for me on their kernel either. What module is the correct one for your adaptor?

---

### Post by audax321 on 2005-04-01
Not entirely sure, but this is what lspci -v gave me:

0000:02:07.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip co mpatible 10/100 Ethernet (rev 40)
        Subsystem: Davicom Semiconductor, Inc.: Unknown device 8212
        Flags: bus master, medium devsel, latency 32, IRQ 209
        I/O ports at d200
        Memory at f3040000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

Looks like DEC-Tulip...

---

### Post by kleeman on 2005-04-01
Looks like it is dmfe. Does this show up with lsmod in warty? In hoary what does modprobe dmfe give as root? BTW you should perhaps lodge a bug report on this...

---

### Post by audax321 on 2005-04-01
I just booted into the Hoary Live CD and am posting from there, so the network card appears to work... and lsmod does list dmfe.

I wonder why the network card wouldn't work when I upgraded from Warty before??? Damn it, now I want to try upgrading again but I don't want to end up formatting... ](*,) 

Maybe they fixed the bug already? I just checked where I downloaded the iso from and the file was updated on March 30th. :)

---

### Post by kleeman on 2005-04-01
Well in my case it was a kernel bug so if the same is true for you then the latest kernel should be safe if you upgrade. Maybe....  8-)

---

### Post by audax321 on 2005-04-02
RRRRRRRRRRRRRGH.... just dist-upgraded to Hoary and my network card worked ................. until I rebooted. Now it can't access the internet or my local network. All the same modules are loaded and it seems like Ubuntu knows the card exists, it just can't do anything with it...  :-? 

It appears someone has posted a Bugzilla request about it, so hopefully something will come of it and I can just fix a package instead of having to format :-(

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8086](https://bugzilla.ubuntu.com/show_bug.cgi?id=8086)

Probably should have done a search for that before upgrading.

---

### Post by audax321 on 2005-04-02
What's really odd is that my laptop works fine with its Wifi card under Hoary.... DHCP works like its supposed to...  I wonder what is wrong with my desktop, there seems to be a lot of people with different network cards having problems with DHCP and Hoary.

---

### Post by audax321 on 2005-04-02
Since, the LiveCD worked, would it be a good idea to add the LiveCD as a source in apt to use the dhcp3 client from the LiveCD (3.0.1-1ubuntu1) to replace the dhcp3 client that is currently installed (3.0.1-1ubuntu4).

---

### Post by kleeman on 2005-04-02
Sounds like it is worth a shot. You could also just grab it directly off the cd.

---

### Post by audax321 on 2005-04-02
well, didn't work :(  guess something else is conflicting with dhcp...

---

### Post by alastair on 2005-04-03
If you look at the bug mentioned, the "dmesg" output shows "eth0" device created. Can you also look?

Check : /var/log/syslog

and look for lines like :

.....
Linux Tulip driver version 1.1.13 (May 11, 2002)
PCI: Found IRQ 10 for device 0000:00:10.0
tulip0:  MII transceiver #1 config 3100 status 7829 advertising 01e1.
eth0: Davicom DM9102/DM9102A rev 64 at 00017400, 00:08:A1:31:A8:EE, IRQ 10.
dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)
....

Then :

ifconfig -a
route -n

Also, use "ethtool" (install it perhaps) and :

ethtool eth0

---

### Post by audax321 on 2005-04-03
Running, dmesg, I found the following lines:

  Linux Tulip driver version 1.1.13 (May 11, 2002)
  ACPI: PCI interrupt 0000:02:07.0[A] -> GSI 22 (level, low) -> IRQ 22
  tulip0: MII transceiver #1 config 1000 status 782d advertising 01e1.
  eth0: Davicom DM9102/DM9102A rev 64 at 0001d200, (insert MAC here), IRQ 22.
  dmfe: Davicom DM9xxx net driver, version 1.36.4 (2002-01-17)

Not sure but the ACPI PCI interrupt line and the eth0 line have the same IRQ. Is that normal?

I also noticed these line elsewhere as well (below the ones above):

  IPv6 over IPv4 tunneling driver
  eth0: no IPv6 routers present
  0000:02:07.0: tulip_stop_rxtx() failed


/var/log/syslog is just a giant log filled with output from dhclient eth0 trying to get an IP for it and saying No DHCPOFFERS received.

When I do ifconfig -a nothing gets configured for eth0, it still has no IP. But now ifconfig lists something called sit0:

  Link encap:IPv6-in-IPv4
  NOARP MTU:1480 Metric:1
  RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  collisions:0 txqueuelen:0
  RX bytes:0 (0.0 b) TX bytes (0.0 b)


And sudo ethtools eth0 displyed:

  Settings for eth0
  No data available.



Any ideas where to go from here?

---

### Post by audax321 on 2005-04-03
OKAY, PROBLEM FIXED.. kind of :)

We decided to upgrade to our network to gigabit since one of our three computers already had a gigabit card and we've been talking about it for awhile. The new card which is a Netgear GA311 worked perfectly and file transfer is nice and fast between our computers now, so its all good.

Thanks to everyone who tried to help and hopefully Ubuntu will figure out what is wrong with the Davicom drivers that is keeping that card from working properly.

---

### Post by atom on 2005-04-09
i was having this problem with a davicom dm9102 using the tulip driver. i put the dmfe driver in /etc/modules which caused it to load before the tulip driver and everything works now.

---

### Post by ischg on 2005-09-08
Thanks a lot! While I still don't know what the dmfe driver does, putting it in /etc/modules resolved the problem.

---

