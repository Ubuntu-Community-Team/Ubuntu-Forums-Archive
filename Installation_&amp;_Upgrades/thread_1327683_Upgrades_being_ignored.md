---
title: "Upgrades being ignored"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by jus71n742 on 2009-11-15
```

W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009o+repack-0ubuntu0.8.04.2_all.deb
  404 Not Found [IP: 91.189.88.46 80]

```

I think this is because I am running an older version of Ubuntu (Ubuntu 8.04 (hardy))
Kernel: 2.6.24-19-generic

Am I correct in my assumption or is there another reason for this?  or should I just upgrade it to the newest version?

---

### Post by yeats on 2009-11-15
Did you do a

```
sudo apt-get update
```

before updating?  (Or Check if you're using Synaptic/Update Manager)?

---

### Post by Slowjoe on 2009-11-29
Thanks Chrissharp123, that helped me out too!  Now I understand what apt-get update is about.  I feel that where I've read about installing software, this command hasn't really been explained well.

---

### Post by jus71n742 on 2010-01-03
Terribly sorry for taking so long to reply. Yes I have done it both ways. both ignore packages

---

### Post by QIII on 2010-01-03
Are you in the US?

If in the US, try setting your Software Sources to download from the "Server for the United States".

It looks like you are going to the main server, which is a good bet unless you are having connectivity problems.

You could try a nearby server, but it sometimes takes a while for the newest stuff to be pushed to mirrors.

---

### Post by jus71n742 on 2010-01-03
I download from a server in I think Georgia Tech.  I am upgrading to 9.10 so I will deal with this issue if need be later.  Thank you for all your help guys

---

