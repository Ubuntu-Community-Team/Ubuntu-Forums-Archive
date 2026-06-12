---
title: "Network problem"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by tschweg on 2005-08-03
Hello, I'm having some network problems with my Ubuntu.
It's the same problem, others have mentioned in the forums.

First, here's how my network looks:
=========================
[Internet] <---- [Cablemode] <---- [Router] <---- [Ubuntu]
- the cablemodem passes the router a public IP
- the router leases DHCP addresses to my clients (192.168.1.x)

What works:
=========
- Ubuntu can lease a DHCP IP from my router
- it can resolve hosts correctly (google.com, ubuntuforums.org, etc.)
- SSH 
- SMTP & POP3 over telnet 
- Ping to 127.0.0.1
- Ping to localhost
- Ping to external hosts (google etc)
- Ping to internal clients

What doesn't:
==========
- Firefox (gives back a message "document contains no data") both internal   websites(router) and external
- apt-get can't connect to a repository
- E-Mail, AIM, etc. doesn't work


What I've tried so far:
===============
- Setting DNS manually
- Changing from dynamic to static IP
- Manually writing /etc/resolv.conf
- Locking (chattr +i) resolv.conf
- Enabling "prepend domain-name-servers x.x.x.x" in /etc/dhcp3/dhclient.conf
- Setting a static route to route all traffic to my router
- Dig check the DNS server(s) to see if they are working
- Checked router settings with a Windows XP and a Fedora Core 4 client
- apt-get resolv.conf, pump etc. <-- Doesn't work, apt-get tells me, that these are not installable files.



Question:
=======
**What other options do I have to make it work?**


Your help is greatly appreciated.
Thank you in advance,
tschweg

---

### Post by tnilsson on 2005-08-03
[QUOTE=tschweg]Hello, I'm having some network problems with my Ubuntu.
It's the same problem, others have mentioned in the forums.

First, here's how my network looks:
=========================
[Internet] <---- [Cablemode] <---- [Router] <---- [Ubuntu]
- the cablemodem passes the router a public IP
- the router leases DHCP addresses to my clients (192.168.1.x)

What works:
=========
- Ubuntu can lease a DHCP IP from my router
- it can resolve hosts correctly (google.com, ubuntuforums.org, etc.)
- SSH 
- SMTP & POP3 over telnet 
- Ping to 127.0.0.1
- Ping to localhost
- Ping to external hosts (google etc)
- Ping to internal clients

What doesn't:
==========
- Firefox (gives back a message "document contains no data") both internal   websites(router) and external
- apt-get can't connect to a repository
- E-Mail, AIM, etc. doesn't work


What I've tried so far:
===============
- Setting DNS manually
- Changing from dynamic to static IP
- Manually writing /etc/resolv.conf
- Locking (chattr +i) resolv.conf
- Enabling "prepend domain-name-servers x.x.x.x" in /etc/dhcp3/dhclient.conf
- Setting a static route to route all traffic to my router
- Dig check the DNS server(s) to see if they are working
- Checked router settings with a Windows XP and a Fedora Core 4 client
- apt-get resolv.conf, pump etc. <-- Doesn't work, apt-get tells me, that these are not installable files.



Question:
=======
**What other options do I have to make it work?**


Your help is greatly appreciated.
Thank you in advance,
tschweg[/QUOTE]
 
What I use to do on every new Ubuntu installation is to diable ipV6. I do not need ipv6, so why should it be enabled.

This is what I do.

cd /etc/modprobe.d

Created a file called local-aliases

For instance:
vi local-aliases

Populate the file with this content:

# Disable ipv6
alias net-pf-10 off
alias ipv6 off


--
Reboot your machine
Check that ipv6 is not enabled with the command : ifconfig -a
It the sit0 interface is gone, then it is O.K.

---

### Post by tschweg on 2005-08-03
I have disabled IPv6, but it didn't work. I still get the same problem.
But thanks for the help.

I finally got it working now.  \\:D/ 

Here's my solution:
1. Download [resolvconf](http://packages.debian.org/stable/net/resolvconf) , [pump](http://packages.debian.org/stable/base/pump) and [dnsmasq](http://packages.debian.org/unstable/net/dnsmasq) from any available PC with internet access.
2. Put it on a floppy and mount it in ubuntu 
```
 sudo mount /dev/fd0 
```
3. Uninstall the old dhcp client
```
 sudo dpkg -r dhcp3-client
sudo dpkg -r dhcp3-common

```

4. Install the new packages
```
sudo dpkg -i /media/floppy0/resolvconf.deb 
```
5. Install pump
```
sudo dpkg -i /media/floppy0/pump.deb 
```
6. Install dnsmasq
```
sudo dpkg -i /media/floppy0/dnsmasq.deb 
```
7. Reboot your pc
```
sudo reboot
```
8. Check if your network is up, if not do
```
ifup eth0
```

Notes:
- dpkg refused to install pump while dhcp3 was still installed. So make sure to remove that one first. 
- Don't copy-paste the commands, I didn't include the full filename.

P.S. Kudos to the poster who wrote the original HowTo involving pump.

---

### Post by muaddip on 2005-08-20
I have same problem I want to install pump but 
I did not uninstall dhcp3-client 


sudo dpkg -r dhcp3-client
dpkg: dependency problems prevent removal of dhcp3-client:
 ubuntu-base depends on dhcp3-client.
dpkg: error processing dhcp3-client (--remove):
 dependency problems - not removing

---

