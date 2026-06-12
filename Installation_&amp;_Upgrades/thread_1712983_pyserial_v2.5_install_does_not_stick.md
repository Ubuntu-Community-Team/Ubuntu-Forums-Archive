---
title: "pyserial v2.5 install does not stick"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by tippyTdizzle on 2011-03-23
I hope this is the right spot for this post! Please forgive if it is not, and advise otherwise.

Having trouble upgrading the python-serial module for my python-2.6. Currently, I have the python-serial 2.3.1 installed (default for ubuntu/debian). When I follow the install instructions from the pyserial site ([http://pyserial.sourceforge.net/pyserial.html#installation](http://pyserial.sourceforge.net/pyserial.html#installation)) the installation does not hold. 

i.e., From terminal, before installation: 
```

dpkg -l | grep -i python-serial
ii  python-serial                                                        2.3-1 
 
```So I know the module 2.3-1 is installed. I then follow the pyserial install instructions (as superuser/sudo), run the same command from the terminal, and get the same print out in return. (i.e. AFTER the 2.5 installation process, dpkg -l still tells me that 2.3-1 is installed). 

How do I get around this? I'm trying to upgrade so the available on-line API (pyserial v2.5) is accurate for development purposes (and for that matter, I can't find the API/documentation for 2.3-1, either, which would also be an acceptable solution, I suppose). 

A few things I have tried already: 
1) upgrade to a newer version of pythonX.Y than python2.6
2) tried the pyserial install process by calling "python2.6" (or matching #) instead of simply "python"
3) first removing the package 2.3-1, and then doing the pyserial 2.5 install process

...

Thanks in advance!

Other Info:
Release: Ubuntu 10.04 LTS
uname -r: 2.6.32-29-generic-pae

---

