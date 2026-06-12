---
title: "I need some Guidence here...."
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by mattcadu on 2008-08-21
Well here is the problem.  I visited java.com to upgrade my computers java. Anyway the current java download for linux was downloaded and is sitting on my desktop.  The name of the files is jre-6u7-linux-i586-rpm.bin  

/home/mcadu/Desktop/jre-6u7-linux-i586-rpm.bin

I have tried finding this file in add/remove , and the package manager.  I cant seem to install it, how do i use the terminal, can somebody walk me thru exactly what to type to install this file?  Any help is appreciated., 


ty
matt

---

### Post by forger on 2008-08-21
How about going to menu Applications > Accessories > Terminal and executing:
```

sudo apt-get install --reinstall sun-java6-jre sun-java6-bin

```

If you want all the "restricted goodies", like flash java and codecs, you can use:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mattcadu on 2008-08-21
ok, cool that seemed to work, now.... another file i have on my desktop i need to install is 


/home/mcadu/Desktop/frostwire-4.17.0.i586.deb


same thing here as the last one but frostwire-4.17.0.i586.deb?

---

### Post by forger on 2008-08-21
No, there's a simpler way, you double click on the file, it opens an installer window :)

---

