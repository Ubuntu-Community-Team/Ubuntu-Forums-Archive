---
title: "Won't upgrade?"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by duncan12 on 2012-04-27
```
duncan@Duncan-Linux:~$ sudo do-release-upgrade
[sudo] password for duncan: 
Checking for a new ubuntu release
Err Upgrade tool signature                                                     
  Connection failed                                                            
Get:1 Upgrade tool [5612 kB]                                                   
Fetched 5612 kB in 6s (51.9 kB/s)                                              
WARNING:root:file 'precise.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem.
```

I'm trying to upgrade from 11.10 to 12.04.

Is anybody else getting this? What should I do?

Thanks,
Duncan

---

### Post by garvinrick4 on 2012-04-27
You have a internet connection?
```
sudo apt-get update
```
Is she working?

---

### Post by duncan12 on 2012-04-27
> **garvinrick4 said:**
> You have a internet connection?
```
sudo apt-get update
```
Is she working?

Yeah, I'm writing this from the same computer.

apt-get update loads fine.

---

### Post by jroa on 2012-04-27
Did you try to update through the update manager?

---

### Post by duncan12 on 2012-04-27
Got it to work by going into Software Sources and changing "Server for New Zealand" to "Main Server". NZ server must be missing a file or something.

Thanks anyway

---

### Post by jroa on 2012-04-28
Great.

---

