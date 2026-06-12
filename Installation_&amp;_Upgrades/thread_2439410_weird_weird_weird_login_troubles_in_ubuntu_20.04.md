---
title: "weird weird weird login troubles in ubuntu 20.04"
date: 2020-03-27
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2020-03-27
when I login 
in to my machine I come here 
test@worker01:~$ 
I know that I have login to test@test20
but no matter what I do I can't change 
to test@test20
Thanks

---

### Post by Doug S on 2020-03-27
This thread needs to be moved to the development area.

For whatever reason your computer thinks its primary name is worker01.
I can get the same thing (also a 20.04 computer) if I login using an alias computer name:

```
doug@DOUG-64:~/config/etc/bind$ [COLOR="#FF0000"]ssh doug@test04[/COLOR]
... deleted non relevant stuff ...
doug@[COLOR="#FF0000"]test04[/COLOR]'s password:
Welcome to Ubuntu Focal Fossa (development branch) (GNU/Linux 5.4.0-18-generic x86_64)
... deleted non relevant stuff ...

Last login: Thu Mar 26 13:24:20 2020 from 192.168.111.101
[COLOR="#FF0000"]doug@s15[/COLOR]:~$

```Now, here is an excerpt from my related DNS stuff:

```
doug@DOUG-64:~/config/etc/bind$ [COLOR="#FF0000"]cat db.smythies.com[/COLOR]
;
; BIND data file for smythies.com
;
$TTL    604800
@       IN      SOA     smythies.com. doug.smythies.com. (
                        2020032401      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
                IN      A       192.168.111.1
;
@               IN      NS      ns1.smythies.com.
ns1             IN      A       192.168.111.1
www             IN      A       192.168.111.1

...
[COLOR="#FF0000"]s15[/COLOR]             IN      A       192.168.111.112
bla             IN      A       192.168.111.112
test01          IN      A       192.168.111.112
test02          IN      A       192.168.111.112
test03          IN      A       192.168.111.112
[COLOR="#FF0000"]test04[/COLOR]          IN      A       192.168.111.112
...
doug@DOUG-64:~/config/etc/bind$

```

---

### Post by hoboy on 2020-03-28
Hi 
what Ubuntu command have you used to change to doug@test04's password:  ???

Cheers

---

### Post by Doug S on 2020-03-28
> **hoboy said:**
> Hi 
what Ubuntu command have you used to change to doug@test04's password:  ???

CheersI didn't use any command. My point was that sometimes computers can have multiple network names that end up at the same place. However, they typically only have one reverse lookup answer. So in my example, I logged into 192.168.111.112 via one of many possible names, but the computer itself, thinks its name is "s15".

---

