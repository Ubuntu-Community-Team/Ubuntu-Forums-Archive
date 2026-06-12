---
title: "problem installing 14.04 64-bit version"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by wallek on 2014-09-06
Hi, recently a download the latest ubuntu 14.04.1 64-bit version. I burn the DVD and then install like normal but when ubuntu is running and i check the version it says 32-bit. I tried downloading one more time the image in case i downloaded wrong the first time but same result. I dont know what can be.

I have an AMD Athlon II X4 630 with 4gb RAM if it is of interest.

Thanks in advance and greetings

---

### Post by grahammechanical on 2014-09-06
How did you check the version? On my machine

```
uname -a
```

gives

> Linux sdb8-Roll-Dev 3.16.0-6-generic #11-Ubuntu SMP Mon Jul 28 01:59:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


What do you get? 

The name of a 64bit ISO image will have "-amd64.iso" as part of its name but a 32bit ISO image will have "-i386.iso" as part of its name.

Regards.

---

### Post by wallek on 2014-09-07
Hi

```
uname -a
```

gives me

```
Linux wallek-GA-MA785GM-US2H 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 athlon i686 GNU/Linux
```

and the name of the iso i downloaded is "ubuntu-14.04.1-desktop-amd64.iso"

Also i check in System Settings > Details says OS type  32-bit

---

### Post by shellback84 on 2014-09-07
This happened to me as well. When I went to download some hardware drivers, their site says that I have the 64 bit operating system, after a system check but my system settings in ubuntu says I have the 32 bit operating system. I thought I had downloaded the 64 bit system as well. I am not an expert with this operating system in any way shape or form but to my uneducated Linux mind that could spell trouble if one trys to install, using sudo, a 32 bit driver into what might be a 64 bit system. I am not asking for anything here, I am just sying that this happened to me as well.

---

