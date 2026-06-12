---
title: "[SOLVED] Problems with updates"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by ptnewby on 2008-09-10
Hello all, i have had ubuntu 8.4 installed on my laptop since its release.The past few weeks there has been a problem with the updates failing.

the error i get is listed below, i was wondering if someone could please advise if this can be fixed

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/Hardy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/Hardy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/Hardy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/Hardy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/Hardy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/Hardy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/Hardy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/Hardy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Many Thanks

---

### Post by mattduckman on 2008-09-10
for whatever reason, the H in hardy is capitalized, which is your problem.

the error is most likely in your sources.list
open a terminal and type
```

gksudo gedit /etc/apt/sources.list

```
and replace all instances of 'Hardy' with 'hardy'

---

### Post by ptnewby on 2008-09-11
Hello, 

Thanks for you help, i will give it a go. But just out of interest how can you tell that is the problem, from the error message i posted?

Many thanks

---

### Post by iaculallad on 2008-09-11
> **ptnewby said:**
> Hello, 

Thanks for you help, i will give it a go. But just out of interest how can you tell that is the problem, from the error message i posted?

Many thanks

To answer you question, bear in mind that in Ubuntu (Linux) everything is case sensitive. 'H' is very much different with 'h'. Comparing the repository links you posted with the normal repository on Hardy, the only difference is that of 'Hardy' and 'hardy'. So changing it to 'h' should probably sort your problem.

---

### Post by Sef on 2008-09-11
> Thanks for you help, i will give it a go. But just out of interest how can you tell that is the problem, from the error message i posted?]

When one clicks on your link, this appears:  > The requested URL /ubuntu/dists/Hardy/universe/binary-i386/Packages.gz was not found on this server.
The H is capitalized which it should not be.

---

### Post by ptnewby on 2008-09-12
Problem sorted, 

Thanks everyone for you help :)

---

