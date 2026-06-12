---
title: "Enable wifi and wifi switch"
date: 2016-01-31
forum: Installation &amp; Upgrades
---

### Post by jerry51 on 2016-01-31
Just installed Ubuntu on a Dell Vostro 1520 laptop.   While the Ethernet connection is working fine, the Vostro also has wireless wifi and bluetooth capabilities, at least it did with the previous Win XP OS.  i would like to enable these functions in Ubuntu.  How is this done, the wifi switch and bluetooth function key are not functioning at all with Ubuntu.

---

### Post by grahammechanical on 2016-01-31
> How is this done, the wifi switch and bluetooth function key are not functioning at all with Ubuntu.

They don't work. That is a function set up by the manufacturer and Microsoft but not with Linux.Do you still have XP installed? If WiFi is switched off in XP it will be switched off in Ubuntu. If WiFi is switched off in the BIOS it will be switched off in Ubuntu. If WiFI is not switched on with the function keys before Ubuntu is loaded then Ubuntu might not detect a working wireless adapter.

With an ethernet connection you should see a Network Manager indicator icon in the top panel. It will be 2 arrows going in opposite directions and that will indicate an active connection to the router. Click on the network manager icon and make sure the Enable Networking is ticked. Do you also see Enable WiFi? That will indicate that Ubuntu has detected a working wireless adapter. Is Enable WiFi ticked?

If Enable WiFi is ticked you should see a list of available wireless access points. Select your wireless access point and authenticate the connection with the wireless passphrase or wireless key or WPA-PSK key, whatever it is called by the manufacturer of the router. Not your Ubuntu user password. And that is it. Done.

It may be that you need to install a wireless driver. Go to System Settings>Software & Updates>Additional Drivers tab. You need to be connected to the internet and allow time for the utility to find the drivers. You may get offered a proprietary WiFi driver for installation.

By the way what version of Ubuntu are you using? Knowing that might help us give more precise directions. Also System Settings has a utility for Bluetooth. I do not have it myself so I cannot help you there. But the Bluetooth adapters will have to be powered up to be detected.

Regards.

---

### Post by jerry51 on 2016-02-02
XP is not installed, the hard disk was formatted and Ubuntu 14.04 LTS was installed from the cd drive.  The additional drivers tab did detect a Broadcom Wireless 1397 LAN Mini-card and downloaded a driver from the manufacturer.  After the install, the Network Manager detected my wi-fi network and asked for the password.  It appears to be working fine now.  Thanks.

---

