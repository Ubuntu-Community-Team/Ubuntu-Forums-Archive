---
title: "Sources.list using Ubuntu mirrors"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by dessale on 2005-06-16
My ISP provides a mirror of Ubuntu archives which is unmetered and therefore more economical for me to use.  
So I have edited /etc/apt/sources.list to replace the ubuntu archive name with that of my ISP's mirror.  For example I have replaced:-

  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
with in **my case:-**
  deb [http://mirror.internode.on.net/pub/ubuntu/ubuntu](http://mirror.internode.on.net/pub/ubuntu/ubuntu) hoary-updates main restricted   

and so on through the list.  And this works fine for me.  However I can't see how to do the same thing for the security.ubuntu entries, such as:-
  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
as I can't see anything like that on my ISP's mirror.

Anyone got any suggestions?

---

### Post by defkewl on 2005-06-16
Then use the ones from Ubuntu. Otherwise ask your ISP.

---

