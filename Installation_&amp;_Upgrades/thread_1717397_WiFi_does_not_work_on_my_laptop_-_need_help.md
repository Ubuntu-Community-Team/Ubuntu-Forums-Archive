---
title: "WiFi does not work on my laptop - need help"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by dindoliya on 2011-03-29
I have having trouble getting the WiFi to work on my Gateway laptop model M6752. It has the Marvell Technologies Ethernet card. I am attaching the output of various commands like lpsci - nn, ndiswrapper -l etc. I have followed the instructions from one of the threads and got the driver installed. It even says that the device is present. I don't know why it is not connecting.
Also, Under System->Administration->Network Tools, it is showing on Local Loopback and wired eth0 interface. The wireless interface is not showing up there. Attached is the text file with information that may help point to the problem. Please help!

I am using ubuntu 10.10, 32 bit

---

### Post by lkraemer on 2011-03-31
It appears that you have ndiswrapper installed because your computer has
a driver installed and present, but that doesn't work.

1. Did you install ndiswrapper and some specific driver?
2. How many methods have you tried?  Post the output of:
**history > junk.txt**
3. Have you connected your Laptop via Ethernet Patch Cable and did the "UPDATE"?
4. Have you tried to locate the NEW Hardware drivers after Step #3?
5. Will you post the output of **lsmod**, so we can see what conflicting
modules you may have loaded?
6. Will you post the output of: 
**cat /etc/modprobe.d/blacklist.conf** 
7. Will you post the output of:
**dmesg | grep -e iwl -e wlan**
8. Are you sure that the Wifi is ENABLED? Is there a Switch or Special
Keystrokes (maybe CNTL F2) that turns it ON/OFF?  Don't worry about the LED's Color.

I'm thinking you should start with the following, but only after we
review what you have done so far.......

Let's clean up the Windows drivers by removing them along with ndiswrapper.

**Open a Terminal Window (Console):**

**REMOVE WINDOWS DRIVERS:**
If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. as an EXAMPLE, if memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.

Once you have this corrected, and ndiswrapper -l (MINUS LOWERCASE "L") try:
```

sudo /etc/init.d/networking restart

```
or reboot. You should have the Wifi functional. If it isn't move your mouse over the Wifi Icon in the Top Right Toolbar, then RIGHT click and ENABLE the WIFI. It must be ENABLED.


To try and Manually set up the Wifi try:
[B]
MANUAL SETUP:[/B]
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and Wlan0
```

sudo iwconfig Wlan0 essid "Airlink"

```
It shouldn't take more than about 15 minutes......


lk

---

### Post by dindoliya on 2011-04-01
Thank you! I have been able to get the ndiswrapper to work and i am able to connect to the wireless network. However, I do not get any IP address from the wireless router. I disabled WPA so I could take that out of the equation. Even with an unsecure network, I am not getting any IP address. Here is the output of the follwing commands:
---------------
deepak@deepak:~$ ndiswrapper -l
netmw14x : driver installed
	device (11AB:2A08) present
---------------------

deepak@deepak:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
---------------------
deepak@deepak:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

