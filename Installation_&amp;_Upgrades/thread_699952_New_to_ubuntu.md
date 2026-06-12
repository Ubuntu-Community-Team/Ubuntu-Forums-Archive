---
title: "New to ubuntu"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by glmoring on 2008-02-17
Hello, I'm a new Ubuntu user. And I am sad to say that I am already having problems. First I tried to download GCC. After spending two days with no success, I gave up. I have very little programming knowledge. I wanted to learn C and C+ that is the reason for downloading GCC. 


Anyway, I am now receiving the following errors:


Errors were encountered while processing:

 amavisd-new

 amavisd-new-milter

 emdebian-tools

E: Sub-process /usr/bin/dpkg returned an error code (1)




The entire script reads:



Reading package lists... Done

Building dependency tree       

Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

3 not fully installed or removed.

Need to get 0B of archives.

After unpacking 0B of additional disk space will be used.

Setting up amavisd-new (1:2.4.2-6.2ubuntu1) ...

Creating/updating amavis user account...

Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory

  The value of variable $myhostname is "gary-desktop", but should have been

  a fully qualified domain name; perhaps uname(3) did not provide such.

  You must explicitly assign a FQDN of this host to variable $myhostname

  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 

  network name!

(failed).

invoke-rc.d: initscript amavis, action "start" failed.

dpkg: error processing amavisd-new (--configure):

 subprocess post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of amavisd-new-milter:

 amavisd-new-milter depends on amavisd-new (= 1:2.4.2-6.2ubuntu1); however:

  Package amavisd-new is not configured yet.

dpkg: error processing amavisd-new-milter (--configure):

 dependency problems - leaving unconfigured

Setting up emdebian-tools (0.2.0) ...

Unable to determine apt-cache policy for Debian main! at /var/lib/dpkg/info/emdebian-tools.postinst line 132.

dpkg: error processing emdebian-tools (--configure):

 subprocess post-installation script returned error exit status 255

Errors were encountered while processing:

 amavisd-new

 amavisd-new-milter

 emdebian-tools

E: Sub-process /usr/bin/dpkg returned an error code (1)



Thank you in advance for any help.

---

### Post by zvacet on 2008-02-18
Programs>accessories>terminal

```
sudo dpkg --configure -a
```

---

### Post by glmoring on 2008-02-18
Thank you for your help. But I'm still getting the following error:


Errors were encountered while processing:

amavisd-new

amavisd-new-milter

emdebian-tools



[SIZE="3"][SIZE="5"]***Thanks again for your help.***[/SIZE][/SIZE]

---

### Post by zvacet on 2008-02-18
```
sudo apt-get -f install
```

---

