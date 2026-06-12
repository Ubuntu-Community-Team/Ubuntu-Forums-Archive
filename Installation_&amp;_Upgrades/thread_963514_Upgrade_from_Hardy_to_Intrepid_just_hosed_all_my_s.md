---
title: "Upgrade from Hardy to Intrepid just hosed all my sites..."
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by rmsx97 on 2008-10-30
Apache is causing every one of my sites to redirect to /var/www

I removed the default site in sites-available, and now all my sites redirect to the first config entry in that directory.

Absolutely nothing changed in any of my config files, but on Apache starting up, I get:

[warn] NameVirtualHost *:80 has no VirtualHosts

It's as if the VirtualHost directive changed or something... I really have no clue how to remotely begin fixing this.

---

### Post by rmsx97 on 2008-10-30
Ok, I figured it out by pure random luck.

Putting  "NameVirtualHost *" above every single <VirtualHost *> directive somehow makes it work. 

Example:

```
NameVirtualHost *
<VirtualHost *>
        ServerName domain.net
        ServerAlias domain.net www.domain.net
        DocumentRoot /www/domain.net

        CustomLog /var/log/apache2/domain.net/access.log combined
</VirtualHost>
NameVirtualHost *
<VirtualHost *>
        ServerName t.domain.net
        ServerAlias t.domain.net
        DocumentRoot /www/t.domain.net

        CustomLog /var/log/apache2/t.domain.net/access.log combined
</VirtualHost>
```


Is there something that changed in the upgrade that suddenly made all this fail?

I really don't know what I changed or why this suddenly made everything work.

This fixes it for now, but I still get the following when Apache is started:

```

 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Thu Oct 30 10:33:16 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:16 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:16 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:16 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:16 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:16 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:16 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Thu Oct 30 10:33:17 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:17 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:17 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:17 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:17 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:17 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Oct 30 10:33:17 2008] [warn] NameVirtualHost *:80 has no VirtualHosts

```

---

### Post by palcica on 2008-10-30
> **rmsx97 said:**
> Apache is causing every one of my sites to redirect to /var/www
.


I have same problem... :(  do you have some solution for that?

---

### Post by drumcap on 2008-10-31
I think this is NameVirtualHost bug of new Apache version of ubuntu.
You dont have to use "*:80" (asterisk)

I solved it like this..
```

NameVirtualHost 192.168.0.100:80  <========= your IP

<VirtualHost 192.168.0.100:80>  <========== same as NameVirtualHost IP

</VirtualHost>

```

---

### Post by palcica on 2008-10-31
not workin :(

---

### Post by PeterB on 2008-11-07
Same problem here and can't find a fix for it... I have servername specified for all virtualhosts

---

### Post by CrazyMonkey77 on 2008-11-07
Usually when I'm declaring a NameVirtualhost it is in this format:

NameVirtualhost 192.168.0.100:80

Then list the VirtualHosts underneath as

<VirtualHost mywebsite.com:80>
blah...
blah..
blah..
</VirtualHost>

Of course in my example,  mywebsite.com must resolve to 192.168.0.100 in DNS, and this must be bound to a valid interface on your system. So you will need to do two things.

1.  Create an extra ip address on your machine (192.168.0.100 or whatever your website address is) that the web service can bind to - unless this is the ip address of your machine, but bear in mind that this should be a static address not a dhcp allocated one.

2.  Update your DNS server so that mywebsite.com resolves to 192.168.0.100 OR add a /etc/hosts entry if you are just accessing it from the same machine which will look something like;

192.168.0.100     mywebsite.com

Edit: it might be worth adding that if you don't have a DNS Server on your network, you'll need to add a host entry on all of the machines that you wish to use to connect to your website with. /etc/hosts on Linux and C:\Windows\System32\drivers\etc\hosts on windows machines...

---

