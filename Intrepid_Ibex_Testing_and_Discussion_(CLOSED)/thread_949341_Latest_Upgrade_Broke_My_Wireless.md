---
title: "Latest Upgrade Broke My Wireless"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by igb on 2008-10-16
Today's upgrade seems to have broken my wireless connection, which has worked fine up to now. My wireless chip is:

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

iwconfig shows no wireless extensions found:

```
ian@scamper:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

dmesg shows that the adaptor was detected OK:

```
[   17.352064] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   17.352206] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
```

Ian.

---

### Post by BackwardsDown on 2008-10-16
I'm having the same problem with the same wireless-card.

---

### Post by orduek on 2008-10-16
same here.

---

### Post by Bucky Ball on 2008-10-16
```

wlan0     IEEE 802.11abg  ***ESSID***:""
          Mode:Managed  Frequency:2.412 GHz  ***Access Point: Not-Associated***
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```Your wireless is happening you're just not talking to your router as you have no access point associated. You need to put in the ESSID and any security details in System->Admin->Network or whatever gui you are using for this purpose.

---

### Post by cmccauley on 2008-10-16
If this

iwlist wlan0 scan

works then you probably just need to re associate.

Chris

---

### Post by BackwardsDown on 2008-10-16
niels@inoue:~$ iwlist wlan0 scan
Wlan0     No scan results

---

### Post by napsy on 2008-10-16
Hello.

I have the same problem with my Intel wireless.

dmesg complains something about "iwl3945: Could not read microcode -2"

Any ideas how to fix this?

---

### Post by igb on 2008-10-16
> **BackwardsDown said:**
> niels@inoue:~$ iwlist wlan0 scan
Wlan0     No scan results

Same here.

Ian.

---

### Post by BackwardsDown on 2008-10-16
The problem is fixed by installing the latest linux-firmware, it's already in the update's.

See [http://ubuntuforums.org/showthread.php?t=948665](http://ubuntuforums.org/showthread.php?t=948665)

---

### Post by neko21 on 2008-10-16
It also broke my wireless :(  Whats even more disturbing is that it also broke it in osx on my macbook pro!!!  As i have installed it on boot camp.  Has anyone else had this problem?

---

### Post by UberWookieks on 2008-10-17
Neko, I'm dual-booting on a Macbook and the update broke my wireless, but my OSX partition remains unaffected.

---

### Post by UberWookieks on 2008-10-17
I reinstalled, and the second set of updates killed it a second time. I just reinstalled again but will not update until this gets sorted out.

---

### Post by Lorenz on 2008-10-17
I didn't update now since the 15th, is the problem still there or already fixed?

---

### Post by igb on 2008-10-17
> **BackwardsDown said:**
> The problem is fixed by installing the latest linux-firmware, it's already in the update's.

See [http://ubuntuforums.org/showthread.php?t=948665](http://ubuntuforums.org/showthread.php?t=948665)

The update hasn't appeared on my system, so I tried downloading the deb directly. This gets wireless working again, but performance is dire. In fact it's so bad it's unusable.

I'll wait a few days and see what happens when the offical fix appears in my update[B]s.

Update:[/B] I tried installing linux-firmware_1.1_all.deb instead of nic-firmware_1.1_all.deb and my wireless connection is now going at normal speed.

Ian.

---

### Post by Nhorning on 2008-10-17
I had a similar bug where I couldn't connect to a non-static IP.   It was a Kernel bug. Booting with 2.6.24-19 Generic fixed the problem.  You should all try that if updates don't work.

---

### Post by UberWookieks on 2008-10-17
Just so you all know, the update broke my wireless, but on advice from [this]("http://ubuntuforums.org/showthread.php?t=948434") thread, I hit Esc at boot and chose the non-safe-mode version of the .19 kernel, and my wireless functioned normally after booting.

---

### Post by Bucky Ball on 2008-10-17
> **UberWookieks said:**
> Just so you all know, the update broke my wireless, but on advice from [this]("http://ubuntuforums.org/showthread.php?t=948434") thread, I hit Esc at boot and chose the non-safe-mode version of the .19 kernel, and my wireless functioned normally after booting.

If you mean the first kernel on the list, you should be booting from that anyway, not safe mode. :)

---

### Post by Scheater5 on 2008-10-17
Just another voice in the choir:
Latest kernel update borked my intel wireless ("broke" in software sense - not bricked)
Choosing an old kernel at boot lets wireless work
Reinstalling firmware and/or linux-restricted-modules-common still does not allow newest kernel to use wireless

---

### Post by UberWookieks on 2008-10-18
> **Bucky Ball said:**
> If you mean the first kernel on the list, you should be booting from that anyway, not safe mode. :)

Sorry, I'm new to the Ubuntu thing and your terminology. I am a recent convert from Gentoo, and I'm used to being a bit more of a computer slob than Ubuntu allows, and when I compiled my kernels in the past, I just used the last one I managed to get functioning from the list in GRUB if the new one was dysfunctional.

My safe-configuration Kernel was usually labeled something like:

Linux-2.6-X-Try-this-crap-now.

---

### Post by Bucky Ball on 2008-10-18
Cool, got ya. You could try running the second one down (recovery) and see if that spits any errors and work from there. :)

---

### Post by colinpat on 2008-10-19
I can't get wireless in the 2.6.27 kernels.  2.6.24-19 works ok.

In latest network manager shows connected with ip address but I can't ping anything, firefox times out and evolution timesout trying to connect.

colin@colin-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"qms"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:72:20:5B:53   
          Bit Rate=36 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-22 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

pan0      no wireless extensions.

---

### Post by caryb on 2008-10-19
Thanks for the tip, now have wireless back again:) Now to get it to autostart with knetworkmanager in Kubuntu.


Cary

---

### Post by brandoncolorado on 2008-10-19
I seem to be having a similar problem.  After partial-update, my card stopped working too.


  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:72:5b:a0:9d
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:5c:e2:1e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:13:fb:78:c2:eb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A

---

### Post by sharp65 on 2008-10-19
I'm having the same problem as everyone else. How did you get it fixed with the latest kernel?

---

