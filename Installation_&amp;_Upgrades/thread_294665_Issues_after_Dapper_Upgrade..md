---
title: "Issues after Dapper Upgrade."
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by bootbat on 2006-11-06
All...

I had a triple boot machine with XP, FC5, and Ubuntu Breezy (5.10), with Ubuntu being the primary OS. Last week, I decided to upgrade both my Linux distros. Although I could have upgraded to 6.10, I got some feelers that it is best not to upgrade at the moment. I decided to upgrade Fedora Core to FC6 and Ubuntu to Dapper. FC6 upgrade went flawlessly and everything seems to be working fine. 

I checked some threads here to find out about things I should prepare with before the Dapper upgrade. I followed the thread: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) and used the method **"Upgrading by changing sources and the command line"**. 

Upgrade went fine. However, after I rebooted, I found that I have the following problems:

1. It gets stuck while booting @ "Configuring Network Interfaces"
2. Starting PCMCIA services while booting fails.
3. My sound remains muted after boot which I have to enable.

I resolved the second problem by turning off PCMCIA services. However, the other two persists. I do not have wifi. It is a single machine with IP addresses assigned statically. I understand that I can comment out auto eth0 in /etc/network/interfaces to get around this problem. Understandably, my connection needs to be activated after I boot back. "Configuring Network Interfaces" can be bypassed by using Ctrl + C during bootup. These two are not solutions but more of workarounds which I was not looking for. I searched the forum somemore and found a reference to ifplugd. I understand that I need to comment out "auto eth0" and use ifplugd somehow. I am not sure of what I have to do. I would really like to know whether this would solve the problem that I have. If yes, please let me know how to use ifplugd to resolve this as I could not find it anywhere. I can provide any information you might need for this. I love Ubuntu and it will remain my primary OS regardless of whether this works out or not. I will live with it:D. However, just checking if I can get some headsup on this.

My sound does work. I can listen to my music CDs. However, after boot the sound icon remains muted. A niggling irritation to have to enable it everytime. Besides, I love the music when Ubuntu boots up or shuts down. When I take the cursor over the icon, it says "Master Muted". I have to open volume control and remove the mute. I really do not know what to do. I will really appreciate any help here as well. I am willing to work hard to get this thing to work properly and yes, I do not expect everything to work out of the box.....

---

### Post by Najand on 2006-11-07
Well, for the third issue, use "alsamixer" to setup your sound level/volume. It would probably work fine afterwards.

---

### Post by bootbat on 2006-11-07
Thank you Najand for a quick response...I did try > sudo alsamixer earlier and increased the sound level for master to maximum. Quit by pressing > q. However, after I reboot it still remains muted. I am sorry I missed posting that part earlier. Apologies

---

### Post by bootbat on 2006-11-07
I solved the problem related to "Configuring Network Interfaces" by commenting ALL lines EXCEPT:

auto lo
iface lo inet loopback

in the file /etc/network/interfaces....

That seems to work...Rebooted a number of times after this....it seems to be booting fine now...

If only I can get this niggling sound issue taken care of I will be really thankful.

---

### Post by Najand on 2006-11-08
> **bootbat said:**
> I solved the problem related to "Configuring Network Interfaces" by commenting ALL lines EXCEPT:

auto lo
iface lo inet loopback

in the file /etc/network/interfaces....

That seems to work...Rebooted a number of times after this....it seems to be booting fine now...

If only I can get this niggling sound issue taken care of I will be really thankful.

Hmm, seems your *alsa-utils* cannot restore the */var/lib/alsa/asound.state* state. Hmm, can you send us a copy of /etc/init.d/alsa-utils?

---

### Post by bootbat on 2006-11-08
Thank you, Najand...I will post the contents of /etc/init.d/alsa-utils once I reach home from work. Really appreciate your taking time off for this.

---

### Post by bootbat on 2006-11-08
> Hmm, seems your alsa-utils cannot restore the /var/lib/alsa/asound.state state. Hmm, can you send us a copy of /etc/init.d/alsa-utils?

Find it attached herewith. Thank you!!

Also the problem related to "Configuring Network Interfaces" has cropped up again. I really do not know what to do..I am posting the output for lspci -v:

> 0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I /O Controller (rev 04)
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, fast devsel, latency 0
Capabilities: [e0] #09 [2109]

0000:00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Expres s Chipset Family Graphics Controller (rev 04) (prog-if 00 [VGA])
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, fast devsel, latency 0, IRQ 5
Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
I/O ports at e400 [size=8]
Memory at c0000000 (32-bit, prefetchable) [size=256M]
Memory at d0180000 (32-bit, non-prefetchable) [size=256K]
Capabilities: [d0] Power Management version 2

