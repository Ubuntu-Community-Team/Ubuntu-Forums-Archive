---
title: "getting updates from a mirror site"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by tobmeister on 2006-09-02
Hi all,

Was curious if it was possible to get the updates for 6.06 without using the add updates on the ubuntu system.

I have a dial up at home but I could download them from work on a T1 if there was a site available

Thanks

Tobmeister

---

### Post by &#12465;&#12452;&#12488; on 2006-09-02
Yes, indeed! You can download packages from [packages.ubuntu.com](http://packages.ubuntu.com/) and manually install them at home. If you press the Mark All Upgrades button in Synaptic, and select File &#8594; Generate package download script, it'll output a script which downloads all the updated packages. If you don't use any UNIX-like system at work, you could open the script in a text editor, and manually download each file listed there.

GDebi makes it easy to install packages. Just double-click on one, and press the Install button!

---

