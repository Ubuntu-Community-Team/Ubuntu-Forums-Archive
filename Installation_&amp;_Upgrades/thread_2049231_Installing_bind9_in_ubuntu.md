---
title: "Installing bind9 in ubuntu"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by mick463 on 2012-08-28
Hi i am trying to get bind9 to advertise my websites I have registered 2 domain names with crazy domains.com.au last night at aprox 9 pm.

They have still not come up and I am beginning to think I have done something wrong.I have set the master names in the name.conf.local file like so.

```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "mjcmelectricalservices.com.au" {
	type master;
        file "/etc/bind/db.mjcmelectricalservices";
};

zone "micksblog.com.au" {
	type master;
        file "/etc/bind/db.micksblog";
};
```

and i have created two .db files as in the name.conf.local like so.
```

;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	mjcmelectricalservices.com.au. root.mjcmelectricalservices.com.au. (
			      4		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns.mjcmelectricalservices.com.au.
@	IN	A	123.2.148.42
@	IN	AAAA	::1
ns      IN      A       123.2.148.42
```

I have not created a reverse lookup zone as you can see as i am told that is not needed.

I have created an exception port 53 UDP and TCP in my firewall and port forwarded port 53 UDP and TCP in my router.
Crazydomains.com asked for my NS so i said 

ns.mjcmelectricalservices.com.au. 123.2.148.42

Have I done anything incorrect is there something else i need to do or am I just being impatient.

Thankyou mick463

---

