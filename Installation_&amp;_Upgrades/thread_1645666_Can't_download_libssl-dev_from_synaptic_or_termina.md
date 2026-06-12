---
title: "Can't download libssl-dev from synaptic or terminal?"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by 3rr0r on 2010-12-14
Hello all.  I'm trying to install libssl-dev onto my Ubuntu 10.04 system.

When I run sudo aptitude install in a terminal, I get the following:
```
user@ubuntu:/etc/apt$ sudo nano sources.list
[sudo] password for user: 
Sorry, try again.
[sudo] password for user: 
user@ubuntu:/etc/apt$ sudo aptitude install libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  libssl-dev 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,011kB of archives. After unpacking 5,857kB will be used.
Writing extended state information... Done
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libssl-dev 0.9.8k-7ubuntu8.3
  404  Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/main libssl-dev 0.9.8k-7ubuntu8.3
  404  Not Found [IP: 91.189.92.166 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8k-7ubuntu8.3_i386.deb: 404  Not Found [IP: 91.189.92.166 80]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```Then I tried it through synaptic (see attachments) and still nothing.

What am I doing wrong?  In my sources.list file, I did make sure to append deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main 

Any help to resolving this is much appreciated!

---

### Post by 3rr0r on 2010-12-15
bump

---

### Post by sikander3786 on 2010-12-15
Try changing your update server from System > Administrations > Software Sources and select the Main Server. Try again. If unsuccessful, post the output of this command.

```
cat /etc/apt/sources.list
```

---

### Post by 3rr0r on 2010-12-15
> **sikander3786 said:**
> Try changing your update server from System > Administrations > Software Sources and select the Main Server. Try again. If unsuccessful, post the output of this command.

```
cat /etc/apt/sources.list
```


OMG it worked!!!  Thank you so much.  I have been dealing with this issue for weeks now.

---

