---
title: "Failed to install VLC in ubuntu 10.10 x64"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by FelipeAragao on 2011-01-21
Hi! My ubuntu 10.10 is 64 bits and one week-old. While trying to install vlc i'm getting this error since the first day:

Failed to fetch: [http://br.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdio/libiso9660-7_0.81-4_amd64.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdio/libiso9660-7_0.81-4_amd64.deb) 404  Not Found

What can I do? Thx!

=========== EDIT ===========
this problem occurs when trying to download it through software center (something like "failed to download packages: verify the connection to the internet").
Seems that the same problem also appears while trying to download other programs, such as the Compiz Fusion Icon:
Failed to fetch [http://br.archive.ubuntu.com/ubuntu/pool/universe/l/lua50/liblua50_5.0.3-4_amd64.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/l/lua50/liblua50_5.0.3-4_amd64.deb) 404  Not Found
Failed to fetch [http://br.archive.ubuntu.com/ubuntu/pool/universe/l/lua50/liblualib50_5.0.3-4_amd64.deb](http://br.archive.ubuntu.com/ubuntu/pool/universe/l/lua50/liblualib50_5.0.3-4_amd64.deb) 404  Not Found

---

### Post by coffeecat on 2011-01-21
There must be something wrong with the br.archive.ubuntu.com server - hopefully only temporarily. I tried clicking on the links that the forum has made in your post and I get the 404 too. But if I change br.archive to gb.archive or fr.archive in the address bar of Firefox, then I can download the deb packages. Which means that the download path is correct, except for the particular server.

Either - wait for 24 hours. Perhaps the br.archive server simply needs to be resynchronised with the main archive server.

Or...

Go to System > Administration > Synaptic. Now, Settings menu > Repositories > Ubuntu Software tab. Under 'Download from:' change to 'Main Server', or 'Other' and choose from one of many servers around the world. Preferably geographically near you.

---

### Post by FelipeAragao on 2011-01-21
That worked! Thanks.

---

