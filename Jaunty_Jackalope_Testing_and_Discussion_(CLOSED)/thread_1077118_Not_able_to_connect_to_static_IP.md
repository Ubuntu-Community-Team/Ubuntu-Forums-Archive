---
title: "Not able to connect to static IP"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by harsh1kumar on 2009-02-22
I have installed Kubuntu 9.04 alpha 4. I am not able to connect to network using static ip. I created a new connection where I filled in the IP address, subnet mask, gateway and DNS. But when I save the settings, it shows me that it was never connected. When I check the setting again, the subnet mask is 0 instead of 255.255.252.0 that I entered. When I try to connect to the connection, it says "not able to connect to New Connection".

I tried to enter the setting manually in 
/etc/network/interfaces 
and 
/etc/resolv.conf

but that doesn't helped. Please help.

---

### Post by E_K on 2009-02-22
is another box using that ip, you shouldnt use address from the dhcp pool,

/etc/init.d/networking restart

is also another idea...

what does ifconfig show

---

### Post by harsh1kumar on 2009-02-22
I removed the connection from network manager, entered settings manually in /etc/network/interfaces
and
/etc/resolv.conf then restarted to get the things to works. Thanks.

---

### Post by E_K on 2009-02-22
no worries glad its working,

its a good idea into getting into the habbit of restarting anything you just edited the config off.. if in doubt reboot ;) but that is "never" needed hehe just restart/reload the right things.

Trust me it will prevent those moments of WTF WHY WHY WHY isn't it working ;)

---

### Post by harsh1kumar on 2009-02-22
I will keep that in mind. Thanks.:p How do I mark this as solved??

---

### Post by E_K on 2009-02-22
dont know never done it :P edit thread title? to [solved] blah

---

