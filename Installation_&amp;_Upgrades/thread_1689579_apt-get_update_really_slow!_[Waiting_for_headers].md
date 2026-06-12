---
title: "apt-get update really slow! [Waiting for headers]"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by Arminius Chieftan on 2011-02-17
Fresh install of 10.04 server and trying to run apt-get update but it takes forever! Gets caught up on [I][Waiting for headers]
[/I]
**source.list**
```
#This file was auto generated at 2011-01-12 0:38:09.
#Please visit http://ubuntu9.com for more infomation.

deb http://ftp.grokthis.net/ubuntu lucid  main restricted universe multiverse
deb-src http://ftp.grokthis.net/ubuntu lucid  main restricted universe multiverse
deb http://ftp.grokthis.net/ubuntu lucid-security  main restricted universe multiverse
deb-src http://ftp.grokthis.net/ubuntu lucid-security  main restricted universe multiverse
deb http://ftp.grokthis.net/ubuntu lucid-updates  main restricted universe multiverse
deb-src http://ftp.grokthis.net/ubuntu lucid-updates  main restricted universe multiverse
deb http://ftp.grokthis.net/ubuntu lucid-proposed  main restricted universe multiverse
deb-src http://ftp.grokthis.net/ubuntu lucid-proposed  main restricted universe multiverse
deb http://ftp.grokthis.net/ubuntu lucid-backports  main restricted universe multiverse
deb-src http://ftp.grokthis.net/ubuntu lucid-backports  main restricted universe multiverse

```

**ping**
```
 ping -c 5 ftp.grokthis.net
PING ftp.grokthis.net (206.251.37.236) 56(84) bytes of data.
64 bytes from 88480064-49ac-400c-91bd-ab3e1929640b.static.grokthis.net (206.251.37.236): icmp_req=1 ttl=49 time=59.0 ms
64 bytes from 88480064-49ac-400c-91bd-ab3e1929640b.static.grokthis.net (206.251.37.236): icmp_req=2 ttl=49 time=61.6 ms
64 bytes from 88480064-49ac-400c-91bd-ab3e1929640b.static.grokthis.net (206.251.37.236): icmp_req=3 ttl=49 time=60.8 ms
64 bytes from 88480064-49ac-400c-91bd-ab3e1929640b.static.grokthis.net (206.251.37.236): icmp_req=4 ttl=49 time=61.9 ms
64 bytes from 88480064-49ac-400c-91bd-ab3e1929640b.static.grokthis.net (206.251.37.236): icmp_req=5 ttl=49 time=62.5 ms

--- ftp.grokthis.net ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 59.020/61.201/62.577/1.256 ms

```

Any ideas on how to speed it up?

---

### Post by pedi0022003 on 2011-02-17
Have you tried changing the server?
I suggest you to use "Choose Best Server" option.

---

### Post by sikander3786 on 2011-02-17
> **pedi0022003 said:**
> Have you tried changing the server?
I suggest you to use "Choose Best Server" option.
+1

Instead, I would first recommend to choose the Main server and later you can switch to the Best Server, first we can see that there is no other problem.

Go to Software Center > Edit > Software Sources > Select Main Server for downloads and then paste the output of this command.

```
sudo apt-get update
```

---

### Post by Arminius Chieftan on 2011-02-17
Thanks for the replies however I'm doing this on 10.04 **server** and only use BASH commands (different issue trying to get a GUI); I've tried several source.list files to include the main server and still have problems.

Any other ideas?

