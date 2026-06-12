---
title: "Server 23.10 DNS restrictions"
date: 2024-06-22
forum: Installation &amp; Upgrades
---

### Post by lisanels47 on 2024-06-22
I have ubuntu server 23.10 running great, it provides dhcp and dns to the network.  

lisa@server:~$ host microsoft.com
microsoft.com has address 127.0.0.1
microsoft.com mail is handled by 10 microsoft-com.mail.protection.outlook.com.
lisa@server:~$ 

As above on the server I put microsoft.com in the hosts file, and you can see the response.

But on the clients respond like this:

lisa@lisa-Legion-Y545-PG0:~$ host microsoft.com
microsoft.com has address 20.76.201.171
microsoft.com has address 20.112.250.133
microsoft.com has address 20.231.239.246
microsoft.com has address 20.236.44.162
microsoft.com has address 20.70.246.20
microsoft.com has IPv6 address 2603:1030:c02:8::14
microsoft.com has IPv6 address 2603:1030:b:3::152
microsoft.com has IPv6 address 2603:1010:3:3::5b
microsoft.com has IPv6 address 2603:1020:201:10::10f
microsoft.com has IPv6 address 2603:1030:20e:3::23c
microsoft.com mail is handled by 10 microsoft-com.mail.protection.outlook.com.
lisa@lisa-Legion-Y545-PG0:~$ 

lisa@lisa-Legion-Y545-PG0:~$ cat /etc/resolv.conf 
# This is /run/systemd/resolve/resolv.conf managed by man:systemd-resolved(8).
# Do not edit.
#
# This file might be symlinked as /etc/resolv.conf. If you're looking at
# /etc/resolv.conf and seeing this text, you have followed the symlink.
#
# This is a dynamic resolv.conf file for connecting local clients directly to
# all known uplink DNS servers. This file lists all configured search domains.
#
# Third party programs should typically not access this file directly, but only
# through the symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a
# different way, replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.


nameserver 192.168.10.6
search mynet.net
lisa@lisa-Legion-Y545-PG0:~$ 

The 10.6 address is my server, and I'd like to find a way to make it's named respond to clients like it does on the server itself.

---

### Post by currentshaft on 2024-06-22
How does the server provide DNS? What program are you using to do so? Does it have a configuration option to honor /etc/hosts?

---

### Post by Impavidus on 2024-06-24
Not directly relevant to your issue, but just a heads-up: Ubuntu 23.10 will reach end of life [in just 17 days]("https://fridge.ubuntu.com/2024/06/05/ubuntu-23-10-mantic-minotaur-reaches-end-of-life-on-july-11-2024/?_gl=1*dj11l4*_gcl_au*Nzk2MDQzMjMyLjE3MTkyMTkyODA"). Try and upgrade to 24.04 within two weeks. You may prefer to deal with your current issue after that, as a release upgrade may affect it.

It's typically best to run servers on LTS releases. 24.04 is an LTS release, with standard support until April 2029.

---

### Post by lisanels47 on 2024-06-25
The server is running bind9/named.  So it uses it's hosts file and then gets DNS via the assigned 'forward' .
For some reason, the ubuntu clients bypass this and do their own DNS lookups outside of my server.

---

### Post by currentshaft on 2024-06-25
From one of the clients:

dig a microsoft.com @192.168.10.6

I use dnsmasq, not bind9, but I wouldn't expect /etc/hosts to be honored by either program. You probably want to just NXDOMAIN the entire microsoft.com zone in your configuration instead.

---

