---
title: "clamav installion of PHP ClamAV Lib (depend stopped it )"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by Zmotters on 2011-05-31
hi all,

i am semi new to UBUNTU worked a bit with it in the passed on vps and that.

but i am currentaly tring to make a module for *Zpanel*

i am making an anti virus module and am going to be using clamav. up to now everything has been going smoothly but i have hit  massive problem 

i am tring to do this 

```

sudo apt-get install php5-clamavlib

``` and i get this in return 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 php5-clamavlib : Depends: phpapi-20060613+lfs
E: Broken packages


```i dont get any install. 
and the information i have collect from people say that and install should not be stopped becuase of an depend


so as any one who is semi new would do i then tried installing the depend
```
sudo apt-get install phpapi-20060613+lfs

```and i get this in return 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package phpapi-20060613+lfs is a virtual package provided by:
  php5-cli 5.2.4-2ubuntu5.17 [Not candidate version]
  php5-cgi 5.2.4-2ubuntu5.17 [Not candidate version]
  libapache2-mod-php5 5.2.4-2ubuntu5.17 [Not candidate version]

E: Package 'phpapi-20060613+lfs' has no installation candidate                 

```so it look like problem after problem 


does any one know why i can not install php5-clamavlib

thanks every one :D

i have UBUNTU 11.04 desktop (with zpanel installed on it)


*zpanel an open source web hosting panel for windows and NOW LINUX (zpanel has just been release on UBUNTU ONLY :o) :D.

i allways try to make my post as detailed as possable. but i am sorry if i have missed somehting out :p

---

### Post by Zmotters on 2011-06-01
does any one know how to solve my problem? or how to get round the depend issue 

thanks alot :D

---

