---
title: "[SOLVED] Atheros ar928x wlan HELP"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mgiacchetti on 2008-09-26
i try to connect, but i get nothing... it just sits with one green dot in the icon,(the lower dot to be exact) then fails, and shows no signal.


uname -a
```

Linux ubuntu 2.6.27-3-generic #1 SMP Wed Sep 10 16:02:00 UTC 2008 i686 GNU/Linux

```lspci -nn
```

Network controller [0280]: Atheros Communications Inc. Device [168c:002a] (rev 01)

```ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:15:af:dd:7c:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-DD-7C-C9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```dmesg |grep wlan0
```

[   55.857897] ADDRCONF(NETDEV_UP): wlan0: link is not ready

``` dmesg |grep Atheros
```


[   41.906100] phy0: Atheros 9280: mem=0xf8be0000, irq=17

```

---

### Post by Mgiacchetti on 2008-09-26
*-network
                description: Wireless interface
                product: Atheros Communications Inc.
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 01
                serial: 00:15:af:dd:7c:c9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

---

### Post by Mgiacchetti on 2008-09-26
*update*

I have vista set up so that my bluetooth is off and wifi is on.

When I resteart into vista from ubuntu, bluetooth is on and wifi is off.  

I'm thinking this may be the sign of whatever problem I am having, considering it seems that my atheros in ubuntu is not transmitting at all when I try to connect...  However bluetooth is transmitting and receiving errors.

SO if this is the issue, i am wondering:

can i echo my wifi on?

in fixing another problem, my light sensor continually turns the screen really dark in ubuntu.  since the fn's dont work, i have to 
```

echo 0 > /sys/devices/platform/asus-laptop/ls_switch

```

Is there a way to do this to the bluetooth and wifi to turn them off and on, respectively?

---

### Post by Mgiacchetti on 2008-09-26
```

sudo su[FONT=monospace] 
[/FONT]enter your password
echo 0 > /sys/devices/platform/asus-laptop/bluetooth
echo 1 > /sys/devices/platform/asus-laptop/wlan 

```

---

### Post by AlexH76 on 2008-10-02
Sweet victory! 

This was indeed the final step to get my ath9280 connecting with my wireless router. (laptop used: asus x71a)

---

### Post by trippnk on 2008-10-02
Can you please clarify what you did exactly to make your wireless work.  I have the M50Vm and I get the same single green dot but no love on connecting.

---

### Post by AlexH76 on 2008-10-06
You installed the new driver as explained in [this thread]("http://ubuntuforums.org/showthread.php?t=894177")?

What does iwconfig show?

After installing the driver all I needed to do was 'echoing' wlan on (as explained above)

---

### Post by trippnk on 2008-10-06
I'll try that when I get home from work and let ya know if that fixed it.

---

### Post by trippnk on 2008-10-07
Okay, the fix works awesome.  One question though, anyway to make it where I don't have to open terminal and run those commands each time I restart?

---

### Post by AlexH76 on 2008-10-08
Sure. Use the /etc/rc.local file: 

I find it not necessary to switch bluetooth off, so a few lines like these will do the trick:

```
# switch wlan on

echo "1" > /sys/devices/platform/asus-laptop/wlan && \
    /sbin/ifup wlan1
```

---

### Post by trippnk on 2008-10-08
I'll give it a try.  From what you posted I put something similar in for the light sensor... will this work?

# switch ls off

echo 0 > /sys/devices/platform/asus-laptop/ls_switch

---

