---
title: "Error at the very end of downloading the files of Ubuntu 10.04"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by linux_dream on 2010-05-10
Ok so it's been like 4 or 5 days I didn't turn off my computer in order to fully download Ubuntu 10.04, from Ubuntu 9.10.
I've downloaded 1990 of the 1996 files and now I get the error:
```
Failed to fetch http://ar.archive.ubuntu.com/ubuntu/pool/main/i/indicate-python/python-indicate_0.3.0-0ubuntu1_i386.deb 403  Forbidden
Failed to fetch http://ar.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp_0.8-0ubuntu3_i386.deb 403  Forbidden
Failed to fetch http://ar.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-pptp/network-manager-pptp-gnome_0.8-0ubuntu3_i386.deb 403  Forbidden
Failed to fetch http://ar.archive.ubuntu.com/ubuntu/pool/main/p/policykit-desktop-privileges/policykit-desktop-privileges_0.1_all.deb 403  Forbidden
Failed to fetch http://ar.archive.ubuntu.com/ubuntu/pool/main/p/pyasn1/python-pyasn1_0.0.8a-1_all.deb 403  Forbidden
Failed to fetch http://ar.archive.ubuntu.com/ubuntu/pool/main/t/ttf-kacst-one/ttf-kacst-one_3.0-1ubuntu2_all.deb 403  Forbidden
Failed to fetch http://ar.archive.ubuntu.com/ubuntu/pool/main/t/ttf-takao/ttf-takao-pgothic_003.02.01-2ubuntu1_all.deb 403  Forbidden
```
What should I do?  I've googled this and found nothing.  Also I don't have a that bad internet connection, my usual speed of download is 100 Mbits/s but lately it's been much, much slower to upgrade anything regarding my ubuntu.

---

### Post by davidmohammed on 2010-05-10
looks like your software source - repository is not being updated.  Try another repository (choose other and then select another country (not argentina))

---

### Post by linux_dream on 2010-05-10
> **davidmohammed said:**
> looks like your software source - repository is not being updated.  Try another repository (choose other and then select another country (not argentina))
Thank you very much for helping.  I'm really a newbie, would you mind to explain me how can I do so?

---

### Post by davidmohammed on 2010-05-10
administration - software sources

in download from click the down arrow and choose other

---

### Post by linux_dream on 2010-05-10
> **davidmohammed said:**
> administration - software sources

in download from click the down arrow and choose other
Thanks, I found it.  It downloaded some files (quite fast) and then I retried to download the missing files for Ubuntu 10.04 and I got the same error, although I specified to download from a Canadian sever...
Nevermind, I'll try another sever.

---

### Post by linux_dream on 2010-05-10
Strangely, although I can select any other server to download from, it won't change the "Download from:   Principal server".  
So I can't choose another one.  What can I do?

---

### Post by RJARRRPCGP on 2010-05-10
This is a serious problem, the server is being instructed to deny you files!

---

### Post by linux_dream on 2010-05-10
Nevermind, I think I'm getting it.

---

### Post by linux_dream on 2010-05-10
Thank you so much [davidmohammed]("http://ubuntuforums.org/member.php?u=600258"), you actually solved 2 problems I had.  I'm replying to you from Ubuntu 10.04 and now my downloads will be faster.  Thread solved.

---

