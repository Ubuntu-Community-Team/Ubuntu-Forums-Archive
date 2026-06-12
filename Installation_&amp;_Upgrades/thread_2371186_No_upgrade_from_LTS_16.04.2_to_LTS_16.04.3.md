---
title: "No upgrade from LTS 16.04.2 to LTS 16.04.3"
date: 2017-09-12
forum: Installation &amp; Upgrades
---

### Post by michael-hoeller on 2017-09-12
Hello 
my system seems to be updated according to the console messages, please see below. Butt any attempt with apt-get update, apt-get upgrade or apt-get distr-upgrade  results in 0 packages to be updated. And I am still on 16.04.2

How can I upgrade to LTS 16.04.3 ?


```
root@p1sr1:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```

```
root@p1sr1:~# uname -a
Linux p1sr1 4.10.0-33-generic #37~16.04.1-Ubuntu SMP Fri Aug 11 14:03:33 UTC 2017 i686 i686 i686 GNU/Linux

```
Thanks a lot for any hint!

---

### Post by deadflowr on 2017-09-12
You're currently updated to 16.04.3 based on the kernel
(4.10 kernels are part of the 16.04.3 base)

I'd look at what the base-files installed is, as that is what gives the lsb_release output
```
apt-cache policy base-files
```

also are any odd errors showing in the apt-get update output?

---

### Post by michael-hoeller on 2017-09-12
Hello

I have no errors at all. Here is the output of ```
apt-cache policy base-files
``` unfortunately it does not tell me more :-( 

```
base-files:
  Installiert:           9.4ubuntu4.4
  Installationskandidat: 9.4ubuntu4.4
  Versionstabelle:
 *** 9.4ubuntu4.4 100
        100 /var/lib/dpkg/status
     9.4ubuntu4 500
        500 http://de.archive.ubuntu.com/ubuntu xenial/main i386 Packages
root@p1sr1:~#

```

---

### Post by deadflowr on 2017-09-12
You need to enable -updates in your sources.list file
Post the output of
```
cat /etc/apt/sources.list
```
to see where that currently stands.

The current base-files is 9.4ubuntu4.5 which is available in the xenial-updates repository.

---

### Post by michael-hoeller on 2017-09-12
Hello 

this is my sources.list, I removed all comments but nothing else:
```
deb http://de.archive.ubuntu.com/ubuntu/ xenial main restricted
deb http://de.archive.ubuntu.com/ubuntu/ xenial universe
deb http://de.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner
deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse

```

I do not see any -update, so there can be something...  How would be the correct version?

Thanks a lot
Michael

---

### Post by deadflowr on 2017-09-12
Did any of the commented lines look like this
```
#deb http://de.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
```
maybe?
if so remove the #,
or else perhaps try adding the line(s) yourself to the file
Typically 3 lines like so
```
deb http://de.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb http://de.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb http://de.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
```
then run the update/upgrade command and see if lsb_release -a shows as 16.04.3 now.

---

### Post by michael-hoeller on 2017-09-12
Thank you very much! 
I added the last mentioned lines and got all updates which where missing!

Great! Thanks!
Michael

---

