---
title: "File exists but I still get HTTP 404"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by Jordanwb on 2007-12-19
I was able to install torrentflux on Ubuntu server 7.10 But when I goto it through: 192.168.1.4/torrentflux I get the http 404 error. I went to 192.168.1.4 and it listed torrentflux but when I click on it I get 404.

---

### Post by ThaRabbit on 2007-12-19
did you set the appropriate rights for the files in (I assume) /var/www/folderwhereyouputorrentflux/ ?

In my case I just ran:
```
sudo chown www-data /var/www/torrentflux/ -R
```

Not perfect, but works.

---

### Post by Jordanwb on 2007-12-19
That was it thanks.

---

