---
title: "server dhcp with ubuntu"
date: 2004-11-25
forum: Installation &amp; Upgrades
---

### Post by ghepx on 2004-11-25
Hello,
i'm a new user of linux... recently i install linux ubuntu in my Pc ...i want configure ubuntu server dhcp but i don't know the procedure... there is some that halp me???

Thanks

---

### Post by jiyuu0 on 2004-11-25
[http://kitech.com.my/ubuntu/4.10/#installdhcpserver](http://kitech.com.my/ubuntu/4.10/#installdhcpserver)

---

### Post by ghepx on 2004-11-26
when execute apt.get install dhcp-server
shell answer me with:
reading pack...ok
produced dipendence trees..ok
E: impossible find dhcp.server

whatis this problem??

---

### Post by p!=f on 2004-11-26
[QUOTE=ghepx]when execute apt.get install dhcp-server
shell answer me with:
reading pack...ok
produced dipendence trees..ok
E: impossible find dhcp.server

whatis this problem??[/QUOTE]
There are no dots...
```

sudo apt-get install dhcp3-server

```
But I would suggest using dnsmasq instead which also contains DHCP server.

---

### Post by ghepx on 2004-11-26
if i write apt-get install dhcp3-server the problem persist...and the terminal answare me the same message...

is possible the download dhcpo pack from internet???where??

---

### Post by p!=f on 2004-11-26
[QUOTE=ghepx]if i write apt-get install dhcp3-server the problem persist...and the terminal answare me the same message...

is possible the download dhcpo pack from internet???where??[/QUOTE]
You probably don't have universe repository turned on.
Read here how to do it:
[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-09-30.5359349801](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-09-30.5359349801)

---

### Post by ghepx on 2004-11-26
my server is not connect ininternet!

---

### Post by p!=f on 2004-11-26
[QUOTE=ghepx]my server is not connect ininternet![/QUOTE]
How do you want to install the package using apt-get then?
You have to download dhcp3-server and all its dependencies, get it on the server and install.
To get dependencies for dhcp3-server, run...
```

apt-cache depends dhcp3-server

```
To install it locally use 
```

sudo dpkg -i <path/to/packages>

```

---

