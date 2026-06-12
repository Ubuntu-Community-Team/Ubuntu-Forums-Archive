---
title: "ubuntu 12.4 bind9 dns reverse look up not working"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by freddylaserna on 2013-04-01
When I test my reverse zone from local machine by host ip, it says it is ok. 1.2.3.4.in-addr.arpa domain name pointer host.domain.co. however when i use tools like mxtoolbox or dnsstuff i get these errors
[TABLE="class: table table-striped table-bordered table-condensed tool-result-table"]
[TR]
[TD]SMTP Reverse DNS Mismatch[/TD]
[TD].[/TD]
[/TR]
[/TABLE]
this is my config in name.config
zone "domain.co" {
        type master;
        file "/etc/bind/db.domain.co";
};

zone "3.2.1.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.3.2.1.in-addr.arpa";
};

this is the main zone

domain.co. IN SOA lnxhost.domain.co. root.domain.co. (
    2008080906 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)

domain.co. IN NS lnxhost.domain.co.
domain.co. IN MX 10 lnxhost.domain.co.

$ORIGIN domain.co.
localhost    IN A 127.0.0.1

; Set the hostnames in alphabetical order
lnxhost       IN A 1.2.3.4
domain.co. IN TXT "v=spf1 a -all"

this is the reverse entry

; IP Address-to-Host DNS Pointers for the 192.168.0 subnet
@ IN SOA lnxhost.domain.co. root.domain.co. (
    2008080906 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)

3.2.1.in-addr.arpa.                IN      NS      lnxhost.domain.co.

233         IN PTR lnxhost.domain.co.

syslogs have these

Apr  1 13:19:01 lnxagelity named[1009]: zone 0.in-addr.arpa/IN: loaded serial 1
Apr  1 13:19:01 lnxagelity named[1009]: zone 127.in-addr.arpa/IN: loaded serial 1
Apr  1 13:19:01 lnxagelity named[1009]: /etc/bind/zones/rev.51.135.206.in-addr.arpa:2: no TTL specified; using SOA MINTTL instead
Apr  1 13:19:01 lnxagelity named[1009]: zone 1.2.3.in-addr.arpa/IN: loaded serial 2008080906
Apr  1 13:19:01 lnxagelity named[1009]: zone 255.in-addr.arpa/IN: loaded serial 1
Apr  1 13:19:01 lnxagelity named[1009]: zone domain.co/IN: loaded serial 2008080906
Apr  1 13:19:01 lnxagelity named[1009]: zone localhost/IN: loaded serial 2
Apr  1 13:19:01 lnxagelity named[1009]: managed-keys-zone ./IN: loaded serial 5
Apr  1 13:19:01 lnxagelity named[1009]: running

Why tools like mxtoolbox. dnsstuff, fail to do the reverse look up?

Any help would be appreciated. Just for the record, I have been researching this for about a week. Thanks

---

