---
title: "Help with RPM's"
date: 2005-07-24
forum: Installation &amp; Upgrades
---

### Post by Mastertronic on 2005-07-24
This is a very important question about rpms's

What is a short version easy way installing these files.? :|

---

### Post by PeP on 2005-07-24
there are 2:
find and install the corresponding .deb with synaptics or apt

if not possible alien (apt-get install alien ) will help you but ... good luck

---

### Post by javiadip on 2005-07-24
[QUOTE=Mastertronic]This is a very important question about rpms's

What is a short version easy way installing these files.? :|[/QUOTE]

```


sudo apt-get install alien 


```


To convert rpm into .deb

```


alien -d rmp_package.rpm


```

---

### Post by Mastertronic on 2005-07-24
[QUOTE=javiadip]```


sudo apt-get install alien 


```


To convert rpm into .deb

```


alien -d rmp_package.rpm


```[/QUOTE]

thankyou i will give it a shot.

---

