---
title: "nagios- nrpe installation error(configure: error: Cannot find ssl libraries)"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by ankur.trapasiya on 2012-05-08
i have installed nagios and i want to install nrpe. While installing NRPE, when i execute (/home/abc/nrpe/configure)

```
./configure
```

it stops after reaching the following line

```

...
checking for type of socket size... size_t
checking for SSL headers... SSL headers found in /usr
checking for SSL libraries... configure: error: Cannot find ssl libraries

```

I have installed libssl-dev and openssl package as i found them as a solution for this error.

I tried the following option also

```

./configure --with-ssl=/usr/bin/openssl --with-ssl-lib=/usr/lib

```

But the error remains.

What can be the possible solution for this ? I am using ubuntu 12.04 as my operating system. Thanks in advance.

---

### Post by safwanlmu on 2012-05-08
Make a link of the libssl.so.version to libssl.so. I was able to install nrpe using this on oneric.

cd /usr/lib

ln -s libssl.so.0.9.8 libssl.so

---

### Post by RHAnthony on 2012-05-08
I am still having the issue as well after installing libssl-dev, and I also can not see any ssl files in /usr/lib


```
root@aspen:/usr/lib# sudo apt-get install libssl-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libssl-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@aspen:/usr/lib# ls libssl*
ls: cannot access libssl*: No such file or directory
root@aspen:/usr/lib#
```

I then put in this command
 ```
dpkg -L libssl-dev
```
... which showed a libssl.so inside of /usr/lib/x86_64-linux-gnu/

I made a link to it with:
```
ln -s /usr/lib/x86_64-linux-gnu/libssl.so /usr/lib/libssl.so
```

..and then was able to configure and make my nrpe install!

---

### Post by demetriades on 2012-09-14
I was also having this issue, even after creating a link to the libssl.so file in /lib/i386-linux-gnuin /usr/lib. This was quite frustrating!

I've found a solution which worked for me at [http://ubuntuforums.org/showthread.php?p=12238023#post12238023](http://ubuntuforums.org/showthread.php?p=12238023#post12238023)

---

### Post by majordom on 2012-10-04
apt-get install apt-file
apt-file update
apt-file search libssl | grep libssl-dev
with the answer of this last command, you'll find where are located the librairies

for me it was : libssl-dev: /usr/lib/i386-linux-gnu/libssl.so


So the "configure" command is :  ./configure --with-ssl=/usr/bin/openssl --with-ssl-lib=/usr/lib/i386-linux-gnu/


Enjoy:popcorn:

---

### Post by tc7 on 2013-01-01
> **RHAnthony said:**
> I am still having the issue as well after installing libssl-dev, and I also can not see any ssl files in /usr/lib


```
root@aspen:/usr/lib# sudo apt-get install libssl-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libssl-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@aspen:/usr/lib# ls libssl*
ls: cannot access libssl*: No such file or directory
root@aspen:/usr/lib#
```

I then put in this command
 ```
dpkg -L libssl-dev
```
... which showed a libssl.so inside of /usr/lib/x86_64-linux-gnu/

I made a link to it with:
```
ln -s /usr/lib/x86_64-linux-gnu/libssl.so /usr/lib/libssl.so
```

..and then was able to configure and make my nrpe install!

The above worked fine for me on Ubuntu 12.10 x64 - thanks.

---

