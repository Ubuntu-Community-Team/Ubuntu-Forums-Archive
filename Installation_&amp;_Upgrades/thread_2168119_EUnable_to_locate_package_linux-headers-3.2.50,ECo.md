---
title: "E:Unable to locate package linux-headers-3.2.50,E:Couldn't find any package by regex"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by mojgan_ghasemi on 2013-08-16
Hi,
so my kernel version is 3.2.50 (by getting uname -r)
I get this error while trying to apt-get the headers (sudo apt-get install linux-headers-3.2.50)

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.2.50
E: Couldn't find any package by regex 'linux-headers-3.2.50'
```

I have checked the other forum which mostly suggested to run "sudo apt-get update", which I did, but it didn't help...
Can someone please tell me what's going on...I'm a bit confused :/
I also hope this is the correct place to ask

---

### Post by GwL3eNC on 2013-08-16
Hello,

i got also no 3.2.50 headers. A apt-get update wont change kernel things.
But a

sudo apt-get dist-upgrade 

does. But if it works, i dont know. Have you build this kernel on yor own?

---

### Post by mojgan_ghasemi on 2013-08-16
Yes, I built this kernel myself. I have the source files in /usr/src
I tried the "sudo apt-get dist-upgrade" as well but it doesn't work.

---

### Post by GwL3eNC on 2013-08-16
Then the dist-upgrade wont help. The headers are also in /usr/src.
More i dont know, i hope someone can help you.

---

### Post by mojgan_ghasemi on 2013-08-16
Thank you for your answer anyway. I hope so too.

---

