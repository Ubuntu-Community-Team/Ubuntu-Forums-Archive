---
title: "Network disconnected after update"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by Droidling on 2010-07-23
I am a novice at all things Linux related so forgive me if I am missing something obvious.

I installed 10.04 yesterday. The computer had an MS OS on it but I chose to format the entire HD for Ubuntu. The install seemed to go fine. When logged in there were updates available, and I installed all of them. After a reboot I tried getting on the internet and found that my network was 'disconnected'. I've checked the cabling, and that the LAN is still enabled in the BIOS. I assume the network had to have been functioning to do the original update. How do I figure out what changed. 

I've been reading the network section of a Linux book and came up with a little data that might help. My hardware is listed after the host file.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4c:b6:6b:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:34 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:141752 (141.7 KB)  TX bytes:141752 (141.7 KB)

etc\hosts:

127.0.0.1	localhost
127.0.1.1	BlueGender

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Hardware:
10.04 Lucid Lynx
Asus P7h55-m pro
  Realtek 8112L Gigabit LAN
Intel i3-530
2GB Crucial Balistix DDR3

---

### Post by thieved on 2010-07-23
Same thing happened to me.
I updated my desktop with 10.04 last night, and when I rebooted  this morning (wasn't required after updates) my router was 'disconnected' though everything checks out physically, and the windows box in my house works fine.

Also our laptop running 9.10 is having the same issue. I thought it might just be a hardware issue but then this happened to my desktop.

Any help would be much appreciated.

---

### Post by thieved on 2010-07-23
So I tried 
> sudo service NetworkManager stop
and then a reboot and it seemed to be working fine.

See this thread:
[http://kubuntuforums.net/forums/index.php?topic=3112347.0]("http://kubuntuforums.net/forums/index.php?topic=3112347.0")

---

### Post by Droidling on 2010-07-23
> **thieved said:**
> So I tried 

and then a reboot and it seemed to be working fine.

See this thread:
[http://kubuntuforums.net/forums/index.php?topic=3112347.0]("http://kubuntuforums.net/forums/index.php?topic=3112347.0")

I tried stopping NetworkManager, and network-manager, as well as deleting the NetworkManager.state file and restarting the service. The network manager no longer displays but there is still no internet connection and I'm not able to mount my network.

---

### Post by Droidling on 2010-07-23
New info that might help. My board has a realtek 8112L NIC is it being misidentified in the excerpt below? How do you tell what devices are included in a particular module?
$dmesg
…
[    1.601025] Freeing unused kernel memory: 876k freed 
[    1.601199] Write protecting the kernel read-only data: 7680k 
[    1.614787] udev: starting version 151 
[    1.631635] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    1.631655] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    1.631694] r8169 0000:02:00.0: setting latency timer to 64 
[    1.631735]   alloc irq_desc for 34 on node -1 
[    1.631738]   alloc kstat_irqs on node -1 
[    1.631752] r8169 0000:02:00.0: irq 34 for MSI/MSI-X 
[    1.632290] eth0: RTL8168d/8111d at 0xffffc90000356000, e0:cb:4e:b9:6e:d6, XID 083000c0 IRQ 34 
[    1.638297] pata_jmicron 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    1.638331] pata_jmicron 0000:05:00.0: setting latency timer to 64 
...

I tried configuring a static IP through the GUI. For a while the network manager indicated 2 arrows one pointing up and the other down. I assumed that meant I had a connection. I couldn't even ping the router. After a reboot it went back to disconnected. 

I've been reading and messing around with this all day. I really could use some help.

---

