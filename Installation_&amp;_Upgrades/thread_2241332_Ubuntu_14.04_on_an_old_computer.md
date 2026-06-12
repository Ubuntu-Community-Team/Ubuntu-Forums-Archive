---
title: "Ubuntu 14.04 on an old computer"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by herrcule on 2014-08-25
Hello everyone,
I have currently the 12.04 LTS version of Ubuntu. My computer is quite old, it is a Toshiba Satellite M 30-204 with an Intel Pentium M at 1.6 GHz and 512 Mo RAM.
Of course everything's not fine, but I somehow manage to make it work with the current Ubuntu version.
Does the 14.04 LTS version more resource-intensive? Is it better to keep the 12.04 LTS or can I switch to the 14.04?

Thank you in advance,Dam

---

### Post by christopher9 on 2014-08-25
Lubuntu 14.04 might just be what you need..nice and easy on system resources...[www.lubuntu.net]("http://www.lubuntu.net")

---

### Post by Dennis N on 2014-08-25
I have the same processor, Pentium M 1.6 ghz (Pentium M 730), running Xubuntu 14.04 on a Dell, and it runs very well. A difference is I upgraded the RAM to 2 gB so that helps. I have not used regular Ubuntu on this laptop since 8.04.

---

### Post by grahammechanical on 2014-08-25
I would say the 14.04 uses less memory than 12.04. That has been my experience. Have you been updating 12.04. You should now have 12.04.5. Run

```
lsb_release -a
```

If you have 12.04.5 then you will have the same hardware stack as 14.04. How much memory does System Monitor show is being used? How much of its own memory does the graphic adapter have? I class the graphic adapter as a key component in getting a suitable user experience. It might be better to remain on 12.04.

If you have enough hard disk space you could install 14.04 to its own partition and dual or triple boot and then you will get a real test of 14.04. Right now I am using Utopic Unicorn (14.10 development branch) and System Monitor shows base memory usage of 32% of 1GB RAM. Now when I first installed 12.04 it was 70% of 1GB RAM. So, things are getting better. 

Regards.

---

### Post by Claus7 on 2014-08-25
Hello,

usually on old laptops xubuntu is my 1st choice, since it is much less resource intensive.

Regards!

---

### Post by Dennis N on 2014-08-25
Some data on memory usage: Xubuntu 14.04 + Firefox + Audacious + Htop = 484 mB of memory used. With your 512 mB you can't have much running. It might be wise to add another memory module if you plan to use that machine.

---

### Post by Ksiencha on 2014-08-26
Try [**Linux Mint 17 Mate**](http://blog.linuxmint.com/?p=2627), really decent on my old laptop.

---

### Post by herrcule on 2014-09-03
Thanks to all of you for the replies !

---

