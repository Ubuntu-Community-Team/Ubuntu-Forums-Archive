---
title: "wireless won't connect"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by /usr/err on 2005-04-25
I have a Broadcom 54G wireless card in my eMachines m6805 laptop and I'm currently unable to get it to connect.  Using the HOWTO information found in [this thread](http://www.ubuntuforums.org/showthread.php?t=25683) I was able to get the ndiswrapper information installed and the wireless radio working along with wlan0 established.

However, after configuring the wireless network (essid, WEP key, etc), I can't get a connection.  I've tried numerous things (and read numerous posts) to no avail.  I've verified the WEP key is correct.  The wireless access point does work as well, I've used this router for well over a year now with Windows XP Pro.

I'm certain it is probably just a configuration issue, but I'm very new to wireless in Linux, so I'm currently at a loss.

I'm including my /etc/network/interfaces below along with the output of 'ifconfig' and 'iwconfig'.

**/etc/network/interfaces**
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
        wireless-essid toolshed
        wireless-key a1138a1138

auto wlan0

auto eth0

```
Note that while eth0 works (I'm using it right now as a fallback), I had the network cable unplugged while trying to get the wireless to work, so it doesn't have an IP Address below.

**Output of 'ifconfig'**
```

eth0      Link encap:Ethernet  HWaddr 00:03:25:0D:B8:B2
          inet6 addr: fe80::203:25ff:fe0d:b8b2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:20592 (20.1 KiB)
          Interrupt:23 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1382598 (1.3 MiB)  TX bytes:1382598 (1.3 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:8A:E7:5A
          inet6 addr: fe80::290:96ff:fe8a:e75a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:d0000000-d0001fff

```
Note that despite the fact I have an essid defined, the ESSID: value below is 'off/any' and from what I've read, having an all 0's (zeros) Access Point: value means it is more than likely just a configuration issue, but I can't determine where the problem is.

**Output of 'iwconfig'**
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Thanks in advance for any help.  I'm liking Ubuntu a lot so far as I had almost everything work out of the box, except wireless (which I was prepared for given the Broadcom chipset, but I didn't expect it to be this problematic given all the good HOWTOs available -- setup was a breeze, but the d*** thing just won't connect).

---

### Post by tread on 2005-04-25
I'm not too great in setting up linux wifi either, but I just use the config tool provided in ubuntu. Theres even a gnome panel applet for it .. it will allow to set the interface, gateway, ip, essid etc.

Check it out, you may not have to fiddle around with config files. I've lost touch with manual config lately .. everything in ubuntu almost always just works for me  :-P

---

### Post by /usr/err on 2005-04-25
I've been using the System -> Administration -> Networking tool to configure the network settings; however, I did notice once that despite the fact I went in and updated my WEP key (on the Ubuntu machine and my router), it was not updating the Ubuntu /etc/network/interfaces file with the new WEP key despite the fact I updated the "Properties" and so forth in the Networking tool.  So that is when I started editing the file by hand.

I haven't yet seen the wireless applet appear, although I've heard others talk about it.  I seem to only have my eth0 ethernet applet up at any time; mousing over it shows it to be eth0, so I keep waiting to see a wlan0 applet appear, but none ever has.

I brought my laptop to work today to try to connect to the wireless connection there (which also used to work fine in Windows) and it too does not want to work.

Basically, using the aforementioned Networking tool, I "Activate" my wlan0 connection and it takes awhile for it to activate, but it does come back and say "The interface wlan0 is active".  I then click "OK" to close the Networking tool and again it sometimes takes awhile to close (not a good sign to me) and while 'iwconfig' and so forth show the wlan0 interface, it is just not connecting to any wireless networks, at all.

---

### Post by poofyhairguy on 2005-04-25
Its time to troubleshoot cowboy (or cowgirl, I don't know). First thing I would do is try and see if the card will coneect and work without a WEP on the router. If it works, then there is a problem with your WEP  (which is possible, I've had trouble getting non-128 bit WEPs to work with Ubuntu). If it doesn't work without the WEP, then your card is misconfigured. 

Please post results here.

---

### Post by /usr/err on 2005-04-25
I removed the WEP key (from the system and the router) and it still would not connect.

I then used the uninstall information found in the thread I linked to in my original post to uninstall ndiswrapper.  I then re-installed ndiswrapper and rebooted per the instructions.

Upon reboot, it appeared to recognize my wireless modem this time and started the wireless radio -- this did not occur the first time I installed ndiswrapper or during any other reboots I've made since (I had to use 'sudo modprobe ndiswrapper' to get it to turn on the wireless radio each time).  Here is the 'dmesg' information:

```
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 18 (level, low) -> IRQ 18
ndiswrapper: using irq 18
wlan0: ndiswrapper ethernet device 00:90:96:8a:e7:5a using driver bcmwl5
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
ndiswrapper: driver bcmwl5 (Broadcom,06/13/2003, 3.20.23.0) added
```

My system and router were still configured for no WEP, yet it still did not connect when the system came up.  Similar to before, it was listed as 'active' in the desktop Networking tool, but there was no connection.

Just for 'fun', I went ahead and setup a 128-bit WEP key since I had previously been using 64-bit keys.  That didn't work either.

 ](*,)

---

