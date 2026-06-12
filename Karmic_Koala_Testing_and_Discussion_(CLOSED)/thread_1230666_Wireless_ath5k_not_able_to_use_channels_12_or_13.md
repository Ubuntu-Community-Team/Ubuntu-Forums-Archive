---
title: "Wireless ath5k not able to use channels 12 or 13"
date: 2009-08-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joffe on 2009-08-03
I have been staying at my friend's since a couple of weeks and have not been able to connect to his wireless router. This is what nm-tool and dmesg reported:

```
- Device: ath0 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:14:6C:3C:BE:B3

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```

```
[ 1039.900063] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 1039.900118] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[ 1039.900350] ath5k 0000:03:00.0: enabling device (0000 -> 0002)
[ 1039.900365] ath5k 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[ 1039.900446] ath5k 0000:03:00.0: registered as 'phy2'
[ 1040.078305] ath: EEPROM regdomain: 0x0
[ 1040.078311] ath: EEPROM indicates default country code should be used
[ 1040.078313] ath: doing EEPROM country->regdmn map search
[ 1040.078318] ath: country maps to regdmn code: 0x3a
[ 1040.078321] ath: Country alpha2 being used: US
[ 1040.078324] ath: Regpair used: 0x3a
[ 1040.082231] phy2: Selected rate control algorithm 'minstrel'
[ 1040.084114] ath5k phy2: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[ 1040.177315] udev: renamed network interface wlan0 to ath0
[ 1044.304759] ADDRCONF(NETDEV_UP): ath0: link is not ready
```

Sometimes some random SSID showed up but often the list of networks was empty. Now I noticed that I couldn't get Windows 7 to connect using wireless either, but my iPod Touch had no problems connecting.

Luckily for me the NETGEAR router was using factory default settings so I was able to access the settings When I changed the  channel from 13 to 12, Windows 7 was suddenly able to connect and when I changed it to 11 Karmic also wanted to play.

I remember having seen this in the release notes for Jaunty:
[[COLOR="RoyalBlue"]Setting wireless regulatory domain via module option no longer supported[/COLOR]]("http://www.ubuntu.com/getubuntu/releasenotes/904#Setting%20wireless%20regulatory%20domain%20via%20module%20option%20no%20longer%20supported")

A quick Google search reveals that channel 12 and 13 are not supported in the US and this dmesg line kind of explains why it is not working:
```
[ 1040.078321] ath: Country alpha2 being used: US
```

I have been trying the iw reg set command as described here:
[[COLOR="RoyalBlue"]Bug #365049[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/365049")

but whatever ISO 3166-1 alpha-2 country code I choose the iw get command always returns the same:
```
xxx@yyy:~$ iw reg set SV
xxx@yyy:~$ iw reg get
country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
```


even though dmesg shows this:
```
[ 3151.050704] cfg80211: Calling CRDA for country: EU
```

Does anybody know how this works and how to force the CRDA setting to other than US? The easy way out is of course to stay with channel 11 but I think my friend chose 13 to avoid interference with his wireless hifi system.

---

### Post by wayne_cat on 2009-08-03
You live in El Salvador (ISO 3166-2 country codes: SV) and you want to
use the frequency settings for Europe? Or do you live in Sweden ... Code: **SE**

```
root@macbook:~# iw reg set SE
root@macbook:~# iw reg get
country SE:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
root@macbook:~# 

```

---

### Post by joffe on 2009-08-03
True, I meant to use SE, have a bad habit of mixing it with the language code :oops:
The problem with setting this domain remains, and I wonder how it is supposed to pick up the right setting without user intervention. I'm ok with writing a script that does this but other users that fiddles with wireless channels might run into the same problem.

Now I got the wanted output in dmesg but the wireless interface still does not pick up any networks so there must be a bug/misconfiguration somewhere...
```

[  762.387197] cfg80211: Calling CRDA for country: SE
[  762.391073] cfg80211: Regulatory domain changed to country: SE
[  762.391080] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  762.391085] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  762.391089] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  762.391093] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  762.391096] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 1302.596328] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1333.048083] ath0: no probe response from AP 00:0f:b5:5e:05:82 - disassociating
[ 1407.336210] ADDRCONF(NETDEV_UP): ath0: link is not ready
```

---

### Post by joffe on 2009-08-07
Sorry for bumping, I haven't been able to find any satisfactory information on this issue with my NETGEAR WG511T pcmcia card.

I have set the country region:
```
xxx@yyy:~$ sudo iw reg set SE
xxx@yyy:~$ iw reg get
country SE:
	[COLOR="Red"](2402 - 2482 @ 40), (N/A, 20)[/COLOR]
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
```
but it still doesn't enable the extra channels:
```
xxx@yyy:~$ iw list
Wiphy phy0
	Band 1:
		Frequencies:
			* 2412 MHz [1] (20.0 dBm)
			* 2417 MHz [2] (20.0 dBm)
			* 2422 MHz [3] (20.0 dBm)
			* 2427 MHz [4] (20.0 dBm)
			* 2432 MHz [5] (20.0 dBm)
			* 2437 MHz [6] (20.0 dBm)
			* 2442 MHz [7] (20.0 dBm)
			* 2447 MHz [8] (20.0 dBm)
			* 2452 MHz [9] (20.0 dBm)
			* 2457 MHz [10] (20.0 dBm)
			* 2462 MHz [11] (20.0 dBm)
			[COLOR="Red"]* 2467 MHz [12] (disabled)
			* 2472 MHz [13] (disabled)
			* 2484 MHz [14] (disabled)[/COLOR]
		Bitrates:
			* 1.0 Mbps
			* 2.0 Mbps (short preamble supported)
			* 5.5 Mbps (short preamble supported)
			* 11.0 Mbps (short preamble supported)
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
	max # scan SSIDs: 4
	Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * monitor
		 * mesh point
```


From linuxwireless.org I have found out that there is a new regulatory infrastructure in place from 2.6.28 onward. There is a very interesting GSoC project related to getting this to work by using GeoClue together with the user timezone for regulatory compliance. Does anybody know how, and if, this is going to work in Karmic?

---

### Post by bluesterror on 2009-08-26
The way it works is that ath5k has a regulatory domain stored in its EEPROM which contains all of the channels with which it has been calibrated, for the market in which it is sold.  Because a card sold in US may not be calibrated for operation abroad, cfg80211 limits regulatory conformance to the intersection of what the card says, what the user says, and any information from 802.11d.  Therefore you probably will not be able to use channels 12 or 13, at least with the standard regulatory DB.

---

