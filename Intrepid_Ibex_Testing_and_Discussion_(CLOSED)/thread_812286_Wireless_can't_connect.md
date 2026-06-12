---
title: "Wireless can't connect"
date: 2008-05-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-05-29
Finally, after over a month of error messages I've finally managed to dist upgrade! And guess what, intrepid is broken. :lolflag:

I've seen this one before, I think it was on the hardy alpha tests. My wireless can see everyone's networks but if I try to connect it asks for the key, then tries to connect for ages before eventually asking for the key again, and again, and again.

Other than that everything seems fine, which is impressive. So please tell me what you need to know to help me figure this niggle out.

---

### Post by caryb on 2008-05-29
Macroshaft, do you have wep enabled on your access point/router? if so I had to add the settings in the /etc/network/interfaces file for my AP

eg of my interfaces file

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless_mode managed
wireless_enc on
wireless-essid put_in_ssid_name_here
wireless-key put_key_passphrase_in_here

auto wlan0


Cary

---

### Post by macroshaft on 2008-05-29
I was connected to a WPA2 connection during the dist-upgrade and it disconnected towards the end of the install, now it cannot connect to WEP, WPA, anything. It just keeps asking for the key.

I tried that fix in the previous reply and now my wireless is 'locked' onto my WEP connection although it isn't connected wireless has vanished off my toolbar and in the network settings shows it is purely set to connect to one network. Essentially my connection has been crippled!

---

### Post by caryb on 2008-05-29
I have tried all means of GUI apps (Kwireless, WICD, networkmangler etc) but none have worked for me so I just set mine up this way as default as I'm over Linux wireless apps that either don't work or ask for a password every logon etc.


Cary

---

### Post by macroshaft on 2008-05-29
I use several networks and since intrepid is supposed to be about pervasive net access it seems a shame to force it to lock down.

---

### Post by macroshaft on 2008-05-30
It will be interesting to see what you guys make of this, today the wireless just started working but signal strengths appear reduced and it keeps repetedly disconnecting and requires the key to be re-entered every time.

---

### Post by ronacc on 2008-05-30
I don't know if this will have anything to do with your problem, this morning on bootup intrepid nm-applet showed just cycling and looking for the network and I'm wired . I could not connect to my router , killing nm-applet allowed the connection to establish .

---

### Post by cariboo on 2008-05-30
After an update yesterday network manager set eth0 to roaming mode, and even though it indicated that it was not connected to the router running ifconfig showed it was connected and that every thing was OK. I just set it for dhcp and everything was good to go.

Jim

---

### Post by plun on 2008-05-30
This sticky thread is great for solving wireless trouble

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

The NM is just junk for a lot of wireless circuits.

I have a D-Link DWL-G122......  (probably proprietary   :)  )

---

