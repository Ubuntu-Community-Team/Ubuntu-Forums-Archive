---
title: "Accessing server using IP"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by brizvi on 2011-12-12
Hello everyone,
I installed Ubuntu Server at home and have the LAMP component in. I am connected to the web and was able to install Webmin.
 
In addition to the installation, I did the following:
 
IP address is: IP address 172.19.0.10
sudo vi /etc/network/interfaces
 
# The primary network interface
auto eth0
iface eth0 inet static
address 172.19.0.10
netmask 255.255.255.0
network 172.19.0.0
broadcast 172.19.0.255
gateway 172.19.0.1
 
I am able to access an index.html found in /etc/www when I w3m [http://localhost](http://localhost). I am also able to access it using my static IP: [http://172.19.0.10](http://172.19.0.10)
 
I am not able to access the site [http://172.19.0.10](http://172.19.0.10) off my laptop (from home). Once I can access this site from both internal and external computers, I can start working on webmin configs.

---

### Post by MAFoElffen on 2011-12-12
> **brizvi said:**
> Hello everyone,
I installed Ubuntu Server at home and have the LAMP component in. I am connected to the web and was able to install Webmin.
 
In addition to the installation, I did the following:
 
IP address is: IP address 172.19.0.10
sudo vi /etc/network/interfaces
 
# The primary network interface
auto eth0
iface eth0 inet static
address 172.19.0.10
netmask 255.255.255.0
network 172.19.0.0
broadcast 172.19.0.255
gateway 172.19.0.1
 
I am able to access an index.html found in /etc/www when I w3m [http://localhost](http://localhost). I am also able to access it using my static IP: [http://172.19.0.10](http://172.19.0.10)
 
I am not able to access the site [http://172.19.0.10](http://172.19.0.10) off my laptop (from home). Once I can access this site from both internal and external computers, I can start working on webmin configs.
Are you able to see the router table in a browser from your laptop? I do that to confirm that a new device when configuring a static IP to make sure it took. If it didn't then my router assigns it a dhcp ip.

Here is my /etc/network/interfaces file from one of my servers:
```

mafoelffen@hplp1000r:$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo 
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static 
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1

# The secondary network interface
auto eth1
iface eth1 inet static 
address 192.168.2.6
netmask 255.255.255.0
gateway 192.168.2.1

```
From what you posted, that only half of the config. The second half is in /etc/resolv.conf
to something similar to this:
```

# My ISP is westell.com and I use their DNS Servers
# domain westell.com
# search westell.com
nameserver 209.206.160.253, 209.206.184.250

```
This is my local info. You need to modify yours to your info.  If you open up Network tools on your laptop, change from local to your eth device, "netstat" tab, then routing table, you should be able to gather all that info.

Does that help?

---

### Post by MAFoElffen on 2011-12-12
So 172.19.0.10 is the fixed/static address assigned by your ISP?  Are you sure? No domain name registered? I don't see anything with that address...
```

mafoelffen@maf-ubuntu-01:~$ whois 172.19.0.10
#
# Query terms are ambiguous.  The query is assumed to be:
#     "n 172.19.0.10"
#
# Use "?" to get help.
#

#
# The following results may also be obtained via:
# http://whois.arin.net/rest/nets;q=172.19.0.10?showDetails=true&showARIN=false&ext=netref2
#

NetRange:       172.16.0.0 - 172.31.255.255
CIDR:             172.16.0.0/12
OriginAS:       
NetName:        PRIVATE-ADDRESS-BBLK-RFC1918-IANA-RESERVED
NetHandle:      NET-172-16-0-0-1
Parent:            NET-172-0-0-0-0
NetType:          IANA Special Use
Comment:        This block is used as private address space.
Comment:        Traffic from these addresses does not come from IANA.
Comment:        IANA has simply reserved these numbers in its database 
Comment:        and does not use or operate them. We are not the source 
Comment:        of activity you may see on logs or in e-mail records.
Comment:        Please refer to  http://www.iana.org/abuse/
Comment:             
Comment:        Addresses from this block can be used by 
Comment:        anyone without any need to coordinate with 
Comment:        IANA or an Internet registry. Addresses from
Comment:        this block are used in multiple, separately 
Comment:        operated networks.
Comment:        
Comment:        This block was assigned by the IETF in the
Comment:        Best Current Practice document, RFC 1918
Comment:        which can be found at:
Comment:        
Comment:        http://www.rfc-editor.org/rfc/rfc1918.txt
RegDate:        1994-03-15
Updated:        2011-04-12
Ref:            http://whois.arin.net/rest/net/NET-172-16-0-0-1

OrgName:        Internet Assigned Numbers Authority
OrgId:          IANA
Address:        4676 Admiralty Way, Suite 330
City:           Marina del Rey
StateProv:      CA
PostalCode:     90292-6695
Country:        US
RegDate:        
Updated:        2004-02-24
Ref:            http://whois.arin.net/rest/org/IANA

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number
OrgTechPhone:  +1-310-301-5820 
OrgTechEmail:  abuse@iana.org
OrgTechRef:    http://whois.arin.net/rest/poc/IANA-IP-ARIN

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number
OrgAbusePhone:  +1-310-301-5820 
OrgAbuseEmail:  abuse@iana.org
OrgAbuseRef:    http://whois.arin.net/rest/poc/IANA-IP-ARIN

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/whois_tou.html
#

```Meaning this is an internal/private network address...

EDIT-- There used to be a site that you could see what your IP was, how is is seen from the internet, from the outside looking in.  Let me see if I still have that link.

---

### Post by MAFoElffen on 2011-12-12
Here is those links:
[http://www.whatsmyip.org/](http://www.whatsmyip.org/)
[http://whatismyipaddress.com/](http://whatismyipaddress.com/)
[http://ipchicken.com/](http://ipchicken.com/)
[http://www.myipaddress.com/show-my-ip-address/](http://www.myipaddress.com/show-my-ip-address/)

Go to those and it will display the address.  From my servers, I have elinks installed (text based browser) as I can then use online tools such as these and report bugs to launchpad.

---

### Post by brizvi on 2011-12-14
I was able to fix this problem. I was making a couple of mistakes: 1. Needed to define a static internal IP in networking and 2. Using a router so needed to forward port requests to defined static IP.

Thanks everyone.

---

