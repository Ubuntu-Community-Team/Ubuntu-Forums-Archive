---
title: "apt-get update is ignoring 3rd party repositories"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by tjones00 on 2010-08-10
Something weird happening today with a new 10.04 LTS server install.

apt-get update is ignoring 3rd party repositories

```
xbmc@xbmc-HTPC:~$ sudo add-apt-repository ppa:team-xbmc-svn
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A292248FCB9CFB8689A30B7A2BBD133164234534
gpg: requesting key 64234534 from hkp server keyserver.ubuntu.com
gpg: key 64234534: public key "Launchpad PPA for XBMC SVN BUILDING" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
xbmc@xbmc-HTPC:~$ sudo apt-get update
Get:1 http://ppa.launchpad.net lucid Release.gpg [307B]
Ign http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:2 http://ppa.launchpad.net lucid Release [57.3kB]
Hit http://security.ubuntu.com lucid-security Release                      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com lucid-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release       
Get:4 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]              
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Get:5 http://ppa.launchpad.net lucid/main Packages [14B]                       
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Get:6 http://us.archive.ubuntu.com lucid-updates/main Packages [275kB]
Get:7 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,252B]
Get:8 http://us.archive.ubuntu.com lucid-updates/main Sources [99.6kB]
Get:9 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,292B]
Get:10 http://us.archive.ubuntu.com lucid-updates/universe Packages [88.9kB]
Get:11 http://us.archive.ubuntu.com lucid-updates/universe Sources [29.6kB]
Get:12 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [3,771B]
Get:13 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [1,499B]
Fetched 606kB in 3s (169kB/s)                            
Reading package lists... Done
xbmc@xbmc-HTPC:~$ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024R/64234534 2009-01-20
uid                  Launchpad PPA for XBMC SVN BUILDING

```I've tried this with multiple repositories and it behaves the same. It's not just xbmc svn.

[B]Ign [http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/) lucid/main Translation-en_US
[/B]
To make sure it wasn't something I did mucking around with the install the above output was given by a fresh 10.04 LTS min network install with only basic server and openssh. Those were the first commands I entered upon logging in.

**edit actually I installed 
python-software-properties
[FONT=Verdana]
before adding the repository
[/FONT]  It was working fine yesterday on the exact same install. Did something change in the ubuntu repositories overnight? My internet is fine no firewalls or proxies just 1 router and I haven't changed any settings. I can download with wget and this was a network install.

```
xbmc@xbmc-HTPC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 70:71:bc:44:eb:11  
          inet addr:192.168.1.197  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:fe44:eb11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:971322 (971.3 KB)  TX bytes:91025 (91.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```Is there someway I can force an update for a 3rd party repository? I've tried adding repositories directly to /etc/apt/sources.list it didn't make a difference.


**edit
I just tried adding the same repository to my desktop pc as well separate install separate machine same error, while checking software sources in gnome nothing seems out of the ordinary. My desktop was updated today via the update manager.

---

### Post by tjones00 on 2010-08-10
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

```
xbmc@xbmc-HTPC:/etc/apt/sources.list.d$ sudo add-apt-repository ppa:kernel-ppa/ppa
[sudo] password for xbmc: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 800AA67AE64A6D9E1859C561A8267963484B044F
gpg: requesting key 484B044F from hkp server keyserver.ubuntu.com
gpg: key 484B044F: public key "Launchpad PPA for Ubuntu Kernel PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
xbmc@xbmc-HTPC:/etc/apt/sources.list.d$ sudo apt-get update
Get:1 http://ppa.launchpad.net lucid Release.gpg [307B]
Hit http://security.ubuntu.com lucid-security Release.gpg                     
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu/ lucid/main Translation-en_US
Get:2 http://ppa.launchpad.net lucid Release [57.3kB]
Hit http://security.ubuntu.com lucid-security Release                      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                             
Hit http://security.ubuntu.com lucid-security/main Packages                                      
Hit http://us.archive.ubuntu.com lucid-updates Release                       
Hit http://security.ubuntu.com lucid-security/restricted Packages            
Hit http://security.ubuntu.com lucid-security/main Sources                   
Hit http://security.ubuntu.com lucid-security/restricted Sources             
Hit http://us.archive.ubuntu.com lucid/main Packages                         
Hit http://security.ubuntu.com lucid-security/universe Packages              
Hit http://security.ubuntu.com lucid-security/universe Sources               
Hit http://us.archive.ubuntu.com lucid/restricted Packages                   
Hit http://us.archive.ubuntu.com lucid/main Sources                          
Hit http://us.archive.ubuntu.com lucid/restricted Sources                    
Hit http://us.archive.ubuntu.com lucid/universe Packages                     
Hit http://us.archive.ubuntu.com lucid/universe Sources                      
Hit http://ppa.launchpad.net lucid Release                                   
Hit http://security.ubuntu.com lucid-security/multiverse Packages      
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://us.archive.ubuntu.com lucid/multiverse Packages           
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Get:3 http://ppa.launchpad.net lucid/main Packages [4,422B]
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources      
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://ppa.launchpad.net lucid/main Packages
Fetched 62.0kB in 1s (37.5kB/s)
Reading package lists... Done
xbmc@xbmc-HTPC:/etc/apt/sources.list.d$ 

```


Maybe all the launchpad ppas are broken?

---

### Post by drs305 on 2010-08-10
I sometimes get the translation error and clear it with the following command. When I rerun apt-get update it eliminates the errors. Don't think that would affect only the ppa's but you could give it a try.
```

unset LANG LANGUAGE

```

---

### Post by tjones00 on 2010-08-10
```
xbmc@xbmc-HTPC:/etc/apt/sources.list.d$ unset LANG LANGUAGE
xbmc@xbmc-HTPC:/etc/apt/sources.list.d$ sudo apt-get update
Hit http://us.archive.ubuntu.com lucid Release.gpg
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Hit http://security.ubuntu.com lucid-security Release.gpg
Hit http://ppa.launchpad.net lucid Release.gpg 
Hit http://ppa.launchpad.net lucid Release.gpg 
Hit http://security.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid Release 
Hit http://ppa.launchpad.net lucid Release     
Hit http://us.archive.ubuntu.com lucid-updates Release                                     
Hit http://ppa.launchpad.net lucid Release                           
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://ppa.launchpad.net lucid/main Packages                                           
Hit http://us.archive.ubuntu.com lucid/main Packages                 
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources           
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://us.archive.ubuntu.com lucid/multiverse Packages           
Hit http://us.archive.ubuntu.com lucid/multiverse Sources            
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024R/64234534 2009-01-20
uid                  Launchpad PPA for XBMC SVN BUILDING

pub   1024R/484B044F 2009-01-20
uid                  Launchpad PPA for Ubuntu Kernel PPA


```
```

xbmc@xbmc-HTPC:/etc/apt/sources.list.d$ sudo apt-get install xbmc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xbmc

```and inside /etc/apt/sources.list.d/team-xbmc-svn-ppa-lucid.list

```
deb http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu lucid main
```it's uncommented

So nobody else is getting an error like this today? I have it on both machines and my desktop was installed months ago.

Maybe it's just a display error and there is something wrong with the xbmc svn repo I've tried both of them though the standard and the svn.

bleh

I'm gonna go check the packages manually in that repo

---

### Post by tjones00 on 2010-08-10
Yeah it seems packages just aren't there it's an xbmc issue. It had me freaking out though when I saw the update lines I just never tried installing a package from a ppa besides xbmc.....doh.

Well at least I figured out how to add a kernel ppa.

---