0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, medium devsel, latency 0, IRQ 23
I/O ports at e000 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at e100 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at e200 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at e300 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, medium devsel, latency 0, IRQ 23
Memory at d01c0000 (32-bit, non-prefetchable) [size=1K]
Capabilities: [50] Power Management version 2

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: d0000000-d00fffff
Capabilities: [50] #0d [0000]

0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FR W (ICH6 Family) AC'97 Audio Controller (rev 04)
Subsystem: Micro-Star International Co., Ltd.: Unknown device b010
Flags: bus master, medium devsel, latency 0, IRQ 17
I/O ports at e500 [size=256]
I/O ports at e600 [size=64]
Memory at d01c1000 (32-bit, non-prefetchable) [size=512]
Memory at d01c2000 (32-bit, non-prefetchable) [size=256]
Capabilities: [50] Power Management version 2

0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family ) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at <unassigned>
I/O ports at <unassigned>
I/O ports at <unassigned>
I/O ports at <unassigned>
I/O ports at f000 [size=16]

0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Contr oller (rev 04) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
I/O ports at e900 [size=8]
I/O ports at ea00 [size=4]
I/O ports at eb00 [size=8]
I/O ports at ec00 [size=4]
I/O ports at ed00 [size=16]
Capabilities: [70] Power Management version 2

0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
Subsystem: Micro-Star International Co., Ltd.: Unknown device 7131
Flags: medium devsel, IRQ 11
I/O ports at 0500 [size=32]

0000:01:02.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
Subsystem: Conexant Dynalink 56PMi
Flags: bus master, medium devsel, latency 32, IRQ 9
Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
I/O ports at d000 [size=8]
Capabilities: [40] Power Management version 2

0000:01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
Subsystem: Micro-Star International Co., Ltd.: Unknown device 131c
Flags: bus master, medium devsel, latency 32, IRQ 23
I/O ports at d100 [size=256]
Memory at d0020000 (32-bit, non-prefetchable) [size=256]
Capabilities: [50] Power Management version 2

Also ifconfig gives this:

> eth0 Link encap:Ethernet HWaddr 00:11:09:13:238
inet addr:10.129.16.105 Bcast:10.255.255.255 Mask:255.255.255.0
inet6 addr: fe80::211:9ff:fe13:23d8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:54881 errors:0 dropped:0 overruns:0 frame:0
TX packets:2117 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:5305228 (5.0 MiB) TX bytes:343564 (335.5 KiB)
Interrupt:23 Base address:0xd100

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:14 errors:0 dropped:0 overruns:0 frame:0
TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:588 (588.0 b) TX bytes:588 (588.0 b)

I suspect that the system is using or detecting a wrong sound device which is why I have a problem with sound. Usually, activating the surround facility works but mine has not. I installed gnome alsa mixer to activate both master and surround. I really do not know what else I can try. Any help is appreciated.

---

### Post by Najand on 2006-11-08
Hmm, there is no problem with your file. But there is a reason it cannot overwrite to the asound.state file. Hmm, let us remove /var/lib/alsa/asound.state and then set the volumes, etc. using alsamixer and then store the state using:
```

sudo alsactl store 0

```

Then check the permission privillege of the file /var/lib/alsa/asound.state and see if it is "*544 (-rw-r--r--) root:root*" or not.

After you do this, just restart alsa by running:
```

sudo /etc/init.d/alsa-utils restart

```
and see if it works or not?

---

### Post by Najand on 2006-11-08
About "Configuring Network Interfaces", it just do a "ifup -a" and it just  ifup the state of networks written in /var/run/network/ifstate... So just run that command and see if it errors or not? And also copy and paste the your ifstate file here, please...

---

### Post by zasf on 2006-12-31
> **Najand said:**
> Hmm, there is no problem with your file. But there is a reason it cannot overwrite to the asound.state file. Hmm, let us remove /var/lib/alsa/asound.state and then set the volumes, etc. using alsamixer and then store the state using:
```

sudo alsactl store 0

```

Then check the permission privillege of the file /var/lib/alsa/asound.state and see if it is "*544 (-rw-r--r--) root:root*" or not.

After you do this, just restart alsa by running:
```

sudo /etc/init.d/alsa-utils restart

```
and see if it works or not?

YESSSS!!! sound works again!! I don't know exactly what happened but wine broke my sound configuration, now it works again

```
matteo@burnt:~$ sudo mv /var/lib/alsa/asound.state /tmp/
matteo@burnt:~$ sudo alsactl store 0
matteo@burnt:~$ vdir /var/lib/alsa/asound.state 
-rw-r--r-- 1 root root 4.7K 2006-12-31 16:22 /var/lib/alsa/asound.state
matteo@burnt:~$ sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                 [ ok ] 
 * Setting up ALSA...                                                    [ ok ] 
matteo@burnt:~$ 

```

Thank oyu so much

---

