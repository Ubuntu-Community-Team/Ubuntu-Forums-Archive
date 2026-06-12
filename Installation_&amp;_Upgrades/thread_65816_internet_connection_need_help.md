---
title: "internet connection need help"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by opendevlite on 2005-09-15
This are my specs of my PC:
Celeron 1.7Ghz
Asus P4S333 Motherboard
10GB harddisk
256DDR PC333

I'm having problems on my 2 Network Cards:
1 - connected to a modem atenna for wireless connection
1 - connected to a CNet 8-Port Switch 

Both Network cards are CNETPro 10/100Mbps... something

I have sucessfully installed Ubuntu 5.04 Hoary OS, but i cannot connect to the internet, can someone help me connect this PC to the Internet, and it would be great if you could make it step-by-step.

I'm not currently on my PC right now and im at an internet cafe, posting this help post, because i cant connect to the internet on my PC at home.

Thanks in advance.

---

### Post by Richard Rowlands on 2005-09-15
Hi there,

It's likely that your network cards are known to Ubuntu, try typing "ifconfig" at a terminal prompt.  You should see a list of all active adapters on your system.  Could you confirm whether or not the adapters are listed in the output of this command?

If the adapters are listed then it is likely that you just need to configure them correctly in order to connect to the internet.  You can do this by editing the "/etc/network/interfaces" file.  For information on this file type "man interfaces".

For example, if you have a network card eth0 and you want to automatically bring it up on boot using a static IP address 192.168.1.1, you would enter the following in you /etc/network/interfaces file.

auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0

If, on the other hand, you want to automatically bring it up on boot using a dynamic IP address assigned by a DHCP server (which your wireless access point or router might well have) you'd enter the following in the /etc/network/interfaces file.

auto eth0
iface eth0 inet dhcp

In both cases above, substitute "eth0" with the name of the network interface you're configuring (the name you saw on the left of the output generated when you typed "ifconfig").

After you have made these changes, reboot and hopefully you will be able to access the internet.

Good luck!

Regards, Richard.

---

