---
title: "Need pan, but Install libgnet 2.0 failed..."
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by doolang on 2005-07-11
I am trying to install the pan newsgroup reader using both terminal and synaptic, and I get the following error and can't install. The file exists, is it just corrupted? can anyone fix this?

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnet/libgnet2.0-0_2.0.4-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnet/libgnet2.0-0_2.0.4-1_i386.deb)
  MD5Sum mismatch

Thanks for any help.  :smile:

---

### Post by SGC on 2005-07-11
Here a list of mirrors for libgnet:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgnet%2Flibgnet2.0-0_2.0.4-1_i386.deb&md5sum=9d1054a22e7bb8bc41d12d195d10aecd&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgnet%2Flibgnet2.0-0_2.0.4-1_i386.deb&md5sum=9d1054a22e7bb8bc41d12d195d10aecd&arch=i386&type=main)

After downloading the file , install it with:
dpkg -i libgnet2.0-0_2.0.4-1_i386.deb

---

### Post by doolang on 2005-07-11
Thanks so much. Worked great.  :smile:

---

