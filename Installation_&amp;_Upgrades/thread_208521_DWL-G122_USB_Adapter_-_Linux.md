---
title: "DWL-G122 USB Adapter - Linux?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by AMCDeathKnight on 2006-07-03
Does the DWL-G122 USB Wireless dongle have support for Ubuntu Linux? If so how do I go about installing it. Im new to the wireless thing and hope that you could help me, the community is really letting me down with problems I have had and not helping so I hope it picks up here. Either this or im going to try and find away to put Windows back on.

---

### Post by jISh on 2006-07-03
Here's the little note I wrote for myself so I'd always remember how to set this thing up for myself :) I'll comment through the steps for you though. 

Install ndiswrapper from livecd
*newer version is in the repos, if you have any internet access on this machine. both versions work fine. To install from CD, add your CD as a repository in Synaptic, then search for ndiswrapper.*
Copy drivers from official cd to desktop
*from the driver CD that came with your adapter*
go to terminal
*applications -> accessories -> terminal*
*type the following commands, line by line*
cd Desktop
sudo ndiswrapper -i "PRISMA02.inf"
sudo modprobe ndiswrapper
sudo modprobe -m

Restart your machine.
go to system -> admin -> network, configure.

Good luck.

---

### Post by AMCDeathKnight on 2006-07-03
modprobe: invalid option

---

### Post by AMCDeathKnight on 2006-07-03
How will I be able to see and connect to wireless networks? Like on Windows you just doube click it and enter.


Also on a side note, how do I change into a different workgroup?

---

### Post by jISh on 2006-07-03
Sorry, I made a mistake in that.
The last command is
sudo ndiswrapper -m
Also , you need to push alt+f2, write

gksudo gedit /etc/network/interfaces

and insert the following

```

iface wlan0 inet static
address x.x.x.x
netmask 255.255.255.0
gateway x.x.x.x
wireless-essid <YOUR NETWORK NAME HERE>

auto wlan0

```

Change the x's to your IP info. wireless-essid to your network name.

You can do further configuration from network settings on your machine, you will have a wlan0 option.

---

### Post by AMCDeathKnight on 2006-07-03
Thanks, I want to do alot of swappable wired network to wireless as I want to wardrive and use Wireless networks on the go? How might I go about doing this?

---

### Post by jISh on 2006-07-03
Err, sorry I only use the one network so I'm not entirely sure. I believe there are wifi managers available, maybe search through the forums for one. Let me know if you get the adapter working, though.

---

### Post by AMCDeathKnight on 2006-07-03
I believe it is working, it seems to have eth1 which is Wireless active, yet I dont know how to connect to any networks etc

Wireless manager is something I need.

---

### Post by AMCDeathKnight on 2006-07-03
Any suggestions on wireless managers etc?

---

### Post by jISh on 2006-07-03
eth1 isn't wireless. wlan0 is wireless. The alias you put in the interfaces file should enable a wlan0 to show up in your Network settings. The SSID part of the alias is the network you will connect to.

---

### Post by AMCDeathKnight on 2006-07-04
So, I have to change that whenever I join a wireless network? I am confused. Is there no GUI program that shows me what ones there is, so I can connect to it? Like Windows.

---

### Post by jISh on 2006-07-04
Perhaps this will help you further:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

At the bottom, there is a list of GUIs.

---

### Post by AMCDeathKnight on 2006-07-06
Thanks

---

### Post by AMCDeathKnight on 2006-07-06
[QUOTE=jISh]Sorry, I made a mistake in that.
The last command is
sudo ndiswrapper -m
Also , you need to push alt+f2, write

gksudo gedit /etc/network/interfaces

and insert the following

```

iface wlan0 inet static
address x.x.x.x
netmask 255.255.255.0
gateway x.x.x.x
wireless-essid <YOUR NETWORK NAME HERE>

auto wlan0

```

Change the x's to your IP info. wireless-essid to your network name.

You can do further configuration from network settings on your machine, you will have a wlan0 option.[/QUOTE]

Im a bit confused about this part, my IP changes all the time where ever I am out, I want a Dynamic one, so what do I put? ALso I dont get what Network name is either.

---

### Post by jISh on 2006-07-07
That's easy. Just change the "iface wlan0 static" line to:

iface wlan0 inet dhcp

And remove the IP address line.

Put your network name as your router's name. The Wifi Wiki has a script to let you pick networks.

---

### Post by AMCDeathKnight on 2006-07-07
What router? I have none.

---

### Post by jISh on 2006-07-07
How do you have a wireless network without a router??

---

### Post by AMCDeathKnight on 2006-07-07
Well, I want to connect to several wireless networks not just one.

---

