---
title: "webmin not working on ubuntu server 10.04"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by agitdd99 on 2010-03-19
I have installed lucid ubuntu server daily build per March 17th 2010, and i then i installed webmin (.deb). As a refference, webmin installation in karmic server a long ago, there was no problem.

but in lucid, I have noticed that there is file dependency error. there is no libmd5-perl package in lucid that is needed in the dependency.

Well then, i installed it with -f option, but can't run it on client browsers. typing "*[https://hostnameORserverIPaddress:10000](https://hostnameORserverIPaddress:10000)*" is no use.

is there anybody experiencing the same thing and please tell what's wrong and the solution? thanks.

---

### Post by perro84 on 2010-03-19
I've download that package from here:

[http://packages.ubuntu.com/jaunty/libmd5-perl](http://packages.ubuntu.com/jaunty/libmd5-perl)

And now works flawlessly

---

### Post by nanog on 2010-03-19
debian (and ubuntu) stopped packaging webmin because webmin developers refused to follow debian package configuration policy:
[https://answers.edge.launchpad.net/ubuntu/+question/2873](https://answers.edge.launchpad.net/ubuntu/+question/2873)

where to go if you have problems with webmin: [http://www.webmin.com/community.html](http://www.webmin.com/community.html)

---

