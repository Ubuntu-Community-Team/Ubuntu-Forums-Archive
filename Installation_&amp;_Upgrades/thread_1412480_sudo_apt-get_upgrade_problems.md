---
title: "sudo apt-get upgrade problems"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by dencamel on 2010-02-21
Hello I did a update yesterday and by doing the upgrade I receive the following:

```
Setting up g++ (4:4.4.1-1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing g++ (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.3.1); however:
  Package g++ is not configured yet.
dpkg: error processing build-essential (--configure):
 dependency problems - leaving unconfigured
Setting up cvs (1:1.12.13-12ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing cvs (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 g++
 build-essential
 cvs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anybody any idea on how to solve this?
I've already tried to apt-get -f install and clean but I always receive this error...

---

### Post by Barriehie on 2010-02-21
Try:
```

sudo dpkg-reconfigure g++
```
and see if that moves you any farther along.

---

### Post by dencamel on 2010-02-21
> **Barriehie said:**
> Try:
```

sudo dpkg-reconfigure g++
```and see if that moves you any farther along.


Thanks for your reply... I executed the statement and this is the output:
/usr/sbin/dpkg-reconfigure: g++ is broken or not fully installed

---

### Post by Barriehie on 2010-02-21
I'ld purge both g++ and build-essential and then re-initiate installing g++.  At that point build-essential should be pulled in.

---

### Post by dencamel on 2010-02-21
> **Barriehie said:**
> I'ld purge both g++ and build-essential and then re-initiate installing g++.  At that point build-essential should be pulled in.


I've tried sudo apt-get purge g++ but it returns the same error, here's the output:

> 
sudo apt-get purge g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  build-essential* g++*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 90.1kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 184242 files and directories currently installed.)
Removing build-essential ...
Removing g++ ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing g++ (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 g++
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by Barriehie on 2010-02-21
I hate when that happens!  Try it with **sudo dpkg -P g++**

---

### Post by Barriehie on 2010-02-21
If that doesn't work you can either wait for more posters or manually uninstall/purge, not recommended but doable.

---

### Post by Soul-Sing on 2010-02-21
```
sudo -i
```
or ```
gksudo nautilus
```
navigate via nautilus to /var/lib/dpkg/info
remove [COLOR="Red"]g++[/COLOR]
close nautlus

```
sudo apt-get update
```

---

### Post by Barriehie on 2010-02-21
Good to know leoquant!

---

### Post by dencamel on 2010-02-22
> **Barriehie said:**
> Good to know leoquant!

Thanks for the replies... 
I did as you told me and removed the g++ files from the info folder:
g++.list, g++.postinst, g++.prerm, g++-4.4.list and g++-4.4.md5sums

Then I did a sudo apt-get update and then an sudo apt-get upgrade and now I have the following error during the upgrade:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cvs (1:1.12.13-12ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing cvs (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 cvs
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

any idea?

---

