---
title: "Can acces server remotely and locally, can not access internet from server"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tica vun on 2010-04-14
The title pretty much says it, I'm running lucid on my server, and I'm able to ssh into it remotely, it pings the local router fine, and I'm able to ping it from the LAN, but I'm unable to access the internet from it - pinging returns unknown hosts, and it can't update packages.

---

### Post by doas777 on 2010-04-14
can you get an nslookup or dig on [www.ubuntuforums.org?]("http://www.ubuntuforums.org?")
```
nslookup www.ubuntuforums.org
```if not, how do you usually get dns server addresses? dhcp?

if so, can you ping [www.ubuntuforums.org]("http://www.ubuntuforums.org?")  ?
if not, what is the output of 'route'

---

### Post by tica vun on 2010-04-14
My router uses dhcp, yeah. And internet works on all the other computers connected to the router, so I'm guessing that's not the problem.

```
$ nslookup www.ubuntuforums.org
;; connection timed out; no servers could be reached
$ ping www.ubuntuforums.org
ping: unknown host www.ubuntuforums.org
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0


```

---

### Post by doas777 on 2010-04-14
ok. the problem is that you don;t have an dns server set or the one that is there, is offline.

what is the output of 
```
cat /etc/resolv.conf
```?

one simple fix, is to lookup the dns server on one of the working hosts, and put it in the resolv.conf with a line like:
```

nameserver <ip of dns server>

```it is likely 'nameserver 192.168.1.1' if you have a newer router.
then restart networking on the server like so:
```
sudo /etc/init.d/networking restart
```then try the nslookup again.


alterntely, if you used network-manager to configure your servers network connection (is it a ubuntu server edition; cli only, or do you have a gui on it?) then you can add the dns server there.

---

### Post by tica vun on 2010-04-14
```
$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory
$ sudo su
# cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory
# echo 'nameserver 192.168.1.1' > /etc/resolv.conf
bash: /etc/resolv.conf: No such file or directory

```EDIT: Apparently the networking service is down and won't even start. Note, I'm doing all this connected to the machine remotely, and that somehow works. wtf?

```
$ sudo service networking start
networking stop/waiting
```

P.S.: I never even configured the connection beyond telling it to use the router's DHCP at install. It's always worked fine until today.

---

### Post by tica vun on 2010-04-15
bump

EDIT: Well, I got home and had local access to the server again. It turns out it was still stuck on the plymouth booting screen (for two days), so I rebooted it via power button. Works now.

---

### Post by doas777 on 2010-04-15
wow man. please, always reboot before you post for help.
so if the server wasn't booted, what were you running the commands above on?

---

### Post by tica vun on 2010-04-15
> **doas777 said:**
> wow man. please, always reboot before you post for help.
so if the server wasn't booted, what were you running the commands above on?

As I said, I was logged onto it remotely. I didn't have local access and I've disabled reboot and shutdown commands from remote access for security purposes. By the looks of it, it was stuck somewhere halfway through the booting process, as I could log onto it, but couldn't start the networking service.

---

