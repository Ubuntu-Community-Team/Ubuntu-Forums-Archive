---
title: "Failed to fetch -- 404 not found"
date: 2015-08-23
forum: Installation &amp; Upgrades
---

### Post by Ryryanator on 2015-08-23
Whenever I try to update or install anything, when trying to connect to Ubuntu servers, I always get this error.

```
ryanb@RBLinuxMac:~$ sudo apt-get update
Ign http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com maverick Release.gpg                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://security.ubuntu.com maverick-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://security.ubuntu.com maverick-security/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com maverick Release
Ign http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com maverick-security/restricted Sources/DiffIndex
Ign http://security.ubuntu.com maverick-security/universe Sources
Ign http://security.ubuntu.com maverick-security/multiverse Sources
Ign http://security.ubuntu.com maverick-security/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates Release
Ign http://security.ubuntu.com maverick-security/main Sources
Ign http://security.ubuntu.com maverick-security/restricted Sources
Ign http://extras.ubuntu.com maverick Release                        
Ign http://security.ubuntu.com maverick-security/universe Sources    
Ign http://security.ubuntu.com maverick-security/multiverse Sources
Ign http://security.ubuntu.com maverick-security/main i386 Packages
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://us.archive.ubuntu.com maverick/main Sources
Ign http://us.archive.ubuntu.com maverick/restricted Sources
Ign http://us.archive.ubuntu.com maverick/universe Sources
Ign http://us.archive.ubuntu.com maverick/multiverse Sources         
Ign http://us.archive.ubuntu.com maverick/main i386 Packages         
Ign http://us.archive.ubuntu.com maverick/restricted i386 Packages   
Ign http://us.archive.ubuntu.com maverick/universe i386 Packages     
Ign http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://security.ubuntu.com maverick-security/main Sources
Ign http://extras.ubuntu.com maverick/main Sources                   
Ign http://us.archive.ubuntu.com maverick-updates/main Sources       
Ign http://us.archive.ubuntu.com maverick-updates/restricted Sources
Ign http://us.archive.ubuntu.com maverick-updates/universe Sources
Ign http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Ign http://security.ubuntu.com maverick-security/restricted Sources  
Err http://security.ubuntu.com maverick-security/universe Sources    
  404  Not Found [IP: 91.189.91.15 80]
Err http://security.ubuntu.com maverick-security/multiverse Sources  
  404  Not Found [IP: 91.189.91.15 80]
Ign http://security.ubuntu.com maverick-security/main i386 Packages  
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages
Ign http://us.archive.ubuntu.com maverick/main Sources               
Ign http://us.archive.ubuntu.com maverick/restricted Sources         
Ign http://us.archive.ubuntu.com maverick/universe Sources           
Ign http://us.archive.ubuntu.com maverick/multiverse Sources         
Ign http://us.archive.ubuntu.com maverick/main i386 Packages         
Ign http://us.archive.ubuntu.com maverick/restricted i386 Packages   
Ign http://us.archive.ubuntu.com maverick/universe i386 Packages     
Ign http://us.archive.ubuntu.com maverick/multiverse i386 Packages   
Err http://security.ubuntu.com maverick-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://security.ubuntu.com maverick-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign http://us.archive.ubuntu.com maverick-updates/main Sources
Ign http://us.archive.ubuntu.com maverick-updates/restricted Sources
Ign http://extras.ubuntu.com maverick/main i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/universe Sources
Ign http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Ign http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://security.ubuntu.com maverick-security/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://security.ubuntu.com maverick-security/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err http://security.ubuntu.com maverick-security/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick/main Sources               
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick/restricted Sources         
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick/universe Sources           
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick/multiverse Sources         
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick/main i386 Packages         
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick/restricted i386 Packages   
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick/universe i386 Packages     
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://security.ubuntu.com maverick-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick-updates/main Sources
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick-updates/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Ign http://extras.ubuntu.com maverick/main Sources
Err http://us.archive.ubuntu.com maverick-updates/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign http://extras.ubuntu.com maverick/main i386 Packages
Err http://extras.ubuntu.com maverick/main Sources
  404  Not Found
Err http://extras.ubuntu.com maverick/main i386 Packages
  404  Not Found
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.91.15 80]

```


Note: I am running Ubuntu 10.10 because my Macbook (2,1) has problems reading DVDs and i needed to install Ubuntu that could fit on a CD. I'm currently trying to update it to 12.04 LTS.

If I try to update from the Update Manager I get this error:

```
W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.24 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.24 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.24 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.24 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.24 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.24 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.24 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.24 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.]
```

I've already tried changing the sources from different locations (in the sources.list file) but I always get the same error. This happens if I try to update or install anything.

Any help would be great!

---

### Post by howefield on 2015-08-23
The Maverick repositories have been moved to old-releases.

Have a browse here...  [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Ryryanator on 2015-08-23
awesome. That helps alot. Thanks!

---

### Post by howefield on 2015-08-23
> **Ryryanator said:**
> Note: I am running Ubuntu 10.10 because my Macbook (2,1) has problems reading DVDs and i needed to install Ubuntu that could fit on a CD. I'm currently trying to update it to 12.04 LTS.

Another option might be to install via an iso that would fit a CD, eg the minimal install. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

A modicum of knowledge would be required.

---

### Post by Ryryanator on 2015-08-25
Actually I have tried to install from the minimal iso but I have the same problem, but I'm using the minimal install for 14.04 LTS. So it hasn't reached its end of life so why can't i access the Ubuntu archive?

---

### Post by Bashing-om on 2015-08-25
Ryryanator; Well ...

Can not say - yet - about:
> 
So it hasn't reached its end of life so why can't i access the Ubuntu archive?

Show us what you get from terminal commands:
```

ping -c3 ubuntu.com
sudo apt-get update
sudo apt-get upgrade

```

As the [lace to start a troubleshooting process.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Ryryanator on 2015-08-28
I can't post everything it says because I can't install any web browser so I can't copy.

If I do 'ping -c3 ubuntu.com' i get
```
ping: unknown host ubuntu.com
```

If I do 'sudo apt-get update' I get Err for us.archive.ubuntu.com and security.archive.ubuntu.com
And failed to fetch/could not resolve for the same links.

Sudo apt-get upgrade finds and installs nothing

---

### Post by SeijiSensei on 2015-08-28
You can install from a USB thumbdrive as well as an optical drive.  I'd get a copy of 14.04LTS and follow the instructions here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by Ryryanator on 2015-08-28
I can't boot from USB sticks because I'm on a macbookpro. Can't boot even using refind or refit.

---

### Post by Bashing-om on 2015-08-29
Ryryanator; Well;

I do not know Macs, but :
> 
If I do 'ping -c3 ubuntu.com' i get
Code:
ping: unknown host ubuntu.com

indicates we need to isolate this to a hardware or a configuration issue.

To that end let's do in terminal:
```

ping -c3 127.0.0.1
ping -c3 8.8.8.8.

```

How are you connecting to the internet ? If you have a router between the computer and the modem, can you ping the router ?
Show us:
```

ip route list

```

[INDENT][INDENT]a failure to communicate
[/INDENT][/INDENT]

---

