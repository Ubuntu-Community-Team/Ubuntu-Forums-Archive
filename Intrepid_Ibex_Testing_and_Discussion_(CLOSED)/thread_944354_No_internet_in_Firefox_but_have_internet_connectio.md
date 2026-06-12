---
title: "No internet in Firefox but have internet connection (Intrepid)"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bodzasfanta on 2008-10-11
I've just finished the upgrading to 8.10 Intrepid Ibex. Everything went fine, I didn't have any problems.

But, I don't have internet. I mean Firefox and Epiphany says, there are problmes with internet connection. But I have connection! Pidgin works. I did ping some adresses and I got response. So whats the problem? I did try reconfigure my ADSL connection through pppoeconf but it also doesn't help me (I mean, pppoeconf went okay but the Firefox still doesn't work)

---

### Post by dhtseany on 2008-10-11
Try opening terminal and type the following:
```
$ ping google.com
```

Let it go for a few hops and press Ctrl + C to make it stop. Post the output.

Peace
Sean

---

### Post by bodzasfanta on 2008-10-11
```

bodzasfanta@bodzasfanta-laptop:~$ ping google.com
PING google.com (209.85.171.99) 56(84) bytes of data.
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=1 ttl=242 time=193 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=2 ttl=242 time=194 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=3 ttl=242 time=194 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=4 ttl=242 time=193 ms
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3010ms
rtt min/avg/max/mdev = 193.050/194.059/194.871/0.896 ms

```

---

### Post by superprash2003 on 2008-10-11
open your firefox browser and type this ip 209.85.171.99 .. does it open the google pagE?? if so its a DNS problem. you would need to assign DNS servers manually.

---

### Post by bodzasfanta on 2008-10-11
A few minutes ago I had a system update/upgrade. Now everything goes well. I think and hope it was a temporary problem.

---

### Post by snake444 on 2008-10-11
i have this problem  too, thee network manager shows theres no connection
but im connected to internet trough pppoeconf, so i opened firefox clicked file and removed the V from Work offline and it works now

---

### Post by dhtseany on 2008-10-11
I agree, it was probably a DNS problem. Sometimes the DHCP server over the PPPoE (DSL) connection will lag a bit and not send the DNS values with the IP address it assigns. If it does it again try restarting your browser as Firefox will actually cache DNS addresses. Other posts also suggest the following:
```
$ sudo /etc/init.d/network restart
``` or ```
$ sudo /etc/init.d/dns-clean start
```. One thread also says telling FF to work offline then back to working online will clear it too.

Hope this helps
Sean

---

