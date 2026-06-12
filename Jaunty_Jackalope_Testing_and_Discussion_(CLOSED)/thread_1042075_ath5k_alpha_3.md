---
title: "ath5k alpha 3"
date: 2009-01-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by thor2002ro on 2009-01-17
the driver seems to work i get the wireless interface in ifconfig but network manager says wireless disabled and the wireless checkbox is greyed
anyone any ideas?

i installed the backports

---

### Post by IanW on 2009-01-18
Try "gksu gedit /etc/modprobe.d/blacklist" and add these lines:-

# Ath5k fix
blacklist ath_pci
blacklist ath_hal

Then reboot.

---

### Post by thor2002ro on 2009-01-18
tryed no change

---

### Post by Limulus on 2009-01-19
Just wanted to add that its not working for me either.

I'm running an Acer Aspire One (A0A 110-1531) and testing Jaunty Alpha 3 on it.

I created a file "blacklist-ath" (with that same text) in the same dir and while that allowed various command line things to see something working (e.g. "dmesg|grep ath5k" went from "failed to wakeup the MAC Chip" to "registered as 'phy0'" and it now shows up as wlan0 when I run "sudo ifconfig"), if I click on the Gnome NetworkManager Applet, it says (in grey) "wireless is disabled" and when I right-click it, the "Enable Wireless" area is greyed out :/

I note that when I had this working with backports in Intrepid, I could go System -> Administration -> Hardware Drivers and select Ath5K as the appropriate driver, but now it doesn't show up in the list.

Anyone get Jaunty's ath5k working along these lines yet?

---

### Post by taavikko on 2009-01-19
Take a look at "lsmod |grep ath"
That show every modules that has ath on it.

Personally I would have put those blacklist lines in that default file, and not created an another for them.
/etc/modprobe.d/blacklist

Something like this
```
echo -e "blacklist ath_pci\nblacklist ath_hal" |sudo tee -a /etc/modprobe.d/blacklist
```

Ive used /etc/modules to load ath5k module.
No jockey for me :D

Only ath5k modules should be present.

If it fails to "wakeup chip"
that can be resolved by by shuttingd down computer.
Not an reboot, an shutdown, no power at all, for few seconds, then fire it up again.

---

### Post by Lucretius on 2009-01-19
tried both methods... neither worked for me i'm afraid..

this is on an acer aspire one

---

### Post by taavikko on 2009-01-19
> **Lucretius said:**
> tried both methods... neither worked for me i'm afraid..

this is on an acer aspire one

Without any output from commands, its kinda hard to tell whats wrong...

I have the same laptop (currently not running jaunty yet, fallback pc)

But the procedures shouldn't differ from intrepid, since same drivers.
Same thing was on intrepid alpha* ath5k module were present in kernel, but dropped due issues. And packaged along in "backports-modules" pkg.

so, what does say **lsmod |grep ath**
If you used jockey to install drivers, please remove them, to let ath5k driver work alone.

ath5k should be on kernel at the moment
quick check
```
cat /boot/config-`uname -r` |grep -i ath5k
```

which should return
[I]cat /boot/config-`uname -r` |grep -i ath5k
CONFIG_ATH5K=m
# CONFIG_ATH5K_DEBUG is not set
[/I]
where m= build in as module.

And finally, check dmesg what errors it comes up with.
```
dmesg |grep ath
```

If there's those older modules ath_hal and ath_pci running,
remove them with **sudo rmmod ath_pci** and so on.

---

### Post by Lucretius on 2009-01-20
sorry for the delayed response... this is my terminal output...

cat /boot/config-`uname -r` |grep -i ath5k returns

CONFIG_ATH5K=m
# CONFIG_ATH5K_DEBUG is not set

dmesg |grep ath returns

[    3.139991] device-mapper: multipath: version 1.0.5 loaded
[    3.139997] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.627440] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.627475] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   12.627584] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   14.706576] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)


I did not use jockey or any other 3rd party installer... the default ubuntu driver is loaded and claims to be working... however wireless claims to be "disabled" in network manager and any option to correct this is greyed out.

Perhaps a network manager issue and not a driver issue?

---

### Post by taavikko on 2009-01-21
I'll be tempted to point my finger towards NM.
what is th,e output of **nm-tool** 

Also you coukd test wicd as a last resort.
But since it isn't part of default install, that makes testing pointless IMO.

---

### Post by Lucretius on 2009-01-21
here is the output of nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:1E:68:A8:CF:EA

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         192.168.1.65
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k_pci
  State:             unavailable
  Default:           no
  HW Address:        00:22:69:07:44:3C

  Capabilities:
    Supported:       yes

  Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

---

### Post by hajk on 2009-01-21
Just installed Alpha-3 on my Aspire One 110Ab, tried both ath_pci and ath5k (separately, of course): ath_pci (etc) gave an error message in dmesg about not being able to attach to the hardware; ath5k worked, but showed slow speed and regular disconnects. So, I've followed the Ubuntu AspireOne wiki and downloaded/compiled/installed the latest Madwifi (ath_pci), and now all's well.

N.B. I always disable Network-Manager and configure the ath0 interface in /etc/network/interfaces:```

auto ath0
iface ath0 inet manual
    wpa-driver wext
    wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
iface default inet dhcp
```
while /etc/wpa_supplicant/wpa_supplicant.conf has contents like```

ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="MySSID"
        psk="MySecretPassPhrase"
}
network={
        ssid="HotSpotProvider"
        key_mgmt=NONE
}
```(this is set up by default to handle WPA/WPA2 Personal security). The "wpa-driver wext" line is needed in /etc/network/interfaces because wpa-supplicant may time out before it gets around to trying the wext driver.

