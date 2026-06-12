---
title: "Failed to Fetch"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by jloflin on 2007-10-30
Failed to fetch [http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/binary-amd64/Packages.gz](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/main-amd64/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/experimental-amd64/binary-amd64/Packages.gz](http://janvitus.interfree.it/ubuntu/dists/feisty-upure64/experimental-amd64/binary-amd64/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found

---

### Post by jloflin on 2007-10-30
I don't know how I got that entered, but the above message contains the response when I try to upgrade to gutsy. Can anybody tell me what I need to do to fix this?

Thanks.

Randy

---

### Post by taurus on 2007-10-30
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of those lines in there to comment them out.  Save it and then run

```
sudo apt-get update
```
See if you can upgrade your machine now.

---

### Post by jloflin on 2007-10-30
OK, I did that and got this:
(the medibuntu lines were NOT in sources.list)

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by taurus on 2007-10-30
Look in /etc/apt/sources.list.d.  

```
ls -la /etc/apt/sources.list.d
```
Otherwise, post the output of this command here.

```
ls -la /etc/apt
```

---

### Post by jloflin on 2007-10-30
Wait, I found it. Let me try it now.

---

### Post by jloflin on 2007-10-30
Working. Thanks.

---

