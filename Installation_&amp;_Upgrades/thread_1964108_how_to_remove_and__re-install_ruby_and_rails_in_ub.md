---
title: "how to remove and  re-install ruby and rails in ubuntu 11.10"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by blaablaa on 2012-04-23
I did some wrong stuff with installation . Earlier i installed ruby 1.9.0, rubygems ( rails ) and rvm from source code . There was some unknown problem so ... i removed everything which has ruby word on it by this command 

```
apt-get purge ruby*
```
Now , 
the problem is when i run this command 
whatis ruby 
whereis ruby 
i get proper and acceptable response but when i try to run it with 
rails new myapp 
this thing will appear ..
> bash: /usr/local/bin/rails: /usr/local/bin/ruby: bad interpreter: No such file or directory

i want to install Ruby on rails . Is there any solution other then formating  and re-installation from stract 
please help in , i wasted my whole day  for this .. and you're my last hope.

---

