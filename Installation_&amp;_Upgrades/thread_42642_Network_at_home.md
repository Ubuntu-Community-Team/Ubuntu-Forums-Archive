---
title: "Network at home"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by Turtle.net on 2005-06-18
Hi,
I have a PC using Ubuntu Hoary and I installed the same Ubuntu box on my laptop.
I tried to install a network with these two machines ... but with no success.
Here is the configuration I have :
On my PC I have two ethernet cards eth0 (192.168.25.101) for the local network and eth1 (DHCP) for my internet access. I use Firestarter to protect my PC.
On my laptop I have a ethernet card eth0 (192.168.25.102) connected to my PC.
I can ping one machine on the other and vice versa
I can ping an IP adress from my laptop but I cannot ping an adress like [www.google.com](www.google.com)...

Can someone help me to solve this problem ?

---

### Post by rvergara on 2005-06-18
This is a DNS issue, check that your laptop is inheriting a DNS address via DHCP or set up one manually.

Ramiro

---

### Post by Turtle.net on 2005-06-19
Thanks 
...but...euh....how can I do that  :???:

---

### Post by word_virus on 2005-06-19
[QUOTE=Turtle.net]Thanks 
...but...euh....how can I do that  :???:[/QUOTE]

On the laptop, go to System -> Network and click the DNS tab, choose 'Add' and type in the DNS server IP's the other box is using.

---

### Post by Turtle.net on 2005-06-19
:roll: I change the DNS on my laptop using the same IP's used as DNS for my PC (that is to say 212.27.54.252)
but ```
 $ping 212.27.54.252
connect: Network is unreachable
```
and ```
$ping www.google.com
ping: unknown host www.google.com
```

and I can still ping my PC from my laptop

 ](*,)

---

### Post by paddy2706 on 2005-06-19
you have to tell the computer that is supposed to route the request to the internet to do so.

iptables are very helpful and easy to manage, just google for iptables, routing

---

### Post by jobezone on 2005-06-19
[QUOTE=paddy2706]you have to tell the computer that is supposed to route the request to the internet to do so.

iptables are very helpful and easy to manage, just google for iptables, routing[/QUOTE]
 Doesn't firestarter have a little wizard for creating a network? turtle.net, try it out!

---

### Post by Turtle.net on 2005-06-19
I tried the Firestarter wizard ... but absolutely no improvement.
And after that I tried to use my brain  O:) 
...and I add the IP of my PC as the gateway for my laptop.

After that I restarted the network ```
$sudo /etc/init.d/networking restart
```

(Wonderful idea isn't it  :razz: )

And now....;everything is working again !

Thanks all for your help

---

