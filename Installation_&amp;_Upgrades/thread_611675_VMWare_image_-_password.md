---
title: "VMWare image - password"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by sathyaram_s on 2007-11-13
I downloaded Ubuntu-7.10-server-i386.zip from [http://isv-image.ubuntu.com/vmware/](http://isv-image.ubuntu.com/vmware/). 

There is no mention of any userids/passwords. Does anyone know the userid/password I can use for this image? 

Thanks

---

### Post by zvacet on 2007-11-13
I don´t know that,but why don´t you download it from here

[http://releases.ubuntu.com/gutsy/]("http://releases.ubuntu.com/gutsy/")

---

### Post by sathyaram_s on 2007-11-13
Hi, Thanks for taking time to reply. 

The images in the link you have provided appears to be CD/DVD images for installation. I actually want a VMWare image so that I can run using a VMPlayer. 

Thanks 

> **zvacet said:**
> I don´t know that,but why don´t you download it from here

[http://releases.ubuntu.com/gutsy/]("http://releases.ubuntu.com/gutsy/")

---

### Post by cosinux on 2007-11-13
Had the same problem. Try user ubuntu and password ubuntu.

Have fun

---

### Post by sathyaram_s on 2007-11-13
Fantastic!!!! It works. Thanks for your help.

For the benefit of others who read this:
After logging in, I issued 

sudo passwd root 

and changed root's password. 


> **cosinux said:**
> Had the same problem. Try user ubuntu and password ubuntu.

Have fun

---

