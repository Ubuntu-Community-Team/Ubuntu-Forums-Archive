---
title: "Eaton Network-M2 fail to load even with Github nut"
date: 2020-06-22
forum: Installation &amp; Upgrades
---

### Post by dvb91 on 2020-06-22
Hello,

I have an issue using "nut" and "Eaton 5PX" with Networkcard-M2.
I installed nut from GitHub, this version supports this new "M2 card" from Eaton :
- with my second UPS (using old network-card, not M2), all is OK.
- with M2 card, driver begins to load, but get stucks and never finish to load :

```
sudo /usr/local/ups/sbin/upsdrvctl start
Network UPS Tools - UPS driver controller 2.7.4.1
Network UPS Tools - Generic SNMP UPS driver 1.12 (2.7.4.1)
 >> System stops here. << 

```

/var/state/ups :```

snmp-ups-MGE.pid
>> Nothing else << 

```
I double checked all files.conf without finding anything :

Adding to /usr/local/ups/etc/nut.conf```

MODE=standalone
```

Adding to /usr/local/ups/etc/ups.conf```

[MGE]
driver = snmp-ups
port = 192.168.200.252
desc = "Eaton Evolution S3000"
community = public

```

Adding to /usr/local/ups/etc/upsd.conf```

LISTEN 127.0.0.1 3493
```

Adding to /usr/local/ups/etc/upsd.users```

[admin]
password = me
allowfrom = localhost
upsmon master
actions = SET
instcmds = ALL
[ups]
password = me
allowfrom = localhost
upsmon master
actions = SET
instcmds = ALL

[test]
password = me
allowfrom = localhost
upsmon master
actions = SET
 instcmds = ALL 

```

Running with theses commands :
 ```

sudo /usr/local/ups/sbin/upsdrvctl start
sudo /etc/init.d/nut-server start
/usr/local/ups/bin/upsc -l 

```
Does M2 card need a password before loading ?
Could you please help me to fix this issue ?

Thank you.

---

