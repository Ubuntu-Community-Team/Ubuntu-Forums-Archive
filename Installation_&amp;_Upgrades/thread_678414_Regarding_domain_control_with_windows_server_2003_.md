---
title: "Regarding domain control with windows server 2003 r2 on main server"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by preejith on 2008-01-25
hi....On my main server I have installed windows server 2003r2...and I have got two other server which I want to make as a domain control and I want Ubuntu to be installed in it with samba.....Can anyone of you plz say is it possible....ad if yes can you plz say how.....
plz help me out...i will be ver thankfull..........

---

### Post by benanzo on 2008-01-25
You want to use Samba if you want Ubuntu to act as a PDC.

[This]("http://www.enterprisenetworkingplanet.com/netos/article.php/1144701") article is not Ubuntu-specific but covers the Samba configuration pretty well.

To install Samba in Ubuntu just do:
```
sudo apt-get install samba
```

Then follow the part of the article about setting up Samba for domain authentication etc.

Good Luck!

---

