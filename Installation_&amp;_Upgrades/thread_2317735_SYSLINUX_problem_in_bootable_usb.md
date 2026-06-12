---
title: "SYSLINUX problem in bootable usb"
date: 2016-03-19
forum: Installation &amp; Upgrades
---

### Post by v6rg2 on 2016-03-19
Hi
I have a problem with installing ubuntu 15.10
I made a bootable usb with startup disk creator in another ubuntu (15.10) and then try to boot in ASUS laptop but I got this error:
```
SYSLINUX 6.03 EDD 20150813 Copyright (C) 1994-2014 H. Peter Anvin et al
Boot error
```

what should I do?

---

### Post by sudodus on 2016-03-19
Welcome to the Ubuntu Forums :-)

It is a known bug. There will be a new and much more robust version of the Ubuntu Startup Disk Creator in the next version of Ubuntu, 16.04 LTS, which will be released in April. But now I suggest that you use another tool to make the USB drive an Ubuntu boot drive. I suggest that you try ***mkusb***, according to this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

You run standard Ubuntu, so you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

You can read more about booting from a USB drive at the following link

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by v6rg2 on 2016-03-19
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```




Thanks  :)
But Icant install mkusb:

```
sudo add-apt-repository universe  # only for standard Ubuntu
[sudo] password for v6rg: 
'universe' distribution component is already enabled for all sources.
v6rg@v6rg:~$ sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
 
 More info: https://launchpad.net/~mkusb/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpcxshgccw/secring.gpg' created
gpg: keyring `/tmp/tmpcxshgccw/pubring.gpg' created
gpg: requesting key 54B8C8AC from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpcxshgccw/trustdb.gpg: trustdb created
gpg: key 54B8C8AC: public key "Launchpad PPA for MKUSB" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
v6rg@v6rg:~$ sudo apt-get update
Hit http://ir.archive.ubuntu.com wily InRelease
Get:1 http://ir.archive.ubuntu.com wily-updates InRelease [65.9 kB]            
Get:2 http://security.ubuntu.com wily-security InRelease [65.9 kB]             
Get:3 http://ppa.launchpad.net wily InRelease [15.4 kB]                        
Ign http://extras.ubuntu.com wily InRelease                                    
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net wily InRelease                                    
Hit http://ir.archive.ubuntu.com wily-backports InRelease                      
Get:4 http://dl.google.com stable InRelease [1,540 B]                          
100% [4 InRelease gpgv 1,540 B] [Waiting for headers] [Waiting for headers] [WaSplitting up /var/lib/apt/lists/partial/dl.google.com_linux_chrome_deb_dists_stabIgn http://dl.google.com stable InRelease                                      
W: GPG error: http://ppa.launchpad.net wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6A9653F936FD5529
E: GPG error: http://dl.google.com stable InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
v6rg@v6rg:~$ sudo apt-get install mkusb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mkusb
v6rg@v6rg:~$ sudo add-apt-repository universe
'universe' distribution component is already enabled for all sources.
v6rg@v6rg:~$ sudo add-apt-repository ppa:mkusb/ppa
 
 More info: https://launchpad.net/~mkusb/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp4495wb5u/secring.gpg' created
gpg: keyring `/tmp/tmp4495wb5u/pubring.gpg' created
gpg: requesting key 54B8C8AC from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp4495wb5u/trustdb.gpg: trustdb created
gpg: key 54B8C8AC: public key "Launchpad PPA for MKUSB" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
v6rg@v6rg:~$ sudo apt-get update
Hit http://ir.archive.ubuntu.com wily InRelease
Hit http://ir.archive.ubuntu.com wily-updates InRelease                        
Hit http://ir.archive.ubuntu.com wily-backports InRelease                      
Ign http://extras.ubuntu.com wily InRelease                                    
Get:1 http://ppa.launchpad.net wily InRelease [15.4 kB]                        
Hit http://security.ubuntu.com wily-security InRelease                         
Ign http://ppa.launchpad.net wily InRelease                                    
Get:2 http://ir.archive.ubuntu.com wily/main Sources [1,118 kB]                
Ign http://extras.ubuntu.com wily Release.gpg                                  
Ign http://ppa.launchpad.net wily InRelease                                    
Get:3 http://security.ubuntu.com wily-security/main Sources [40.9 kB]          
Ign http://extras.ubuntu.com wily Release                                      
Get:4 http://dl.google.com stable InRelease [1,540 B]                          
94% [4 InRelease gpgv 1,540 B] [2 Sources 1,062 kB/1,118 kB 95%] [3 Sources 29.Splitting up /var/lib/apt/lists/partial/dl.google.com_linux_chrome_deb_dists_stabHit http://ppa.launchpad.net wily InRelease                                    
Ign http://dl.google.com stable InRelease                                      
W: GPG error: http://ppa.launchpad.net wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6A9653F936FD5529
E: GPG error: http://dl.google.com stable InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
v6rg@v6rg:~$ sudo apt-get install mkusb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mkusb
v6rg@v6rg:~$ 

```


And, I used UNetbootin and have same error.   :(

---

### Post by sudodus on 2016-03-19
Maybe it is a temporary error with Launchpad, that you cannot install from the PPA. I notice that I cannot do it either, so I will look into this problem now.

There is an alternative way to install mkusb, which is described at the following page:

[mkusb/gui#from_phillw.net](https://help.ubuntu.com/community/mkusb/gui#from_phillw.net)

Good luck :-)

---

### Post by sudodus on 2016-03-19
Now I can install from the PPA. Maybe it was a temporarary error at the Launchpad server or some other internet error.

Please try again, maybe it will be enough with the two last commands.

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
[B]sudo apt-get update
sudo apt-get install mkusb[/B]
```

---

### Post by v6rg2 on 2016-03-19
> **sudodus said:**
> Maybe it is a temporary error with Launchpad, that you cannot install from the PPA. I notice that I cannot do it either, so I will look into this problem now.

There is an alternative way to install mkusb, which is described at the following page:

[mkusb/gui#from_phillw.net]("https://help.ubuntu.com/community/mkusb/gui#from_phillw.net")

Good luck :-)

Thanks a lot. Solved.  Now I have a new question:
[http://ubuntuforums.org/showthread.php?t=2317745](http://ubuntuforums.org/showthread.php?t=2317745)
:D

---

### Post by sudodus on 2016-03-19
I'm glad it worked for you :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. It will help other people find your solution.

... and now I will look at your new thread.

---