May be the problems with ath_pci or ath5k will go away if Jaunty adopts the 2.6.29 kernel.

---

### Post by taavikko on 2009-01-21
What's the pci-id for your atheros nic's
```
lspci -vvnn |grep -i atheros
```

List of working ones:
```
168c:0207
168c:0007
168c:0011
168c:0012
168c:0013
a727:0013
10b7:0013
168c:0014
168c:0015
168c:0016
168c:0017
168c:0018
168c:0019
168c:001a
168c:001b
168c:001c 
```

---

### Post by Lucretius on 2009-01-21
lspci -vvnn |grep -i atheros returns

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

thank you for your time btw

---

### Post by taavikko on 2009-01-21
> **Lucretius said:**
> lspci -vvnn |grep -i atheros returns

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

thank you for your time btw

Yep, it should work, but something is missing...?

Do you have a hidden essid? and no neighbours with wlan?
Sure that ath5k module is loaded,
and ath_* disabled.

dmesg doesn't return any error messages "unable to wake up lan chip"

Some extra info 
[http://wireless.kernel.org/en/users/Drivers/ath5k](http://wireless.kernel.org/en/users/Drivers/ath5k)

---

### Post by Lucretius on 2009-01-21
absolutely everything is stock, I have only one neighbour with wlan and he uses it rarely.

dmesg returns....

[   11.907970] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.908041] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   11.908140] ath5k_pci 0000:03:00.0: registered as 'phy0'
.................
[   12.240891] phy0: Selected rate control algorithm 'pid'
.......
[   13.754230] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
................



[   20.081606] apm: BIOS not found.
[   22.719998] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.720091] Bluetooth: BNEP filters: protocol multicast
[   22.793020] Bridge firewalling registered
[   26.707096] [drm] Initialized drm 1.1.0 20060810
[   26.745389] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.745413] pci 0000:00:02.0: setting latency timer to 64
[   26.747034] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   27.183070] r8169: eth0: link down
[   27.183250] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.240432] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   86.744212] r8169: eth0: link up
[   86.744309] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   97.025219] eth0: no IPv6 routers present
[   99.625895] r8169: eth0: link down
[  101.351181] r8169: eth0: link up


I have remove a lot from the output that did not seem relevant

my ethernet did not work initially as my router was turned off, thats why it claims eth0: link down

---

### Post by hajk on 2009-01-22
Same version 168c:001c (rev 01). I have experimented a bit more with the ath5k driver: the "sudo iwconfig" command shows that the wlan0 driver is present (same output in demsg as for Lucretius). I have now replaced network-manager by wicd and this can connect to my WPA/WPA2 secured AP, although only after the second or third try. I'm sending this reply using that wireless connection. I'm keeping my fingers crossed, because I don't really want to use that old Madwifi stuff.

Edit: there is a little toggle switch just below the wireless LED on my Aspire One 110Ab, this switches the wireless card on/off, with last position remembered at reboot...

---

### Post by Lucretius on 2009-01-22
installed wicd and wireless is now working flawlessly...

definitely a network-manager bug.

thanks for the help :D

---

### Post by Limulus on 2009-01-23
My Aspire One also uses the "168c:001c (rev 01)" chip and sure enough, when I installed wicd (and rebooted), I was able to detect the wireless network (though I'm having difficulty connecting because of its hidden essid).  I should file a bug report on this if its not already been done (two actually; one for NM and the other for the driver).

---

### Post by Limulus on 2009-01-23
> **Limulus said:**
> I should file a bug report on this if its not already been done (two actually; one for NM and the other for the driver).

Ah, they seem to have been filed already:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/315056/](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/315056/)

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/320177](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/320177)

---

### Post by thor2002ro on 2009-01-23
try using this [kernel ]("http://ubuntuaone.com/content/slckb0ykuki-kernel-2628-v02-acer-aspire-oneundervolt")
works like a charm.... and even wifi led works...:popcorn:

---

### Post by Limulus on 2009-02-01
> **Limulus said:**
> Ah, they seem to have been filed already:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/315056/](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/315056/)

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/320177](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/320177)

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/323830](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/323830)

> **thor2002ro said:**
> try using this [kernel ]("http://ubuntuaone.com/content/slckb0ykuki-kernel-2628-v02-acer-aspire-oneundervolt")
works like a charm.... and even wifi led works...:popcorn:

Needs to be fixed in Ubuntu :)

[https://bugs.launchpad.net/ubuntu/+bug/284474](https://bugs.launchpad.net/ubuntu/+bug/284474)

---

### Post by Limulus on 2009-02-14
> **Limulus said:**
> [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/320177](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/320177)

Interesting!  I just found Bug #319825:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319825](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319825)

and that is the REAL bug.  Simply run:

```
sudo rmmod acer_wmi
```

And suddenly wireless is enabled!

---

### Post by Limulus on 2009-02-14
Blacklisting acer_wmi has a more permanent effect of making it work, BTW.  Huzzah! :-)

---

### Post by Limulus on 2009-02-14
> **thor2002ro said:**
> try using this [kernel ]("http://ubuntuaone.com/content/slckb0ykuki-kernel-2628-v02-acer-aspire-oneundervolt")
works like a charm.... and even wifi led works...:popcorn:

LOL!  I just noticed this morning, after blacklisting acer_wmi, when I send/receive using WiFi, the front LED blinks! :-)  Looks like another bug bites the dust ;)

---

