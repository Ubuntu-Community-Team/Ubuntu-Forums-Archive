---
title: "Bind error &quot;no current owner name&quot;"
date: 2013-06-29
forum: Installation &amp; Upgrades
---

### Post by melc_sokat on 2013-06-29
Hello,

I installed bind on my server and did the folowing configuration:
```

;
; BIND data file for local loopback interface
$ORIGIN example.com.
; $TTL  10800 @ IN      SOA     ns1.example.com. root.example.com. (
                              2 ; Serial
                          10800 ; Refresh
                            900 ; Retry
                        2419200 ; Expire
                          10800 )
        ; Negative Cache TTL ;
                IN                      NS      ns1.example.com.
                IN                      A      93.114.107.198
ns1           IN                       A      93.114.107.198
www         IN                       A      93.114.107.198


```



I just need www only at this time.

What i get is the folowing error.

```

/etc/bind/db.example.com:5: no current owner name
zone  example.com/IN: loading from master file /etc/bind/db.example.com failed: no owner
zone  example.com/IN: not loaded due to errors.

```

Anyone got any ideea ?


Thank you.

---

### Post by melc_sokat on 2013-07-08
Solved. 
I just installed poweradmin.

---

