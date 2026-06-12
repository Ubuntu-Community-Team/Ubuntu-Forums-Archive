---
title: "old gentoo user can't get access to gateway"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by pccampos on 2005-04-28
Hi,

I just killed a 2 year Gentoo linux installation to try Ubuntu. But since installation I'm not suceed to connect through internet.

Here is the problem, my network is a radio network, which a router in my building. It used to configure the network by dhcp with the following values (it worked on gentoo):

```
ip: 192.168.168.198
mask: 255.255.255.255
gateway: 192.168.255.11
```

As you can see the gateway isn't in same network of ip, and there is a weird mask too. The problem, Ubuntu seems not able to create a route, "ifconfig" shows all the correct configuration above, but a route -n doesn't shows any route.

Please, don't say that my network is ugly and shall never work on Ubuntu, it worked on Gentoo and all other distribution that I tried. I can't change my ISP configuration, so it has to work the way it is.

Thanks, Pedro

---

### Post by heimo on 2005-04-28
I'd love to understand your network settings... Weird*.

I'm not at Linux box, so my instructions may be totaly off.

Have you tried:
 ```
/sbin/route add default gw 192.168.255.11
/sbin/route -n (to verify)

```

Any error messages?


*) Ah! Stupid me! You may need to setup it for interface, not ip. Don't know. I think it's called "single host route". /32

<guesses>

EDIT: I think keyword nexthop can be key to success. Something like:
[http://www.phear.org/content/view/14/2/]("http://www.phear.org/content/view/14/2/")

Or *via*
[https://www.redhat.com/archives/valhalla-list/2003-March/msg00220.html]("https://www.redhat.com/archives/valhalla-list/2003-March/msg00220.html")

</guesses>

---

### Post by pccampos on 2005-04-28
Thanks for your reply Heimo,

Here is how I managed to solve my problem.  
I used a live CD to get a working route configuration. I could see that my gateway is from 192.168.168.222. 

Then I booted on Ubuntu, the dhcp gave me a correct ip and netmask configuration but it was unable to add a working route, so I manually added this two routes (following one of the pages you recommended me):

```
ip route replace 192.168.168.222 dev eth0 scope link
ip route replace default via 192.168.168.222 dev eth0
```

That was not the optimal solution but now it is easier to find where is the problem. Thanks, this is surelly a prompt community.

---

