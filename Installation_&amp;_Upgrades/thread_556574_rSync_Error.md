---
title: "rSync Error"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by Neondog82 on 2007-09-21
Hello everyone. I am having problems installing any kind of packages through Synaptic. This is because I always get errors for rSync.I am currently using Ubuntu 7.04. An example is provided below. I also tried to just mark rSync for reinstalation but that fails for errors also. Would someone be able to help me out with this?

Ubuntu Dialog window after fail:

```
E: rsync: failed in buffer_read(fd)
E: network-manager: failed in buffer_read(fd)
E: network-manager-gnome: dependency problems - leaving unconfigured
```

---

### Post by Pumalite on 2007-09-21
When did the problem start?. What were you doing?.

---

### Post by Neondog82 on 2007-09-21
I was trying to install a program via synaptic when I noticed it. I think it was AirPcap or something. I do know i have tried to install several programs via synaptic and get the same error every time.

---

### Post by Pumalite on 2007-09-21
At the Terminal:

sudo apt-get update

Post the output.

---

### Post by Neondog82 on 2007-09-21
Here is what got:

```
neondog82@Linux:~$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Get:4 http://security.ubuntu.com feisty-security Release [50.9kB]
Hit http://us.archive.ubuntu.com feisty Release    
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty/main Packages                     
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources  
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Get:5 http://security.ubuntu.com feisty-security/main Packages [78.6kB]
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Get:6 http://security.ubuntu.com feisty-security/restricted Packages [6360B]
Get:7 http://security.ubuntu.com feisty-security/main Sources [13.9kB]
Get:8 http://security.ubuntu.com feisty-security/restricted Sources [953B]
Get:9 http://security.ubuntu.com feisty-security/universe Packages [35.6kB]
Get:10 http://security.ubuntu.com feisty-security/universe Sources [4866B]
Get:11 http://security.ubuntu.com feisty-security/multiverse Packages [6101B]
Get:12 http://security.ubuntu.com feisty-security/multiverse Sources [1052B]
Fetched 198kB in 2s (70.0kB/s)                       
Reading package lists... Done
neondog82@Linux:~$ 
```

---

### Post by Pumalite on 2007-09-21
Well, feel happy you have apt-get and Synaptic working. You can install anything you want. Have you tried?.

---

### Post by Neondog82 on 2007-09-21
yes i did try something:

```
neondog82@Linux:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up rsync (2.6.9-3ubuntu1.1) ...
dpkg: error processing rsync (--configure):
 failed in buffer_read(fd): md5hash: Input/output error
Setting up network-manager (0.6.4-6ubuntu7) ...
dpkg: error processing network-manager (--configure):
 failed in buffer_read(fd): md5hash: Input/output error
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (= 0.6.4-6ubuntu7); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rsync
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Pumalite on 2007-09-21
Try: 
sudo apt-get install build-essential

---

### Post by Neondog82 on 2007-09-21
that was what i tried the first time. Do you happen to know how to correct the errors given?

---

### Post by Pumalite on 2007-09-21
Someone will chime in.

---

### Post by Neondog82 on 2007-09-22
Is anyone willing to chime in and help me with this problem?

---

### Post by Pumalite on 2007-09-22
It might be an unresolvable error.

---

### Post by Neondog82 on 2007-09-23
For anyone that reads this, I just did a clean install and the problem went away. Thanks to everyone that helped me out.

---

### Post by Pumalite on 2007-09-23
Good luck with your new install. Sorry that none of my methods worked.

---

