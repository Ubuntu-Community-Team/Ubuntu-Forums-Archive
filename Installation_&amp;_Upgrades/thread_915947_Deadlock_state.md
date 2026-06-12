---
title: "Deadlock state"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by sinser on 2008-09-10
Hi,

Please help me solve the deadlock state.

I have purchased new dell 1310 series. I installed ubuntu on it, that's were the problem started. I cant install Ethernet card driver on ubuntu cos i cant find .deb driver file. without this i cant connect to internet, which leads to no internet connection.

I got the .RPM files of the driver. but i cant convert to .deb file since i dont have alien package installed in my lappy. To get the alien package i need to update my ubuntu which again requires internet which i dont have from the begining.

Now please help me find a way to install ethernet driver.

---

### Post by manishtech on 2008-09-10
> I installed ubuntu on it, that's were the problem started. I cant install Ethernet card driver
Do you really require ethernet driver installation? I never heard that one needs to do so. Ethernet interfaces dont require drivers these days. Maybe you should check out some problems with the settings of the internet connection.

---

### Post by sinser on 2008-09-10
If u say so, then

+ why isn't my ethernet drive displayed in network connections ?
+ how to install other drivers like graphic and audio ?

---

### Post by manishtech on 2008-09-10
We first need to find out the the hardware and whether they are detected or not

For ethernet type

```
 lspci | grep -i Ethernet
```

For wireless type

```
 lspci | grep -i wireless
```

For graphics type

```
 lspci | grep -i graphics
```

---

