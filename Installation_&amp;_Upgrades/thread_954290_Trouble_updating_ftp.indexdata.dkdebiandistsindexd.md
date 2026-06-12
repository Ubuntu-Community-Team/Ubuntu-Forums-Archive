---
title: "Trouble updating ftp.indexdata.dk/debian/dists/indexdata/etch/"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by ceabaird on 2008-10-21
OK, in the process of [installing Koha]("http://wiki.koha.org/doku.php?id=ubuntu_gutsy") on my small Linux box here, and I've run into a problem getting these to fetch:

W: Failed to fetch [http://ftp.indexdata.dk/debian/dists/indexdata/sarge/released/binary-i386/Packages.gz](http://ftp.indexdata.dk/debian/dists/indexdata/sarge/released/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ftp.indexdata.dk/debian/dists/indexdata/sarge/released/source/Sources.gz](http://ftp.indexdata.dk/debian/dists/indexdata/sarge/released/source/Sources.gz)  404 Not Found

Specifically, I'm trying to update the package index for IndexData, after installing libexpat, libssl0.9.7 and yaz.

I tried changing the source file to etch from sarge, but it didn't make a difference. 

What needs to be changed to make this work?

Thanks for any assistance.

---

### Post by Partyboi2 on 2008-10-21
Try adding
```
deb http://ftp.indexdata.dk/debian/ sarge main
```You may run into dependency problems installing the packages though.

---

### Post by ceabaird on 2008-10-21
Thanks for the reply.

OK, I checked my /etc/apt/sources.list file, and it seems I already have the code:

```
deb [http://ftp.indexdata.dk/debian/](http://ftp.indexdata.dk/debian/) sarge main
```

added.

Here's what the bottom of the file looks like now:
```
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ftp.indexdata.dk/debian](http://ftp.indexdata.dk/debian) sarge main
deb-src [http://ftp.indexdata.dk/debian](http://ftp.indexdata.dk/debian) sarge main
deb [http://ftp.indexdata.dk/debian](http://ftp.indexdata.dk/debian) indexdata/sarge released
deb-src [http://ftp.indexdata.dk/debian](http://ftp.indexdata.dk/debian) indexdata/sarge released
```

Looking at the above, it looks (to me) that maybe I have some repetition in the last 4 lines? Are the last two lines necessary, since ftp.indexdata.dk/debian is invoked in the two previous lines?

Still learning, thanks for the help.

-S

---

### Post by Partyboi2 on 2008-10-21
> deb [http://ftp.indexdata.dk/debian](http://ftp.indexdata.dk/debian) indexdata/sarge released
deb-src [http://ftp.indexdata.dk/debian](http://ftp.indexdata.dk/debian) indexdata/sarge released These 2 lines are seem to be incorrect. So by adding a #infront of them you should know longer get 
> W: Failed to fetch [http://ftp.indexdata.dk/debian/dists...86/Packages.gz]("http://ftp.indexdata.dk/debian/dists/indexdata/sarge/released/binary-i386/Packages.gz")  404 Not Found

W: Failed to fetch [http://ftp.indexdata.dk/debian/dists...rce/Sources.gz]("http://ftp.indexdata.dk/debian/dists/indexdata/sarge/released/source/Sources.gz")  404 Not Found

---

### Post by ceabaird on 2008-10-21
Thanks - I deleted those 2 lines, ran sudo apt-get update,
and got no more errors. I guess [the instructions here]("http://wiki.koha.org/doku.php?id=ubuntu_gutsy") need to be updated.

Thanks for the help!

---

