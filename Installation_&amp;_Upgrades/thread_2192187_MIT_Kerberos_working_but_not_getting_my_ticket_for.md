---
title: "MIT Kerberos working but not getting my ticket for IBM Client Access"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by cmptrwhz on 2013-12-06
Hello I am using MIT kerberos, I can authenticate without any issue to the KDC server, I get my tgt ticket. I also get my sub-tickets for each service I access...for example any network shares and websites within the company network as they are all authenticated per your kerberos id. My issue is when I try to use kerberos for IBM client access using kerberos I am not getting a ticket for that service. I am running kubuntu in virtualbox on a windows 7 machine. I have spoke to my IT department and kerberos is setup correctly between the KDC and iSeries with the proper IDs. When I use IBM client access on my windows machine I receive a ticket for the service no problem. I must have something setup incorrectly on my end.

krb5.conf
```
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log
 
[libdefaults]
 default_realm = COMPANY.COM
 dns_lookup_realm = true
 dns_lookup_kdc = true
 ticket_lifetime = 24h
 forwardable = yes
 
[domain_realm]
 company.com = COMPANY.COM
 .company.com = COMPANY.COM

[realms]
 COMPANY.COM = {
  kdc = mbs-dc2.company.com
  admin_server = mbs-dc2.company.com
 }
```

klist
```
dave@davevirtual:~$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: thisisme@COMPANY.COM

Valid starting    Expires           Service principal
06/12/2013 08:16  06/12/2013 18:17  krbtgt/COMPANY.COM@COMPANY.COM
        renew until 07/12/2013 08:16
06/12/2013 08:21  06/12/2013 18:17  HTTP/companywebsite.company.com@COMPANY.COM
        renew until 07/12/2013 08:16
dave@davevirtual:~$
```

startup of client access
```
ibm5250 iseriesmachine.company.com -kerberos -sso -LANGID en_US
```

---

