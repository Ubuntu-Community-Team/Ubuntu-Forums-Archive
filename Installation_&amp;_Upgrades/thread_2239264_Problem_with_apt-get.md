---
title: "Problem with apt-get"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by m_a2 on 2014-08-12
Hello I am new to Ubuntu and still learning and getting used to using terminal. For one of my university assignments I am asked to create a DNS server for a business using Ubuntu, for this I decided to use static addressing, I done this by making changes to the interfaces file and using apt-get remove to remove the dhcp client. 

The problem I am facing is when I try to use apt-get install bind9 I get the following error:


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing

I believe this problem has only started happening after I attempted to make my addresses static as prior to doing so I used the apt-get update  command which worked fine however now even that brings up this error.

Any idea why this is happening, I am a newbie to Ubuntu so I apologise if this is a dumb question which has an obvious solution.

---

### Post by steeldriver on 2014-08-12
Hello and welcome to the forums

Can you post the contents of your current /etc/network/interfaces file please? Did you remember to add at least one nameserver? 

(DHCP usually provides DNS configuration as well as the basic IP addressing)

---

### Post by m_a2 on 2014-08-12
Will a screen shot of the /etc/network/inrerfaces file be suffice as I am doing this project using a virtual machine therefore cant copy and paste the content directly into here. 

As for the name server does this need to be the default gateway?

[IMG]http://postimg.org/image/rm5g05j7z/[/IMG]

---

### Post by m_a2 on 2014-08-12
[http://postimg.org/image/rm5g05j7z/](http://postimg.org/image/rm5g05j7z/)

Link for screen shot

---

### Post by steeldriver on 2014-08-12
**If** your gateway is a router that is running a DNS server, then yes you can just specify that. Otherwise you can use a public DNS provider like OpenDNS or google e.g.

```

dns-nameservers 8.8.8.8  8.8.4.4

```

---

### Post by m_a2 on 2014-08-12
Thank you sooo much steeldriver. It was a problem with the nameserver. Really appreciate the help :D

---

