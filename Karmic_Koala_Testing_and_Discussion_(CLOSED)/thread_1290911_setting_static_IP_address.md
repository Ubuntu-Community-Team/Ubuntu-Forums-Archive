---
title: "setting static IP address"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jynyl on 2009-10-14
Is it possible to set a static IP address using the NetworkManager?
The KubuntuGuide seems to suggest you can only set a static IP address by editing config files.
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Set_a_static_IP_address]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Set_a_static_IP_address")

---

### Post by Bucky Ball on 2009-10-14
Yes. 

Configuration='Static IP Address'
IP Address=the static IP you want for your machine (hit enter and 'Subnet Mask' will be filled automatically)
Gateway=IP of your router

You need to make sure your router is NOT acting as a DHCP server and serving you an IP address.

---

### Post by donniezazen on 2009-10-14
> **jynyl said:**
> Is it possible to set a static IP address using the NetworkManager?
The KubuntuGuide seems to suggest you can only set a static IP address by editing config files.
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Set_a_static_IP_address]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Set_a_static_IP_address")

I have read many sites about differences between Static and Dynamic IPs. Yet i don't get the advantage of static IP over Dynamic IP. If i am true the static is good only if you play games, torrents, FTP transfer, etc and you want to have fix IP. Is that the only profit of Static IP?

---

### Post by lisati on 2009-10-14
My preference is to have my main router assign specific addresses to specific machines (i.e. the laptop and two desktops normally hooked up) and let it dish out whatever it wants to anyone who somehow manages to correctly guess the WPA key. 

In other words, I let the routers deal with IP address assignment, not the computers connected to it.

---

### Post by jynyl on 2009-10-16
A static IP address is handy if you want to connect to the box over your LAN.  I backup data from my laptop to my desktop machine, using a short rsync bash script on the laptop.  This needs to know the IP address of the desktop, which would be awkward if it changes dynamically.

There are probably other ways to do this, but the above method is simple and works, it just needs a static IP on the desktop.

Peter

---

### Post by Bucky Ball on 2009-10-16
With my router, a D-Link 704P, I can have one or the other, not both. I found the best way to do it was setting the static IPs on the local machine and setting static and DHCP to 'disabled' in the router.. 

You might be able to cover both but to assign IPs from the router you will need your machine MAC address which, if you are currently running with router as DHCP server, will be listed there. Switch all machines on and note all MAC addresses. Unplug everything and leave one computer plugged into the router.

Boot up and get into the router admin window. Input the MAC address and IP you want for each machine on the LAN and plug everything in and you should be good. Not sure how you would setup System->Admin->Network to get this running. If you put the SAME static IP in the local machine you will have the local machine trying to stuff and IP into the router and the router trying to stuff one back. 

This method DID NOT work for me with my router. I had to go the first route I outlined. You are going to need to figure out what your router likes. Good luck. :)

---

### Post by stefanlasiewski on 2009-10-27
It's fine to use a static IP address on your workstation if your router uses DHCP. If your workstation has a static IP address, it won't use DHCP.

However, it's a good idea to use a Static IP address which is outside the range of the IP addresses assigned by the DHCP server. My router assigns DHCP addresses in a range like 192.168.1.1-32 . So, if I want a static IP address I simply use something like 192.168.1.100.

Static IP addresses are handy if you want a computer to always remain on the same IP address. I do this for one machine at home so that I can SSH to the machine from outside my house, but not for my other machines. A static IP helps to simplify things like firewall rules, forwarding rules, etc.

Most people do not need static IPs at home. DHCP is much simpler for most people, since it is supported by most home routers out of the box.

-= Stefan

---

