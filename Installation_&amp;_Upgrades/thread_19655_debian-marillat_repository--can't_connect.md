---
title: "debian-marillat repository--can't connect"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by cornmax on 2005-03-13
Greetings,

I've been working with Ubuntu over the past week and so far I love this distro. The only problem I've had so far is trying to set up some of the multimedia options. There are several packages that are only available through the debian-marillat repository. The problem is that I've found it absolutely impossible to connect. I've tried connecting many, many times on different days and at different times and I've had no success. I keep getting the error "Could not connect to ftp.nerim.net:21 (1.0.0.0), connection timed out". I believe that I've added the repository correctly in the sources.list file, but I could be doing something else completely wrong. At this point, I'm clueless. The line I added is as follows:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Has anyone else run into this problem? I would really appreciate any tips!

---

### Post by kahping on 2005-03-13
hoary preview just came out recently, so i think it may have something to do with loads of Ubuntu-ers upgrading their systems  :-? 

i myself could connect to the ftp server, but it's very very sloooow.  ](*,) 

kahping

---

### Post by bored2k on 2005-03-13
[QUOTE=cornmax]Greetings,

I've been working with Ubuntu over the past week and so far I love this distro. The only problem I've had so far is trying to set up some of the multimedia options. There are several packages that are only available through the debian-marillat repository. The problem is that I've found it absolutely impossible to connect. I've tried connecting many, many times on different days and at different times and I've had no success. I keep getting the error "Could not connect to ftp.nerim.net:21 (1.0.0.0), connection timed out". I believe that I've added the repository correctly in the sources.list file, but I could be doing something else completely wrong. At this point, I'm clueless. The line I added is as follows:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Has anyone else run into this problem? I would really appreciate any tips![/QUOTE]
 Just checked, only thing I get is this and its Ok [signature thing I havent configured]
125ko réceptionnés en 29s (4299o/s)                                            
Lecture des listes de paquets... Fait
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures cou
ldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F4
1B907
W: Vous pouvez lancer « apt-get update » pour corriger ces problèmes.


 cat /etc/apt/sources.list
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

---

### Post by cornmax on 2005-03-13
Thanks for responding. I'm still not sure what is going on, but I still can't connect.It's strange that so many others don't have any problems. Hopefully  I'll be able to connect sometime soon.

---

### Post by cornmax on 2005-03-15
I still can't connect. I've tried and tried but still no sucess. Am I the only one that has had this problem? It seems that I can't connect to anything outsiide the Ubuntu repositories.

---

