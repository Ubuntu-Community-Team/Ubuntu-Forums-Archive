---
title: "How to Install Anjuta and Gambas"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by Gaurav_Shah on 2008-07-14
Hello Community,
I am using Ubuntu 8.04 i will like to download and install Anjuta and Gambas

I tried  sudo apt-get install anjuta gambas command but I am getting following message
sudo: unable to resolve host gaurav-desktop

Now can you tell me what to do ?

---

### Post by unoodles on 2008-07-14
simple:
type "sudo apt-get install anjuta gambas" (without the quotes)

---

### Post by shenen on 2008-07-24
hai 
i installed gambas2-2.7.0
but when i called the program an error occured

ERROR: #27: Cannot load component 'gb.qt': cannot find library file 

does anyone know how to solve it

---

### Post by Malac on 2008-07-24
> **Gaurav_Shah said:**
> Hello Community,
I am using Ubuntu 8.04 i will like to download and install Anjuta and Gambas
 
I tried sudo apt-get install anjuta gambas command but I am getting following message
**sudo: unable to resolve host gaurav-desktop**
 
Now can you tell me what to do ?
This is a problem in your /etc/hosts file 
if you check it you will find that your domain has been tagged on the end.
 
e.g.
```
localhost gaurav-desktop.<domainname>
127.0.0.1 gaurav-desktop.<domainname>
......
```
or similar. All you have to do is change it by adding this.
```
localhost **gaurav-desktop** gaurav-desktop.<domainname>
127.0.0.1 **gaurav-desktop** gaurav-desktop.<domainname>
......
```
 
Hope this helps.

---

