---
title: "update problems"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by D-Force on 2006-10-02
Hi,
I've installed yesterday Ubuntu 6.06, wich a friend downloaded for me on the 30th of Mai.
Now I wanted to update all the progs.
But I am not able to install about 13 progs, I've allways get the same error msgs..
Has anybody an idea, how to solve this little problem ?
thx

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5-0.6ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagick9_6.2.4.5-0.6ubuntu0.1_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.22-0ubuntu6.06_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.22-0ubuntu6.06_all.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.22-0ubuntu6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.22-0ubuntu6.06_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-386_2.6.15-26.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-386_2.6.15-26.46_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-386_2.6.15.24_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-386_2.6.15.24_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-common_2.6.15.11-3_all.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-common_2.6.15.11-3_all.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15-26-386_2.6.15.11-3_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/linux-restricted-modules-2.6.15-26-386_2.6.15.11-3_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-386_2.6.15.24_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-386_2.6.15.24_i386.deb)
  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-386_2.6.15.24_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-386_2.6.15.24_i386.deb)
  404 Not Found

---

### Post by Kateikyoushi on 2006-10-02
Try this first, copy it to a terminal.

```
sudo aptitude update
```

---

### Post by D-Force on 2006-10-02
thx, it worked!
it's all fixed now!

---

