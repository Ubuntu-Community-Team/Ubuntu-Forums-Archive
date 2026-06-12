---
title: "Unmet dependencies during upgrade"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by edgreenberg on 2012-06-07
This is on a Hardy (8.04) box. Two of them, out of 50 similar boxen, the rest upgraded fine. 


The system wants to upgrade: 
```
  libsnmp-base libsnmp15 libssl0.9.8 libxml2 nagios-nrpe-server openssl 
  python-libxml2 snmp snmpd sudo 
```

but fails with: 

```
  The following packages have unmet dependencies:
  bind9: Depends: libbind9-30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: libdns36 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: libisc35 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: libisccc30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: libisccfg30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: liblwres30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
  bind9-host: Depends: libbind9-30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
              Depends: libdns36 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
              Depends: libisc35 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
              Depends: libisccfg30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
              Depends: liblwres30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
  dnsutils: Depends: libbind9-30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
            Depends: libdns36 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
            Depends: libisc35 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
            Depends: libisccfg30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
            Depends: liblwres30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
```

For all these packages, dpkg tells me that I have newer versions (1.9.7.3.dfsg-1ubuntu2.4)

What might be wrong?

Thanks,
Ed Greenberg

---

### Post by ptn107 on 2012-06-07
Post your sources.list
```
cat /etc/apt/sources.list
```

Something is wrong.  It wants to install versions from 8.04 LTS but you've got versions installed from 11.04.

---

### Post by edgreenberg on 2012-06-07
Here is my sources.list:
```

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe

deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe

```

And here is the output from aptitude update:
```
root@xxx:/etc/apt# aptitude update
Get:1 http://archive.ubuntu.com hardy Release.gpg [189B]
Get:2 http://security.ubuntu.com hardy-security Release.gpg [198B]
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Get:3 http://archive.ubuntu.com hardy-updates Release.gpg [198B]
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Get:4 http://security.ubuntu.com hardy-security Release [65.9kB]
Get:5 http://archive.ubuntu.com hardy Release [65.9kB]
Get:6 http://archive.ubuntu.com hardy-updates Release [65.9kB]
Get:7 http://archive.ubuntu.com hardy/main Packages [1173kB]                    
Get:8 http://security.ubuntu.com hardy-security/main Packages [302kB]
Get:9 http://security.ubuntu.com hardy-security/restricted Packages [11.1kB] 
Get:10 http://security.ubuntu.com hardy-security/universe Packages [141kB]   
Get:11 http://security.ubuntu.com hardy-security/main Sources [117kB]           
Get:12 http://security.ubuntu.com hardy-security/restricted Sources [1262B]     
Get:13 http://security.ubuntu.com hardy-security/universe Sources [30.1kB]   
Get:14 http://archive.ubuntu.com hardy/restricted Packages [6397B]           
Get:15 http://archive.ubuntu.com hardy/universe Packages [4254kB]
Get:16 http://archive.ubuntu.com hardy/main Sources [338kB]    
Get:17 http://archive.ubuntu.com hardy/restricted Sources [1488B]
Get:18 http://archive.ubuntu.com hardy/universe Sources [1323kB]
Get:19 http://archive.ubuntu.com hardy-updates/main Packages [516kB]
Get:20 http://archive.ubuntu.com hardy-updates/restricted Packages [11.1kB]
Get:21 http://archive.ubuntu.com hardy-updates/universe Packages [258kB]
Get:22 http://archive.ubuntu.com hardy-updates/main Sources [189kB]
Get:23 http://archive.ubuntu.com hardy-updates/restricted Sources [1262B]
Get:24 http://archive.ubuntu.com hardy-updates/universe Sources [65.8kB]
Fetched 8937kB in 7s (1275kB/s)                                                 
Reading package lists... Done

```

and finally the complete run of aptitude upgrade:
```

W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have unmet dependencies:
  bind9: Depends: libbind9-30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: libdns36 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: libisc35 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: libisccc30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: libisccfg30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
         Depends: liblwres30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
  bind9-host: Depends: libbind9-30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
              Depends: libdns36 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
              Depends: libisc35 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
              Depends: libisccfg30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
              Depends: liblwres30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
  dnsutils: Depends: libbind9-30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
            Depends: libdns36 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
            Depends: libisc35 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
            Depends: libisccfg30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
            Depends: liblwres30 (= 1:9.4.2.dfsg.P2-2ubuntu0.10) but it is not installable
root@valleylists:/etc/apt# 


```

---

### Post by edgreenberg on 2012-06-07
On rereading your msg... I'll add that this IS a Hardy machine.

---

### Post by ptn107 on 2012-06-12
Sorry for the delay, I was out of town for 5 days.  You can try to downgrade the packages manually to what aptitude expects them to be (easier to copy/paste):

```
sudo apt-get install bind9=1:9.4.2.dfsg.P2-2ubuntu0.10 bind9-host=1:9.4.2.dfsg.P2-2ubuntu0.10 dnsutils=1:9.4.2.dfsg.P2-2ubuntu0.10 libbind9-30=1:9.4.2.dfsg.P2-2ubuntu0.10 libdns36=1:9.4.2.dfsg.P2-2ubuntu0.10 libisc35=1:9.4.2.dfsg.P2-2ubuntu0.10 libisccc30=1:9.4.2.dfsg.P2-2ubuntu0.10 libisccfg30=1:9.4.2.dfsg.P2-2ubuntu0.10 liblwres30=1:9.4.2.dfsg.P2-2ubuntu0.10
```

Let me know what happens.

---

### Post by edgreenberg on 2012-08-07
My apologies for not responding. The problem is solved, per your suggestion.

---

