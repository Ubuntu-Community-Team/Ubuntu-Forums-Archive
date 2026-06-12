---
title: "New python?"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by camper365 on 2009-07-24
I ran an update, and it installed the new python version, however, when it went to configure it, somewhere in that failed. Now, whenever I run any instance of apt (apt-get, update-manager, aptitude, etc.) the following error occurs:

> 
aaron@truman:~$ sudo aptitude -v full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  libiw29 linux-headers-2.6.31-4 linux-headers-2.6.31-4-generic 
  linux-image-2.6.31-4-generic linux-libc-dev linux-source-2.6.31 
  wireless-tools 
The following partially installed packages will be configured:
  libpython2.6 python2.6 python2.6-minimal 
7 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/104MB of archives. After unpacking 2191kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Setting up python2.6-minimal (2.6.2-0ubuntu3) ...
update-binfmts: /var/lib/binfmts/cli corrupt: out of binfmt data reading
package 
dpkg: error processing python2.6-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.6-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.6-minimal (2.6.2-0ubuntu3) ...
update-binfmts: /var/lib/binfmts/cli corrupt: out of binfmt data reading
package 
dpkg: error processing python2.6-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python2.6:
 python2.6 depends on python2.6-minimal (= 2.6.2-0ubuntu3); however:
  Package python2.6-minimal is not configured yet.
dpkg: error processing python2.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython2.6:
 libpython2.6 depends on python2.6 (= 2.6.2-0ubuntu3); however:
  Package python2.6 is not configured yet.
dpkg: error processing libpython2.6 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.6-minimal
 python2.6
 libpython2.6
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

Current status: 0 broken [+0], 7 updates [+0], 18464 new [+0].
aaron@truman:~$ 



Is anyone else experiencing this problem or is it just a problem on my system? If anyone else is experiencing this problem I will report a bug, but if not I would like to fix it.

---

### Post by wayne_cat on 2009-07-24
apt-get dist-upgrade gave me a clean python 2.6 installation:

```
root@macbook:~# dpkg -l |grep python2.6
ii  libpython2.6                                   2.6.2-0ubuntu3                            Shared Python runtime library (version 2.6)
ii  python2.6                                      2.6.2-0ubuntu3                            An interactive high-level object-oriented language (ver
ii  python2.6-minimal                              2.6.2-0ubuntu3                            A minimal subset of the Python language (version 2.6)
root@macbook:~# 

```

---

### Post by xebian on 2009-07-24
I thought python is now 3.1?

---

### Post by wayne_cat on 2009-07-24
> **xebian said:**
> I thought python is now 3.1?

not yet :biggrin:

```
root@macbook:/usr/src# python --version
Python 2.6.2+
root@macbook:/usr/src# 

```

---

### Post by xebian on 2009-07-24
> **wayne_cat said:**
> not yet :biggrin:

```
root@macbook:/usr/src# python --version
Python 2.6.2+
root@macbook:/usr/src# 

```
```

ii  python2.6                          2.6.2-0ubuntu3                            An interactive high-level object-oriented la
ii  python2.6-minimal                  2.6.2-0ubuntu3                            A minimal subset of the Python language (ver
ii  python3.1                          3.1-0ubuntu2                              An interactive high-level object-oriented la
ii  python3.1-minimal                  3.1-0ubuntu2                              A minimal subset of the Python language (ver
```

---

### Post by wayne_cat on 2009-07-24
Python 3.1 final was released on June 27th, 2009. ;)

---

### Post by xebian on 2009-07-24
> **wayne_cat said:**
> Python 3.1 final was released on June 27th, 2009. ;)

That was more than 48 minutes ago when you said "not yet"
:mrgreen:

---

### Post by wayne_cat on 2009-07-24
> **xebian said:**
> That was more than 48 minutes ago when you said "not yet"
:mrgreen:

the release notes:

[http://www.python.org/download/releases/3.1/](http://www.python.org/download/releases/3.1/)

We are talking about Alpha 3 ... not Alpha 4 ... no ... just kidding :biggrin:

---

### Post by camper365 on 2009-07-25
Here's the output of sudo apt-get dist-upgrade:

> 
aaron@truman:~$ sudo apt-get dist-upgrade
[sudo] password for aaron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libiw29 linux-headers-2.6.31-4 linux-headers-2.6.31-4-generic
  linux-image-2.6.31-4-generic linux-libc-dev linux-source-2.6.31
  wireless-tools
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/104MB of archives.
After this operation, 2191kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python2.6-minimal (2.6.2-0ubuntu3) ...
update-binfmts: /var/lib/binfmts/cli corrupt: out of binfmt data reading
package 
dpkg: error processing python2.6-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
aaron@truman:~$ 


---

### Post by Meson on 2009-07-25
Python 3 is not ready to be used.

---

### Post by camper365 on 2009-07-25
I was able to use ```
dpkg -i 
``` to install the upgrades, however, it looks like there is a problem installing python2.6-minimal and that is making it so that python2.6 can't be configured and therefore libpython2.6 can't be configured. It looks like the problem is right here: ```
update-binfmts: /var/lib/binfmts/cli corrupt: out of binfmt data reading
package 

```
however, I have no clue what that means :/ so I can't fix it. Any help would be appreciated.

---

### Post by camper365 on 2009-07-25
The problem happened when I tried to install the new dpkg. I had to remove any 0 byte files in that directory or it wouldn't install. That was the only 0 byte file there was. After I finished upgrading, I used ```
sudo touch /var/lib/binfmts/cli
``` and apparently it didn't do everything it needed to do.

---

### Post by camper365 on 2009-07-25
If someone could post the contents of their /var/lib/binfmts/cli that would be helpful. I'll use that and see if it installs properly

---

### Post by camper365 on 2009-07-25
Never mind, I removed the /var/lib/binfmts/cli and it worked beautifully.

---

### Post by taavikko on 2009-07-25
nm...

---

### Post by phoogkamer on 2009-07-26
Removing /var/lib/binfmts/cli worked for me too. Content of cli was:
cat /var/lib/binfmts/cli 
Package: python-telepathy
Status: install ok half-configured

---

