---
title: "Belkin 54g Wi-Fi woes"
date: 2005-05-16
forum: Installation &amp; Upgrades
---

### Post by oilz on 2005-05-16
Hi,

I followed this to the letter:
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

but still, can't connect to my WLAN.

I've noticed that my notebook (running Ubuntu) picks up the Wi-Fi network name (essid) in System/Networking.
But I can't ping any of the local machines on my WLAN, or anything else.

I had to manually set the RadioState to 0, but still no dice.

Any tips are greatly appreciated.

Thanks

---

### Post by spd106 on 2005-05-16
Hi, have you tried doing
```
$sudo dhclient wlan0
```

This requires that you use dhcp to receive an ip address. 

If not then edit /etc/network/interfaces file by putting in the static address, subnet mask,... Look to the man pages for examples.

Hope this helps

---

### Post by oilz on 2005-05-17
dhclient - no dice. And for some reason, it's using a netmask of 255.255.255.255

Also, I hardcoded a local static ip address and subnet mask in the interface file.
Taking down and bringing up wlan0, then pinging another machine on the WLAN still gives me the same "Network can't be reached" error.

---

### Post by spd106 on 2005-05-17
The wifi gui config tools aren't always reliable at the moment, so if they don't work stick with the command line.
Do you see your ap with
```
$sudo iwlist wlan0 scan
```

What kind of network adapter is it?
The usb ones don't have much support yet. Even cardbus can be hit and miss.
```
$lspci
```

Check it's installed correctly with
```
$sudo ndiswrapper -l
```

---

### Post by oilz on 2005-05-18
Hi spd106,

Thanks heaps for your help.

I was about to give up, but then I tried the 'iwlist wlan0 scan' found the broadcast (SSID) being picked up by my notebook.

From there I realised that there is a wireless connection present, and something is stopping the connection.
I disabled security on the router and it worked. I know, I should have disabled security from day 1 to test connectivity, but I thought that wouldn't have been the problem.

I'm now using 128-bit WEP.

Is it possible to use WPA security in Ubuntu?
As the Ubuntu System/Administrator/Networking application only specifies to use a WEP.

---

