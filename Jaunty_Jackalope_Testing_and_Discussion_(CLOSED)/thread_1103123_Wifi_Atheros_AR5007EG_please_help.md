---
title: "Wifi Atheros AR5007EG please help"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by johnybv on 2009-03-22
Hello. I'm sorry if I am bugging you with this stupid question but i'm a noob. Also please excuse my english, it's not my native language. I recently installed Ubuntu Studio 9.04 (Jaunty Jackalope) Alpha 6 (X68-version), and I love it. 
The problem is my Wifi **Atheros AR5007EG**. It seems that Ubuntu mistakes my **Atheros AR5007EG** with **AR242x 802.11abg Wireless PCI Express**. 
I've read a lot of posts and tried different aproaches like **ndiswrapper**, [**http://madwifi-project.org/**](**http://madwifi-project.org/**). with no succses (i'm a noob). I even installed **linux-backports-modules-jaunty**. I think I mixed them all up or did something wrong, so I deleted the partitions and installed a fresh version. 
Now I'm trying to follow the instructions from [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and im getting some signall or something, but still not working(cause its still sees my wifi as AR242x 802.11abg). **Any help will be very aprechiated.**


Here are some details about my configuration.
lspci -v | less
```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Device 1a3b:1026
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k_pci
        Kernel modules: ath_pci, ath5k
```

sudo iwconfig
```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I've tryed to set ESSID and password using System>Administration>Network + i changed the Frequency to 2.462 GHz to mach my router's settings.

Now it shoes:
```
wlan0     IEEE 802.11bg  ESSID:"Johnybv"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

But Encryption is off (does encryption key reffers to my passkey?). I read somewere that The Network GUI doesn't set up corectly the passkey. How can i set it up wright?

If i try:
sudo iwlist wlan0 scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:B0:BC:30
                    ESSID:"Johnybv"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=78/100  Signal level:-51 dBm  Noise level=-101 dBm
                    Encryption key:on
                    IE: Unknown: 00074A6F686E796276
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000247782a186
                    Extra: Last beacon: 736ms ago
```

+ if i try the ping command i get some responce from server but not from sites ex: [www.google.com](www.google.com)

If i try:
sudo ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:15:af:cf:d9:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:15:af:cf:d9:e2  
          inet addr:169.254.11.175  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-CF-D9-E2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

If I try:
sudo lsmod | grep ath
```
ath5k                 107008  0 
mac80211              217080  1 ath5k
led_class              12036  1 ath5k
cfg80211               38032  2 ath5k,mac80211
```

P.S. The Suport for Atheros 802.11 wireless LAN cards is **not activated**. 
Do I have to activate it? And could linux-backports-modules-jaunty package help me? Or what should I do to make my laptop see the corect Atheros Wifi card? I am [-o< you to please help me.

---

### Post by Flarkis on 2009-03-22
I have the same card as you so i know about the problems this card faces. Lucky for people like you and me the ath5k driver is now mature enough that we don't need the madwifi stuff. First of all Atheros AR5007EG = AR242x 802.11abg Wireless PCI Express. AR5007 is the product name and AR242x is the hardware identifier. You should have no need to follow any of those guides because they only applied to older kernel releases. The newer kernel in jaunty makes them non applicable.

Now im having trouble figuring out WHAT your problems is. Im guessing you cannot connect to you access point. Can you elaborate a little.

EDIT: after reading that afew times it seems you have DNS issues?

---

### Post by Reiger on 2009-03-22
Your ifconfig output shows that your card is **up & running**. That is **not** the same as having internet. 

To connect, try using Network manager to connect to your wireless network of choice. That should take care of the underlying commandline stack. If you don't like Network manager (like me) there are alternatives in the repositories, but you must be connected to the Internet first before you can install 'em. (For instance, wicd.)

---

### Post by johnybv on 2009-03-22
OMG. I made it. Thanck you Flarkis, and Thanck you Reiger, and last but not least Thanck you Ubuntu Studio :). After Flarkis told me that the wifi card is ok and it should work, I started to concentrate at that Network GUI. Then Reiger suggested WICD. I got it and installed it. I had to remake new settings on my router to get it work but now it does. (I am posting this from wifi). WICD is an amazing tool. Problem with WIFI SOLVED

Offtopic
I gave it an update to ubuntu an update and now I have a small problem with mounting the fat32/ntfs partitions. For example when i Logon in ubuntu and start Audacious my playlist won't play(the files ar on an windows partition). First I have to go to "Start">Places>Windows icon. It waits a second or 2 while is "re"-mounting,  after witch my playlist becomes available for singing.

Apart from that everything is perfect. **Thanck you again for the support**, and I hope to learn as much as possible so that I can too help others ho have problems. 
You may erase this post if you desire.

---

### Post by Reiger on 2009-03-22
Stuck? It may take a while to obtain an IP address but if WICD is truly unable to connect it will automatically abort connecting.

Three things spring to mind:
(a) Perhaps, maybe, you just need to have a little more patience. It could be that your router/connection is just a little slow at DHCP.
(b) You have a problem with obtaining an IP address over DHCP from your router (for instance you do not have a DHCP server within your LAN, nor does the router take up this task). Too bad: manually assign a fixed IP address for your card on your router.
(c) You use MAC (hardware) address filtering in your router, but you have forgotten to whitelist your hardware. Either whitelist your hardware (use the HWAddr field output by **ifconfig** from the terminal), or disable MAC (hardware) address filtering altogether.

Both (a) and (b) require that you are connected to your LAN (so you'll have to use ethernet) and that you have access to your router's settings. Typically the router in a home network has an IP address of 192.168.1.1 or 192.168.2.1 or similar; type the IP address of your router in the address bar of your favourite browser to access its control panel from which you can adjust the device.

---

### Post by johnybv on 2009-03-22
You posted just while i was edditing my last post :) But Thancks. Now it works perfect.

---

### Post by mbott on 2009-04-07
What speed are you getting?  With madwifi under 8.04, I used to get connections at 54 Mb/s most of the time.  Under 9.04 I'm lucky to see numbers over 2 Mb/s.  So far, this issue is the only one I've had with 9.04.  

-- 
Mike

---

### Post by mbott on 2009-04-20
With linux-backports-modules-jaunty, my wireless issues were fully resolved. As I said before I was getting 1MB bit rate and it would not work over 24. It's now showing 54MB and working with no issues.

-- 
Mike

---

### Post by Polygon on 2009-04-20
its a bug in the linux kernel that misreports your wireless card, not ubuntu. I have gotten the same thing in arch linux.

and ath5k USED to work, now it doesn't at all for some reason (with my laptop)

but its not because your card is being misdetected, like i said, it USED to work for me like a month ago but then an update happened and now it doesn't work at all :3

---

