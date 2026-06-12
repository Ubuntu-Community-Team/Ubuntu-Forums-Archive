---
title: "Domain names with ssh?"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by mlapaglia on 2008-06-22
I just registered a domain name with godaddy, and it is forwarded to my router's static ip address.

From a remote computer I can ssh in using the router's ip address, but when I try using the domain name, it doesn't connect.

What am I doing wrong?

---

### Post by wdaniels on 2008-06-22
You may have to wait a while for the DNS record to propagate to your ISP's nameservers. Try:

```
nslookup <your domain>
```

...and see what you get.

---

### Post by mlapaglia on 2008-06-22
k, this is what I got. Do you know how long it takes for the record to get upgraded?




mlapaglia@amanda-laptop:~$ nslookup [www.itsneverlupus.net](www.itsneverlupus.net)
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
[www.itsneverlupus.net](www.itsneverlupus.net)	canonical name = itsneverlupus.net.
Name:	itsneverlupus.net
Address: 64.202.189.170

---

### Post by wdaniels on 2008-06-22
> **mlapaglia said:**
> Address: 64.202.189.170

So is that the right address or not? If it is, then it's already updated. If not, then it can sometimes take about 24 hours, but usually much less.

---

### Post by mlapaglia on 2008-06-22
oh, no that isn't the right IP, that is godaddy's ip address

mlapaglia@amanda-laptop:~$ whois 64.202.189.170

OrgName:    GoDaddy.com, Inc. 
OrgID:      GODAD
Address:    14455 N Hayden Road
Address:    Suite 226
City:       Scottsdale
StateProv:  AZ
PostalCode: 85260
Country:    US

NetRange:   64.202.160.0 - 64.202.191.255 
CIDR:       64.202.160.0/19 
NetName:    GO-DADDY-SOFTWARE-INC
NetHandle:  NET-64-202-160-0-1
Parent:     NET-64-0-0-0-0
NetType:    Direct Allocation
NameServer: CNS1.SECURESERVER.NET
NameServer: CNS2.SECURESERVER.NET
NameServer: CNS3.SECURESERVER.NET
Comment:    
RegDate:    2002-10-22
Updated:    2007-06-14

OrgAbuseHandle: ABUSE51-ARIN
OrgAbuseName:   Abuse Department 
OrgAbusePhone:  +1-480-624-2505
OrgAbuseEmail:  [email]abuse@godaddy.com[/email]

OrgNOCHandle: NOC124-ARIN
OrgNOCName:   Network Operations Center 
OrgNOCPhone:  +1-480-505-8809
OrgNOCEmail:  [email]noc@godaddy.com[/email]

OrgTechHandle: NOC124-ARIN
OrgTechName:   Network Operations Center 
OrgTechPhone:  +1-480-505-8809
OrgTechEmail:  [email]noc@godaddy.com[/email]

# ARIN WHOIS database, last updated 2008-06-21 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

---

### Post by wdaniels on 2008-06-22
Well, so long as you set it correctly from your godaddy account (i.e. using an A record to point to your static ip, assuming godaddy let's you edit the DNS zone directly that way) then it's just a waiting game now...but double check that you set it correctly because there is nothing worse than waiting 24 hours or more only to find that you made the change incorrectly (I know, I've done it, more than once :D)!

---

### Post by mlapaglia on 2008-06-22
oh, I forgot about the A name, i was using godaddy's "forward to a different http address" option. I needed to click on the "Total DNS Control and MX Records" option, and change the A name record. It changed in a few minutes.

Thanks for pointing me in the right direction!

---

### Post by mlapaglia on 2008-06-22
ok, I've got another question. My ISP blocks port 80, and I'm wanting to run a website on my computer.

The godaddy dns control doesn't let me assign a port number to the ip address, so the only other way to do that would be through using a dynamic dns that could right?

---

### Post by scxtt on 2008-06-22
specify a different port via the address bar ... for example,

[http://www.itsneverlupus.net:1234](http://www.itsneverlupus.net:1234)

and make sure that port is forwarded and has something listening on it

or use a flag for ssh ... for example,

ssh -p 1234 [www.itsneverlupus.net](www.itsneverlupus.net)

---

### Post by mlapaglia on 2008-06-22
](*,)

d'oh, forgot about that.
thanks :)

---

