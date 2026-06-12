---
title: "Network disappears after upgrading to 12.04"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by netsurfau on 2012-07-26
I just upgraded my Primary Desktop PC from 10.04 to 12.04.

Everything seemed to work fine, until final reboot where all network connectivity disappeared.  To "add insult to injury" when I try to diagnose what's wrong, when clicking on Network Settings I get the following error msg: "The System network services are not compatible with this version."

**WTF???** This is a joke right?  How the hell can the network services be incompatible? :mad:

---

### Post by NikTh on 2012-07-26
Hi , 
open a terminal (ctrl+alt+t) and give the results of 
```
cat /etc/network/interfaces 
cat /etc/NetworkManager/NetworkManager.conf
``` 

Thanks

---

### Post by netsurfau on 2012-07-26
@NikTh:  As requested output below.


luke@NetSurf:~$ cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.0.27
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 210.15.254.240 210.15.254.241
	dns-search netspace.net.au

luke@NetSurf:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

The DNS nameservers & DNS-serch parameters are the correct ones, as are the IP address settings from my ADSL Modem/Router.

---

### Post by netsurfau on 2012-07-26
During boot the msg "Waiting for Network Configuration...." appears,
followed by another msg similar to "Waiting 60 seconds more for Network Configuration".  
A third msg then appears stating that system booting with incomplete Network Configuration.

Do these messages help?

---

### Post by NikTh on 2012-07-26
Hi , 
did you add all these entries ? 
> ```
# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.0.27
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 210.15.254.240 210.15.254.241
	dns-search netspace.net.au
``` 

can you delete them ? 

if you can , then ```
gksudo gedit /etc/network/interfaces
``` 
and leave only this inside 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
``` delete all other. 

save the file and reboot. 

You must know something else .. package resolv.conf has changed behavior on Ubuntu 12.04. 
So if you want to add custom name-servers you must follow this guide --> [http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf](http://askubuntu.com/questions/130452/how-do-i-add-a-dns-server-via-resolv-conf)
Thanks

---

### Post by netsurfau on 2012-07-26
Thanks Nik,
That fixed the issue.  Not going to worry about customising DNS server addresses.

---

### Post by gnorb on 2012-07-27
Hi,
I had trouble with the same issue after upgrading 10.04 to 12.04.
Thanks NikTh, This fixed the issue for me as well!

---

### Post by acoluthus on 2012-11-03
I've got the same situation; I ran the first info-request line in Terminal and got the same reply as above, 
but the 2nd :"cat /etc/NetworkManager/NetworkManager.conf"
gave the results:
----------------------------
[main]
pluginsifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
----------------------------

I read another thread that asked to run:
sudo ifconfig auto eth0 up
results:
eth0: Unknown host
____________________________
I'm running from a CPU to a router, other users are working fine; router wireless is working fine.
I went into the 'regular' interface, System Settings, Network, and tried to change the Proxy from Automatic to None; retried the Terminal codes above with no further progress.
-I don't know the router "address" info to fill in manually; typically it's been "plug n play" .. router is: linksys wrt54GL
and we do use a password as we have wireless enabled.(I think that's just on the wireless, but in case Wired needs it/fyi)
____________
Help?

---

### Post by Tinkerer22 on 2013-05-18
Hi,

I also had the same networking issue after upgrading my  laptop from 10.04 to 12.04. It turns out that I had to remove all of the  extra settings still saved in /etc/network/interfaces, just as NikTh  posted. Now my "interfaces" file looks like this: 
```
auto lo
iface lo inet loopback

```

After saving the file "interfaces" and  rebooting, the networking services are finally working!

Thanks NikTh and netsurfau.:smile:

---

