---
title: "Install Ubuntu On Multiple (Identical) Machines?"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by csharpplus on 2010-09-26
Hi All,
 
I am an Ubuntu newbie, and would greatly appreciate your help with the following:
 
I would like to set up Ubuntu on 20 identical laptops (IBM Thinkpad T60). What is the best / fastest way to do so?
 
Thanks,
cSharp.
 
 
P.S. all laptops are with the exact same hardware configuration, and empty hard drives (no OS is installed).

---

### Post by mörgæs on 2010-09-26
I have not tried myself, but I guess Clonezilla will do the job:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by csharpplus on 2010-09-26
Thank you very much for your help. I appreciate it.

---

### Post by mörgæs on 2010-09-26
You are welcome. Liberating 20 machines from Windows in one go is an act worth helping :-)

---

### Post by csharpplus on 2010-09-26
Thanks for your help.
 
By the way, can you help with some clues on how to connect all these machines in a network, so that I can (say) SSH into machine Y from machine X?  is it complicated?
 
Thanks in advance!

---

### Post by amauk on 2010-09-26
Just install openssh-server on all machines
then you can SSH in with
ssh user@ip_address

---

### Post by csharpplus on 2010-09-26
> **amauk said:**
> Just install openssh-server on all machines
then you can SSH in with
ssh user@ip_address
 
Thank you, amauk, for your reply.
 
So I just install 'openssh-server' on all machines, connect them to a hub and that's it?
Is there any other configuration / anything that I need to take care of?
 
Also, instead of using the IP address of every machine, is there a way to establish a constant 'name' for every machine that will be part of the network, so that would be able to access every machine by its 'name' (something like 'SSH Machine1', 'SSH Machine2', 'SSH MachineN'...)?

---

### Post by amauk on 2010-09-26
> **csharpplus said:**
> Also, instead of using the IP address of every machine, is there a way to establish a constant 'name' for every machine that will be part of the network
You'll need a DNS server for this
DNS translates a name to an IP address

If the machines are allocated IPs from a router using DHCP, then most decent routers also have a DNS server built-in as well
So yes, you will be able to reference machines by their machine name

---

### Post by csharpplus on 2010-09-26
> **amauk said:**
> You'll need a DNS server for this
DNS translates a name to an IP address
 
If the machines are allocated IPs from a router using DHCP, then most decent routers also have a DNS server built-in as well
So yes, you will be able to reference machines by their machine name
 
Thanks amauk. I appreciate your help!
 
Can you recommend on a decent switch (say, 8-port) that is compatible with Ubuntu and would do the work (and will allow me to 'name' each machine)?
 
I do not need to share internet connection between the machines, as the goal is solely to be able to 'SSH' from one machine to another and to transfer files between the machines.

---

### Post by amauk on 2010-09-26
switches cannot do DHCP (dynamically assigning IP addresses) or DNS (domain to IP translation), as they are not designed for that

You'll need a router for such high level functionality

Switches are quite low level devices, and only map IP addresses to physical MAC addresses

A computer can work as a router, if you don't have a separate router for internet access.
If you have a central server, then you can install a DHCP server and DNS server on it, and the central server will hand out IP addresses to clients and be able to translate machine names to IP addresses for all clients

---

### Post by csharpplus on 2010-09-26
thanks amauk for your help!
 
The truth of the matter is, I don't have to have the 'naming' done. I just want the machines to have a 'constant' identification from the moment the system is set up.
 
so if I have 5 computers, I prefer that each of the 5 will have a unique identification so that when I do 'SSH x', 'x' would always refer to the same computer. and when I do 'SSH y', 'y' would always refer to the same computer  (different than 'x').
 
possible to do so with a switch? 
 
if not, what is the easiest, most simple way to achieve that? (I can assign one of the laptops to be a 'server', if this is a must). thank you!

---

### Post by amauk on 2010-09-26
If you set each machine up with a static IP address, then it's guaranteed not to change
you can then be assured that
ssh user@192.168.1.10 will always ssh into the same machine

however, DHCP is more convenient (no need to manually configure the clients) and DNS eliminates the need to enter IP addresses for commands, and allows for nice human-readable names
ssh bob@bob-laptop

I'd have DHCP & DNS as an end goal and use static IPs as a quick, temporary solution

Are you sure you don't have a router already?
(for internet connection?)

As a side-note,
You can also manually set names to correspond to IP addresses by editing the /etc/hosts file on each client
This emulates a DNS server without actually having one - but it's a hack.
Any changes will mean updating /etc/hosts on all the clients - it's cumbersome and prone to error (mismatching info between clients)

---

### Post by csharpplus on 2010-09-27
amauk,
 
thanks again for your detailed reply. am fortunate to learn from you.
 
yes, of course I have a router (for internet connection). yet, the router I have has only 4-ports, while I would need about 20 ports to connect the new machines (although, I do not need to connect them to the internet -- just want them to be able to 'ssh' one into the other etc).
 
since all machines will be used for the same purpose, I do think that you solution of:
 
>  
You can also manually set names to correspond to IP addresses by editing the /etc/hosts file on each client
This emulates a DNS server without actually having one - but it's a hack.
Any changes will mean updating /etc/hosts on all the clients - it's cumbersome and prone to error (mismatching info between clients) 

 
can work for me. especially because all machines will be numbered (1, 2, 3, ...., 20).
Should I then set each machine with a static IP address, and then edit these files?
can you explain more how to do the above?  thank you.

---

### Post by amauk on 2010-09-27
You using wired ethernet, rather than wireless?

Machines don't have to be directly connected to a router
you can daisy-chain a switch off of the router
The fact you have a router means you can most likely to DHCP

```
/---------\
|  ROUTER |
\---------/
    |
    |
/---------\
|  SWITCH |
\---------/
     | | |
     | | |      /----------\
     | | \------| LAPTOP 1 |
     | |        \----------/
     | |
     | |        /----------\
     | \--------| LAPTOP 2 |
     |          \----------/
     |
     |          /----------\
     \----------| LAPTOP 3 |
                \----------/
```


However, if you want static IPs, see here
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/)

---

### Post by csharpplus on 2010-09-27
amauk,
 
Thanks for all of your help.
 
Yes, I will be using  wired ethernet (faster speed than wireless).
 
I have a question. Suppose I use a router (say, with 4-ports) as you suggest. can I connect to each one of the ports an 8-port switch (for a total of 32-ports)?
 
If so, can each of the machines access another using SSH?

---

### Post by amauk on 2010-09-27
> **csharpplus said:**
> Suppose I use a router (say, with 4-ports) as you suggest. can I connect to each one of the ports an 8-port switch (for a total of 32-ports)?Yes

> **csharpplus said:**
> If so, can each of the machines access another using SSH?Yes

---

### Post by csharpplus on 2010-09-27
great -- thank you.

---

### Post by amauk on 2010-09-27
> **csharpplus said:**
> great -- thank you.no problem

---

### Post by csharpplus on 2010-09-27
amauk,
 
thank you for all of your help!
 
I just thought of the following: there is a chance I might be interested to install condor as well. given your expertise, which 'configuration route' {DHCP / static IPs} would work best?

Would both be OK for condor?

---

### Post by amauk on 2010-09-27
I've never used condor, but I don't see that DHCP or static IPs would make much difference

---

### Post by csharpplus on 2010-09-28
Thanks!

---

