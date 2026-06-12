---
title: "Firestarter launch error."
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-03-16
No search found this one nor did I see it in Launchpad. I'm getting this error after installing Firestarter on jaunty alpha 6 & trying to launch; 
[I]Could not launch 'Firestarter'
Failed to execute child process "su-to-root" (No such file or directory).[/I]
Any ideas?

---

### Post by mhgsys on 2009-03-16
Since I don't boot jaunty I have no idea. 

have a look here.:

[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=printview&t=6187&start=0](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=printview&t=6187&start=0)

---

### Post by GARoss on 2009-03-16
Thanks, mhgsys
I didn't mention in my post that my network is 3 computers; XP Home, Ubuntu 8.10 & Ubuntu jaunty. Firestarter works perfectly on Ubuntu 8.10 (both Ubuntu 8.10 & Ubuntu jaunty are amd64's) but Ubuntu jaunty is were I get the error.

---

### Post by taavikko on 2009-03-16
IMHO firestarter is obsolete, when there's GUFW available.
To an already installed ufw

Both of these front-end's are just a GUI-tool to manage build-in iptables/netfilter thingy...

---

### Post by Nullack on 2009-03-16
I just use UFW

---

### Post by taavikko on 2009-03-16
> **Nullack said:**
> I just use UFW

I don't even use that one, have my router do the work for me.

and when no application is listening to outside world by default, I'm safe...

Sure I have ssh and few, but changing the default port, and tightened security, I'm pretty safe...

It's whole different issue when there's no NAT or hardware firewall,
but ufw is fine effort to apply changes to iptables, still I like to use it directly

```
man iptables
```
for more info...

---

### Post by Nullack on 2009-03-16
Thanks mate :)

I run NAT, and a stateful packet inspection HW router, but I still run UFW with default deny on the internal network machines. I dont open any WAN ports as I dont have any services I need open.

---

### Post by GARoss on 2009-03-16
> **taavikko said:**
> IMHO firestarter is obsolete, when there's GUFW available.
To an already installed ufw

Both of these front-end's are just a GUI-tool to manage build-in iptables/netfilter thingy...

Thanks. GUFW looks good. I set it up for to accept to/from IPs on my network & worked 1st time around.

---

