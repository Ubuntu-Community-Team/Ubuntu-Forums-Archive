---
title: "Upgraded to jammy and now I can't access my router"
date: 2022-09-02
forum: Installation &amp; Upgrades
---

### Post by Evil Wayz on 2022-09-02
This is baffling and annoying.  I upgraded from 21.10 to 22.04 successfully no errors.  I have internet access obviously.  But everytime I try to access my router via the web interface it times out.  I've tried 3 different browsers.  I can access the web interface from my phone and my laptop, so there's nothing wrong with the router.

I have the correct address:

wolf@wolf-Desktop:~$ ip route
default via 192.168.0.1 dev eno1 proto dhcp metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.0.0/24 dev eno1 proto kernel scope link src 192.168.0.12 metric 100 

wolf@wolf-Desktop:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         192.168.0.1     0.0.0.0         UG        0 0          0 eno1
link-local      0.0.0.0         255.255.0.0     U         0 0          0 eno1
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eno1

What am I missing?

---

### Post by QIII on 2022-09-02
What happens if you ping the router?

---

### Post by Evil Wayz on 2022-09-02
Ok this seems to be the issue:

ping -c 2 $(netstat -r | awk '/default/ {print $2}')
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1014ms
ping -c 2 $(netstat -r | awk '/default/ {print $2}')
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1014ms

---

### Post by Evil Wayz on 2022-09-02
Just discovered I can't access any of the shares in my local network anymore either.

Messing with my samba configuration now to see why....

---

### Post by QIII on 2022-09-02
Are you using a wireless connection?  When reinstalling, did you use that wireless connection?  Can you connect with a cable?

I'm going to have to go tend to the livestock for a couple of hours, so hopefully someone can step in.

---

### Post by Evil Wayz on 2022-09-02
> **QIII said:**
> Are you using a wireless connection?  When reinstalling, did you use that wireless connection?  Can you connect with a cable?

I'm going to have to go tend to the livestock for a couple of hours, so hopefully someone can step in.

Noooooope.  This is my desktop, connected to the router via ethernet. It has internet access, and now that i have edited Samba, can see the network.

But it won't access the shares nor can I get the router to respond.

I can access the router via my laptop and phone so the wireless works fine.

---

