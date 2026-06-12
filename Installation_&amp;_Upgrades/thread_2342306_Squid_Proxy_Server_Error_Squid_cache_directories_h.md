---
title: "Squid Proxy Server Error Squid cache directories have not been initialized"
date: 2016-11-05
forum: Installation &amp; Upgrades
---

### Post by sherluck007 on 2016-11-05
dear Ubuntu Supporters iam new to ubuntu iam trying to use squid proxy server in webmin but it's show the error 

[ Your Squid cache directories /hdd1, /ssd1, /hdd2, /ssd2, /hdd3, /ssd3 have not been initialized.This must be done before Squid can be run. ] i also edit squid.conf file and uncomment the cache_dir ufs /var/spool/squid 100 16 256
but same problem and when i run the commond squid -z it's give result 

[ FATAL: Bungled /etc/squid/squid.conf line 3410: cache_dir rock /hdd1 ... min-size=100000
Squid Cache (Version 3.5.12): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.004 user + 0.004 sys
Maximum Resident Size: 32928 KB
Page faults with physical i/o: 6 ]
please someone help me iam trying to fix this problem since 3 days but i did not success..thanks in advance

---

### Post by nd.mashiah on 2017-03-28
have the same problem.
Solved?

---

### Post by SeijiSensei on 2017-03-28
Which problem?  The "cache not initialized" problem or the one about the misconfigured squid.conf file?

For the former, run the command
```
sudo squid -z
```

For the latter, I have no idea what "rock /hdd1" was supposed to be.  On my running Squid server, the only cache_dir directive is
```
cache_dir ufs /var/spool/squid 10000 16 256 
```

---

