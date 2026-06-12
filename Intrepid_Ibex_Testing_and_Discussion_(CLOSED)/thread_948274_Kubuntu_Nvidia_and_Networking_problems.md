---
title: "Kubuntu Nvidia and Networking problems"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by RIchard James13 on 2008-10-15
I last upgraded my Kubuntu Intrepid installation on the 10th of October. Now the Nvidia drivers that it loads crash. This leaves me with the command prompt only. From the command line I cannot access the network as something is not right. ifconfig shows my NIC fine but route returns only "Destination     Gateway         Genmask         Flags Metric Ref    Use Iface"

I think that the Nvidia problem lies with DKMS but I don't know how or where on the system it is running from and loading the Nvidia driver.

I don't know why the network is not working but I assume the service or daemon that does DHCP is not running.

Does anyone know how to fix either of these problems? Anyone :(

---

### Post by devoncatt on 2008-10-15
The networking problem
1.First ethernet or wireless
2.Did it ever work?
3. When you restart networking ( sudo /etc/init.d/networking restart) what   does it say ? or does demsg | grep -i netw anything?
4. Can you ping your router or any other computer on tthe network?
Devoncatt

---

### Post by dabl on 2008-10-15
> **RIchard James13 said:**
> 

Does anyone know how to fix either of these problems? Anyone :(


On the Nvidia problem, couple of suggestions:

1. I hear EnvyNG is in the Intrepid repos -- I haven't used it myself (with 8.10), but that would be the easy solution, if it works.  First

```
sudo apt-get install envyng-core
```

Then when it is installed, get out of X and at the tty console

```
sudo envyng -t
```

and choose #1 "Install the Nvidia driver".


2. The other way -- Depending on the model of your card, I'm getting great results with the downloaded Nvidia driver 177.80, from their web site.  First install the kernel-headers-$(uname-r) and build-essential packages, then get the correct arch of the Nvidia driver/installer package for your system, shut down the X server from the tty console:

```
sudo /etc/init.d/kdm stop
```

and then run the installer and answer "yes" to the questions.

---

### Post by RIchard James13 on 2008-10-16
> **devoncatt said:**
> The networking problem
1.First ethernet or wireless


Wired networking on a PCI 3Com Card
> 
2.Did it ever work?

It has always worked under Linux. In the case of this specific installation it has worked since I installed the alpha 3 build of Kubuntu. It is working right now in Ubuntu.
> 
3. When you restart networking ( sudo /etc/init.d/networking restart) what   does it say ? or does demsg | grep -i netw anything?
4. Can you ping your router or any other computer on tthe network?
Devoncatt

/etc/init.d/dhcpdbd restart
```
 * Restarting DHCP D-Bus daemon dhcdbd
   ...done.
```

/etc/init.d/networking restart
```
 * Reconfiguring network interfaces...
   ...done.
```

ifconfig
```
eth1      Link encap:Ethernet  HWaddr 00:01:02:fc:23:0c  
          inet6 addr: fe80::201:2ff:fefc:230c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11264 (11.2 KB)  TX bytes:468 (468.0 B)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

---

### Post by sokopok on 2008-10-16
I'm having similar problems right now, but I managed to (temporarily, very, very temporarily) fix the by using the VESA driver. Of course: no fancy graphics, and a horribly inadequate screen resolution (800x600). But at least you might be able to load the gui.
If you want to try this, add to the Device section of your /etc/X/xorg.conf:
```
Section "Device"
[INDENT]         Identifier      "Configured Video Device"
        Driver          "vesa"
[/INDENT] EndSection
```

---

