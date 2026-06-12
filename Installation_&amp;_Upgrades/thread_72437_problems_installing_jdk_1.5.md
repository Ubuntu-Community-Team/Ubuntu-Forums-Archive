---
title: "problems installing jdk 1.5"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by paulo.sebastiao on 2005-10-06
Hello,
I am a proud new user of Ubuntu. It's the most friendly distro i've ever tried. Let's cut to the chase.
I'm having problems installing j2eesdk from Sun. I get the following message:

```
paulo@kamikaze:~/downloads$ ./j2eesdk-1_4_02_2005Q2-linux.bin
./j2eesdk-1_4_02_2005Q2-linux.bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```
I have Ubuntu 5.10 Breezy Badger. What should I do? I already have the latest version of libc6. Help needed :)
Cheers!

---

### Post by emperor on 2005-10-06
[quote=paulo.sebastiao]Hello,
I am a proud new user of Ubuntu. It's the most friendly distro i've ever tried. Let's cut to the chase.
I'm having problems installing j2eesdk from Sun. I get the following message:

```
paulo@kamikaze:~/downloads$ ./j2eesdk-1_4_02_2005Q2-linux.bin
./j2eesdk-1_4_02_2005Q2-linux.bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

``` I have Ubuntu 5.10 Breezy Badger. What should I do? I already have the latest version of libc6. Help needed :)
Cheers![/quote] 
Looks like 1.4 not 1.5?

I found that Breezy already had java 1.4 installed but no plugins were installed for Firefox!

try install using "sudo"
sudo ~/downloads/j2eesdk-1_4_02_2005Q2-linux.bin

---

