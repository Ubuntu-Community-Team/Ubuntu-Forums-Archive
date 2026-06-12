---
title: "becoming root"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by jjb945025 on 2011-12-23
this, i do not understand but im hoping someone out there knows of a workaround.... ok when i type in "su" to try becoming root.im promted for the admin. password and when i type it in and press enter i always recieve an "authentication failure" message hence i cannot become root...ever. does anyone know why this is happening because i know im entering the password correctly so what could be going on here??? thank you ...

---

### Post by lisati on 2011-12-23
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by spcwingo on 2011-12-23
You can also use:

```
sudo -i
```

in lieu of "su" to temporarily become root.  Have a quick look-see at the link lisati posted for an explanation as to why this is default behavior in Ubuntu.

---

### Post by coffeecat on 2011-12-23
@jjb945025, you asked this question over a year ago, and you were given a link to the RootSudo page then. Thread here:

[http://ubuntuforums.org/showthread.php?t=1606626](http://ubuntuforums.org/showthread.php?t=1606626)

Please read the link lisati has posted. It will explain all.

Thread closed.

---