```
root@SERVER1:~#** apt-get update**
Get:1 http://64.12.96.232 lucid Release.gpg [189B]
Ign http://64.12.96.232/ lucid/main Translation-en_US
Ign http://64.12.96.232/ lucid/restricted Translation-en_US
Ign http://64.12.96.232/ lucid/universe Translation-en_US
Ign http://64.12.96.232/ lucid/multiverse Translation-en_US
Get:2 http://64.12.96.232 lucid-security Release.gpg [198B]                    
Ign http://64.12.96.232/ lucid-security/main Translation-en_US                 
Ign http://64.12.96.232/ lucid-security/restricted Translation-en_US
Ign http://64.12.96.232/ lucid-security/universe Translation-en_US
Ign http://64.12.96.232/ lucid-security/multiverse Translation-en_US
Get:3 http://64.12.96.232 lucid-updates Release.gpg [198B]
Ign http://64.12.96.232/ lucid-updates/main Translation-en_US                  
Ign http://64.12.96.232/ lucid-updates/restricted Translation-en_US            
Ign http://64.12.96.232/ lucid-updates/universe Translation-en_US              
Ign http://64.12.96.232/ lucid-updates/multiverse Translation-en_US            
Get:4 http://64.12.96.232 lucid-proposed Release.gpg [198B]
Ign http://64.12.96.232/ lucid-proposed/main Translation-en_US                 
Ign http://64.12.96.232/ lucid-proposed/restricted Translation-en_US
Ign http://64.12.96.232/ lucid-proposed/universe Translation-en_US
Ign http://64.12.96.232/ lucid-proposed/multiverse Translation-en_US
Get:5 http://64.12.96.232 lucid-backports Release.gpg [198B]
Ign http://64.12.96.232/ lucid-backports/main Translation-en_US
Ign http://64.12.96.232/ lucid-backports/restricted Translation-en_US          
Ign http://64.12.96.232/ lucid-backports/universe Translation-en_US            
Ign http://64.12.96.232/ lucid-backports/multiverse Translation-en_US
Get:6 http://64.12.96.232 lucid Release [57.2kB]
Ign http://64.12.96.232 lucid Release                                          
Ign http://64.12.96.232 lucid-security Release                                 
Get:7 http://64.12.96.232 lucid-updates Release [44.7kB]
Ign http://64.12.96.232 lucid-updates Release                                  
Get:8 http://64.12.96.232 lucid-proposed Release [42.6kB]                      
Ign http://64.12.96.232 lucid-proposed Release                                 
Ign http://64.12.96.232 lucid-backports Release                                
Get:9 http://64.12.96.232 lucid/main Packages [1,386kB]
Ign http://64.12.96.232 lucid/main Packages                                    
Get:10 http://64.12.96.232 lucid/restricted Packages [6,208B]                  
Get:11 http://64.12.96.232 lucid/restricted Packages [6,208B]                  
Ign http://64.12.96.232 lucid/restricted Packages                              
Ign http://64.12.96.232 lucid/universe Packages                                
Get:12 http://64.12.96.232 lucid/multiverse Packages [180kB]
Get:13 http://64.12.96.232 lucid/multiverse Packages [180kB]                   
Ign http://64.12.96.232 lucid/multiverse Packages                              
Get:14 http://64.12.96.232 lucid/main Sources [659kB]                          
Ign http://64.12.96.232 lucid/main Sources                                     
Get:15 http://64.12.96.232 lucid/restricted Sources [3,775B]                   
Ign http://64.12.96.232 lucid/restricted Sources                               
Get:16 http://64.12.96.232 lucid/universe Sources [3,165kB]                    
Ign http://64.12.96.232 lucid/universe Sources                                 
Ign http://64.12.96.232 lucid/multiverse Sources                               
Get:17 http://64.12.96.232 lucid-security/main Packages [87.5kB]
Get:18 http://64.12.96.232 lucid-security/main Packages [87.5kB]               
Get:19 http://64.12.96.232 lucid-security/main Packages [87.5kB]               
Get:20 http://64.12.96.232 lucid-security/main Packages [87.5kB]
Ign http://64.12.96.232 lucid-security/main Packages
Get:21 http://64.12.96.232 lucid-security/restricted Packages [14B]            
Get:22 http://64.12.96.232 lucid-security/universe Packages [42.7kB]           
Get:23 http://64.12.96.232 lucid-security/universe Packages [42.7kB]           
Ign http://64.12.96.232 lucid-security/universe Packages                       
Ign http://64.12.96.232 lucid-security/multiverse Packages                     
Ign http://64.12.96.232 lucid-security/main Sources
Ign http://64.12.96.232 lucid-security/restricted Sources
Ign http://64.12.96.232 lucid-security/universe Sources
Ign http://64.12.96.232 lucid-security/multiverse Sources
Ign http://64.12.96.232 lucid-updates/main Packages
Ign http://64.12.96.232 lucid-updates/restricted Packages
Ign http://64.12.96.232 lucid-updates/universe Packages
Ign http://64.12.96.232 lucid-updates/multiverse Packages
Ign http://64.12.96.232 lucid-updates/main Sources
Ign http://64.12.96.232 lucid-updates/restricted Sources
Ign http://64.12.96.232 lucid-updates/universe Sources
Ign http://64.12.96.232 lucid-updates/multiverse Sources
Ign http://64.12.96.232 lucid-proposed/main Packages
Ign http://64.12.96.232 lucid-proposed/restricted Packages
Ign http://64.12.96.232 lucid-proposed/universe Packages
Ign http://64.12.96.232 lucid-proposed/multiverse Packages
Ign http://64.12.96.232 lucid-proposed/main Sources
Ign http://64.12.96.232 lucid-proposed/restricted Sources
Ign http://64.12.96.232 lucid-proposed/universe Sources
Ign http://64.12.96.232 lucid-proposed/multiverse Sources
Ign http://64.12.96.232 lucid-backports/main Packages
Ign http://64.12.96.232 lucid-backports/restricted Packages
Ign http://64.12.96.232 lucid-backports/universe Packages
Ign http://64.12.96.232 lucid-backports/multiverse Packages
Ign http://64.12.96.232 lucid-backports/main Sources
Ign http://64.12.96.232 lucid-backports/restricted Sources
Ign http://64.12.96.232 lucid-backports/universe Sources
Ign http://64.12.96.232 lucid-backports/multiverse Sources
Ign http://64.12.96.232 lucid/main Packages
Ign http://64.12.96.232 lucid/restricted Packages
Ign http://64.12.96.232 lucid/universe Packages
Ign http://64.12.96.232 lucid/multiverse Packages
Ign http://64.12.96.232 lucid/main Sources
Ign http://64.12.96.232 lucid/restricted Sources
Ign http://64.12.96.232 lucid/universe Sources
Ign http://64.12.96.232 lucid/multiverse Sources
Ign http://64.12.96.232 lucid-security/main Packages
Ign http://64.12.96.232 lucid-security/universe Packages
Ign http://64.12.96.232 lucid-security/multiverse Packages
Ign http://64.12.96.232 lucid-security/main Sources
Ign http://64.12.96.232 lucid-security/restricted Sources
Ign http://64.12.96.232 lucid-security/universe Sources
Ign http://64.12.96.232 lucid-security/multiverse Sources
Ign http://64.12.96.232 lucid-updates/main Packages
Ign http://64.12.96.232 lucid-updates/restricted Packages
Ign http://64.12.96.232 lucid-updates/universe Packages
Ign http://64.12.96.232 lucid-updates/multiverse Packages
Ign http://64.12.96.232 lucid-updates/main Sources
Ign http://64.12.96.232 lucid-updates/restricted Sources
Ign http://64.12.96.232 lucid-updates/universe Sources
Ign http://64.12.96.232 lucid-updates/multiverse Sources
Ign http://64.12.96.232 lucid-proposed/main Packages
Ign http://64.12.96.232 lucid-proposed/restricted Packages
Ign http://64.12.96.232 lucid-proposed/universe Packages
Ign http://64.12.96.232 lucid-proposed/multiverse Packages
Ign http://64.12.96.232 lucid-proposed/main Sources
Ign http://64.12.96.232 lucid-proposed/restricted Sources
Ign http://64.12.96.232 lucid-proposed/universe Sources
Ign http://64.12.96.232 lucid-proposed/multiverse Sources
Ign http://64.12.96.232 lucid-backports/main Packages
Ign http://64.12.96.232 lucid-backports/restricted Packages
Ign http://64.12.96.232 lucid-backports/universe Packages
Ign http://64.12.96.232 lucid-backports/multiverse Packages
Ign http://64.12.96.232 lucid-backports/main Sources
Ign http://64.12.96.232 lucid-backports/restricted Sources
Ign http://64.12.96.232 lucid-backports/universe Sources
Ign http://64.12.96.232 lucid-backports/multiverse Sources
Err http://64.12.96.232 lucid/main Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid/restricted Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid/universe Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid/multiverse Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid/main Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid/restricted Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid/universe Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid/multiverse Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-security/main Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-security/universe Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-security/multiverse Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-security/main Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-security/restricted Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-security/universe Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-security/multiverse Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-updates/main Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-updates/restricted Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-updates/universe Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-updates/multiverse Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-updates/main Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-updates/restricted Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-updates/universe Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-updates/multiverse Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-proposed/main Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-proposed/restricted Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-proposed/universe Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-proposed/multiverse Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-proposed/main Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-proposed/restricted Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-proposed/universe Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-proposed/multiverse Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-backports/main Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-backports/restricted Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-backports/universe Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-backports/multiverse Packages
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-backports/main Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-backports/restricted Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-backports/universe Sources
  Unable to connect to 64.12.96.232:http:
Err http://64.12.96.232 lucid-backports/multiverse Sources
  Unable to connect to 64.12.96.232:http:
[COLOR=Red]Fetched 995B in 1h 42min 27s (0B/s)[/COLOR]
W: Failed to fetch http://64.12.96.232/dists/lucid/main/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid/restricted/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid/universe/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid/multiverse/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid/main/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid/restricted/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid/universe/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid/multiverse/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-security/main/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-security/universe/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-security/multiverse/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-security/main/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-security/restricted/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-security/universe/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-security/multiverse/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-updates/main/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-updates/restricted/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-updates/universe/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-updates/multiverse/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-updates/main/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-updates/restricted/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-updates/universe/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-updates/multiverse/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-proposed/main/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-proposed/restricted/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-proposed/universe/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-proposed/multiverse/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-proposed/main/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-proposed/restricted/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-proposed/universe/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-proposed/multiverse/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-backports/main/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-backports/restricted/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-backports/universe/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-backports/multiverse/binary-i386/Packages.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-backports/main/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-backports/restricted/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-backports/universe/source/Sources.gz  Unable to connect to 64.12.96.232:http:

W: Failed to fetch http://64.12.96.232/dists/lucid-backports/multiverse/source/Sources.gz  Unable to connect to 64.12.96.232:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by sikander3786 on 2011-02-17
Please post the output of these commands.

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

---

### Post by Arminius Chieftan on 2011-02-17
```
root@SERVER1:~# **cat /etc/apt/sources.lis**t
#This file was auto generated at 2011-01-12 0:09:55.
#Please visit http://ubuntu9.com for more infomation.

deb http://64.12.96.232 lucid  main restricted universe multiverse
deb-src http://64.12.96.232 lucid  main restricted universe multiverse
deb http://64.12.96.232 lucid-security  main restricted universe multiverse
deb-src http://64.12.96.232 lucid-security  main restricted universe multiverse
deb http://64.12.96.232 lucid-updates  main restricted universe multiverse
deb-src http://64.12.96.232 lucid-updates  main restricted universe multiverse
deb http://64.12.96.232 lucid-proposed  main restricted universe multiverse
deb-src http://64.12.96.232 lucid-proposed  main restricted universe multiverse
deb http://64.12.96.232 lucid-backports  main restricted universe multiverse
deb-src http://64.12.96.232 lucid-backports  main restricted universe multiverse

```

```
root@SERVER1:~# **ls -l /etc/apt/sources.list.d**
total 0

```

---

### Post by sikander3786 on 2011-02-17
I would recommed to generate a new sources.list and replace your existing one. See here.

[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

---

### Post by Arminius Chieftan on 2011-02-17
THANKS! It worked, but my problem was actually a hardware problem...switched CAT-5 cables and now it hauls @$$.

---

