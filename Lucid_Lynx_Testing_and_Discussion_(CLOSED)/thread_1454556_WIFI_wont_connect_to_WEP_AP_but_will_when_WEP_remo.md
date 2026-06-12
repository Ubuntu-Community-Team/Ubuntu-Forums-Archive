---
title: "WIFI wont connect to WEP AP but will when WEP removed"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by samuelhug on 2010-04-14
I just got an Asus Eee PC 1201T and loaded it with Ubuntu 10.04. It works great except when I try to connect to my WEP encrypted WiFi access point. It works just fine when I remove the WEP encryption.

Following are the outputs of a few commands hopefully with some useful information. Any help would be appreciated.

lspci
```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
```

lsmod
```
r8192se_pci           486739  0 
```

iwconfig wlan0
```
wlan0     802.11bg  ESSID:"RoostingPigeon"  Nickname:"rtl8191SEVA1"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:06:25:97:E5:A6   
          Bit Rate=11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=86/100  Signal level=-53 dBm  Noise level=-113 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwlist wlan0 scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:06:25:97:E5:A6
                    ESSID:"RoostingPigeon"
                    Protocol:IEEE802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality=86/100  Signal level=-54 dBm  Noise level=-113 dBm
                    Extra: Last beacon: 18ms ago
```

lshw -C network
```
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:4b:d6:6e:0d:e9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:16 ioport:d800(size=256) memory:fbefc000-fbefffff
```

---

### Post by ubername on 2010-04-14
Can I ask a basic question - have you specified your WEP key?

You can do this from the network icon in your panel. Right Click > Edit connections, pick wireless tab, select (or create) an entry, click edit, select wireless security tab, fill in the details. I guess you must have done something similar to get your ESSID set up.

---

### Post by samuelhug on 2010-04-14
Yes, I entered in the WEP key when it asked for it I know I have the correct key because I downloaded the one I use on my other computers using my LAN line. After I enter the WEP key it sits there doing somthing for about 60 seconds then it asks for the WEP key again.

---

### Post by psyke83 on 2010-04-14
WEP encryption is not very secure, is your router capable of WPA or possibly WPA2? If not, a firmware update may provide new functionality.

I know that this isn't the answer to your question - sorry.

---

### Post by Bucky Ball on 2010-04-14
System->Admin->Network.

Enable roaming unticked. ESSID and WEP key. Configuration=Auto Configuration (DHCP).

Are you sure your router is set up to be a DHCP server, ie it serves your machine an IP when you attempt to log onto the network? Your other option is to force the IP from the computer by setting it up with a static IP (Configuration=static) and switch DHCP server OFF on the router. This would mean none of the other machines on the network would be served IPs by the router, of course, and would need to be set up with static IPs, too. ;)

---

### Post by samuelhug on 2010-04-14
The router I'm using is a Linksys BEFW11S4 I've looked before and have not been able to find a firmware upgrade from Linksys or DD-WRT.

---

### Post by Bucky Ball on 2010-04-14
I wouldn't worry about a firmware upgrade right now. See if you can sort this problem. Check my last post.

---

### Post by samuelhug on 2010-04-14
> **Bucky Ball said:**
> System->Admin->Network.

Enable roaming unticked. ESSID and WEP key. Configuration=Auto Configuration (DHCP).

Are you sure your router is set up to be a DHCP server, ie it serves your machine an IP when you attempt to log onto the network? Your other option is to force the IP from the computer by setting it up with a static IP (Configuration=static) and switch DHCP server OFF on the router. This would mean none of the other machines on the network would be served IPs by the router, of course, and would need to be set up with static IPs, too. ;)

The router itself is not the DHCP server its behind another router which is. The router in question works just fine when connected to from a different computer using WiFi.

---

### Post by Bucky Ball on 2010-04-14
Does it work just fine with an ethernet cable into the machine you are setting up? If you haven't already, plug one in and make sure you have updates. You could be missing something re wireless and that should pick it up.

If the router in question works fine with another machine, which router is serving it an IP? If another machine connects fine, it would suggest the problem would lie with the configuration of your computer. Is the other machine running Windows? Either way, have a look how the wireless is set up on the machine which is connecting fine.

---

### Post by samuelhug on 2010-04-14
> **Bucky Ball said:**
> Does it work just fine with an ethernet cable into the machine you are setting up? If you haven't already, plug one in and make sure you have updates. You could be missing something re wireless and that should pick it up.

If the router in question works fine with another machine, which router is serving it an IP? If another machine connects fine, it would suggest the problem would lie with the configuration of your computer.

Yes it works fine with an ethernet cable and I have all the updates. The router with the DHCP server is a Linksys WRT54G with DD-WRT (and broken wifi).
I'm currently trying the proprietary driver I found on Realtek's website I'm hoping this will fix it.

---

### Post by Bucky Ball on 2010-04-14
If it's a linux driver, possibly, but don't try a windows one! That might sound silly but you never know. ... Thing is, seems to be nothing wrong according to your read outs. Showing correct ESSID etc so I am thinking things are fine hardware-wise.

---

### Post by samuelhug on 2010-04-14
It Works!

I downloaded the linux driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE") then I ran the following commands 

```

sudo apt-get install linux-source-2.6.32
cd /usr/src
sudo tar xf linux-source-2.6.32.tar.bz2

#cd to where you downloaded driver

tar xf rtl8192se_linux_2.6.0015.0127.2010.tar.gz
cd rtl8192se_linux_2.6.0015.0127.2010
make

sudo su # required don't just sudo really weired
make install

```

this is based on info from [here]("http://ubuntuforums.org/showthread.php?t=1047374")

Thank you everybody for all your assistance.

---

