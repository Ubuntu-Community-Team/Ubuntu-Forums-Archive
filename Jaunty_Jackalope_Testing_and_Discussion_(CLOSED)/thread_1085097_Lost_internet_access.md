---
title: "Lost internet access"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2009-03-02
i have a rather interesting problem.

i access the internet through a router. ubuntu has no problem getting the IP address and seeing other networked computers. i can get to the web interface of the router. the problem is that for some reason when i run the internet connectivity test on the routers web page it says that it can not get to the DNS servers.

but i can surf normally under windows xp. it is ubuntu that is giving me trouble. i am utterly confused. btw windows has everything set up on automatic.

---

### Post by caryb on 2009-03-02
I have this problem as well if you look at your /etc/resolv.conf file you will see it is not being updated with the settings from your DHCP server.


Cary

---

### Post by syko21 on 2009-03-03
I had a similar problem and it turned out to be an overzealously configured moblock (iptables firewall)

---

### Post by nyarnon on 2009-03-03
Try setting your box up with [http://www.opendns.com/](http://www.opendns.com/) see if that resolves the issue. Dynamic dns is a drag, opendns is the first thing I install on new boxes.

---

### Post by zekopeko on 2009-03-03
so how do i fix it? i have tried the opendns way but it's not working.
what else can i try?

---

### Post by nyarnon on 2009-03-03
Thats dificult the fact that you can reach the router puts the problem just there and not in Ubuntu. So what brand of router is it. Does it have a firewall/nat that lets xp access the net and blocks Ubuntu?

---

### Post by scaine on 2009-03-03
You could rule out the firewall aspects completely by running

```
ping 212.58.226.75
```If that responds, then put that address in the web browser : [http://212.58.226.75](http://212.58.226.75)

If you see the BBC site (or some of it) then you definitely have a DNS issue.  And if so, then your best bet is nyarnon's OpenDNS advice.  From [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu) there are instructions on how to set up just your PC with the relevant DNS.  Or edit resolv.conf with the 208.67.222.222 and 208.67.220.220 addresses then issue
```
sudo invoke.rc networking restart
```
... and see what access you have.

---

### Post by nyarnon on 2009-03-03
@scaine
He already tried opendns. My guess is router as he can reach that. I forgot to ask if his xp runs oin the same box :-(

---

### Post by scaine on 2009-03-03
Yeah, I saw that he tried OpenDNS, but I think he maybe tried the "router" way of using OpenDNS.  I'm posting about putting OpenDNS on his actual Ubuntu build directly, using resolv.conf updates.  Hopefully that will point to a bug in Ubuntu not taking the correct IPv4 DNS settings.

There's a bug about IPv6 connectivity in Jaunty at the moment that *might* be relevant...
[https://bugs.launchpad.net/fedora/+source/glibc/+bug/313218](https://bugs.launchpad.net/fedora/+source/glibc/+bug/313218)

---

### Post by caryb on 2009-03-03
I travel between work & home with my laptop & when I get home & log on to the laptop my resolv.conf has not updated to my home settings very frustrating having to edit ivery time I change locations.


Cary

---

### Post by nyarnon on 2009-03-04
> **caryb said:**
> I travel between work & home with my laptop & when I get home & log on to the laptop my resolv.conf has not updated to my home settings very frustrating having to edit ivery time I change locations.


Cary

Thats one thing OpenDns should resolve. Did you follow the ubuntu directions or did you change it in your router? Your XP box is on a different box? What is the brand and model of your router? Does your router prevent your laptop from going out through a nat/firewall that only allows your xp box?

---

### Post by zekopeko on 2009-03-04
i finally found out what was wrong.
vmware created a virtual eth device and network manager was using that and not my network card.
i simply removed DHCP IP address assignments to the virtual adapters with vmware network editor.
thanks for trying to help out (all of you).much appreciated.

---

