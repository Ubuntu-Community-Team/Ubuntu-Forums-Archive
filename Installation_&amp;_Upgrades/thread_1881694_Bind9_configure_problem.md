---
title: "Bind9 configure problem"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by yy885 on 2011-11-16
Hello I have a few Bind9 configure question.

This is the info for this example.

Domain = mysite.info = 1.2.3.4
Ns1 = ns1.nameserver =  5.6.7.8
Ns2 = ns2.nameserver =  55.66.77.88

==========================
in the named.conf.options

options  {
        directory "/var/cache/bind";
        query-source address * port  53;
   recursion yes;
   allow-recursion { 127.0.0.1; };
   forwarders  { 5.6.7.8; 55.66.77.88; };
        allow-query { any; };
         allow-transfer { none; };
        auth-nxdomain no;
        listen-on-v6 {  any; };
};

==========================

in the /etc/bind/db.mysite

db.mysite

$TTL  604800
@       IN   SOA   mysite.info. dns. mysite.info. (
         201111161     ; Serial
        604800     ; Refresh
        86400       ;  Retry
        2419200    ; Expire
        604800 )    ; Negative Cache  TTL
;
@       IN     NS     dns. mysite.info.
   localhost    A     127.0.0.1
   ns1        A    5.6.7.8
   ns2        A     55.66.77.88

==========================

Are these 2 looks fine? and one more last question, how can can I test is it functional?

---

### Post by yy885 on 2011-11-16
Slave Server

/etc/bind/named.conf.local


zone "example.com" {
type master;
file "/etc/bind/db.example.com";
allow-transfer {
@ip_slave;
};
};


zone "example.com" {
type slave;
file "/etc/bind/db.example.com";
masters { @ip_master; };
};

what is ip_slave, ip_master? do I need to set it?

---

### Post by yy885 on 2011-11-16
Hello I have a few question about configure bind9 on Ubuntu 11.10.

This is my config so far but seems to be not working, I dont know do I  need to do more config or here already have lots of error? Ive tried to  config them in the past few days but still no luck.[IMG]http://static.linuxquestions.org/questions/images/smilies/headscratch1.gif[/IMG] so I wonder anyone here can give me a hand?


thanks


=======================================================
jtest.info
68.xxx.2xx.100

NS67.DOMAINCONTROL.COM
216.xx.xxx.47

NS68.DOMAINCONTROL.COM
208.xxx.255.47;

=======================================================

/etc/bind/named.conf
 	Code:
 	include "/etc/bind/named.conf.options"; zone "jtest.info" {     type master;     file "/etc/bind/db.jtest"; }; include "/etc/bind/named.conf.local"; include "/etc/bind/named.conf.default-zones"; 
=======================================================

/etc/bind/named.conf.options
 	Code:
 	options {         directory "/var/cache/bind";         query-source address * port 53; 	recursion yes; 	allow-recursion { 127.0.0.1; }; 	forwarders { 216.xx.xxx.47; 208.xxx.255.47; };         allow-query { any; };         allow-transfer { none; };         auth-nxdomain no;         listen-on-v6 { any; }; }; 

=======================================================

/etc/bind/db.jtest
 	Code:
 	; ; BIND data file for jtest.info ; $TTL 604800 @       IN      SOA      jtest.INFO. root.jtest.INFO. ( 201111163        ; Serial 172800         ; Refresh 900         ; Retry 1209600         ; Expire 3600 )       ; Negative Cache TTL ; IN      NS      NS67.DOMAINCONTROL.COM. IN      NS      NS68.DOMAINCONTROL.COM. *                       CNAME   jtest.INFO.

---

