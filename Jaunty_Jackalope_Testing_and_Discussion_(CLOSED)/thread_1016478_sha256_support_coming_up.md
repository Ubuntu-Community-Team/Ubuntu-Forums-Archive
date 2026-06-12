---
title: "sha256 support coming up"
date: 2008-12-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-12-19
Hi all, 
 What do you guys think of sha256sum coming up. 

[https://blueprints.launchpad.net/ubuntu/+spec/apt-sha256](https://blueprints.launchpad.net/ubuntu/+spec/apt-sha256)

Should it improve security from md5sum and sha1sum, if how by how much?

Also what do you think as we now have sha384 and sha512 also. 

A random checksum being generated of some file. 

```
$ sha256sum yofrankie.txt
070bc5d4a9db9575aab88e53c292079d1c397a8f925c953b8b92d9cdacb3591f  yofrankie.txt

$ sha384sum yofrankie.txt
ba4e76f127af8f282e69d748538e00d67405ee09c926b7a4b7844ea1a38e0d02e8c4dc4b24f5beff0826ac4fe1b0570c  yofrankie.txt

$ sha512sum yofrankie.txt
28cb9002835e2b344bed52e977c760d86266b0b2a63627b71ba5a111fe7cb678715396e7900f443ce297c7aab0ce5c298ff0328104dca646d0d1c95209be9171  yofrankie.txt

```

Thoughts, comments, opinions all appreciated.

---

