---
title: "Install openproj?"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Hansievr on 2011-01-21
I can't install openproj. I downloaded the deb version and it is in the Downloads file. Is there any things that need to be installed before it will run?:-?

---

### Post by sikander3786 on 2011-01-21
Which version of Ubuntu is this? If 10.04, right click and open with GDEBI package manager. Does it even open in the package manager or Software Center?

---

### Post by waqas_butt0071 on 2011-08-30
hi, i am using 10.04 i installed the openproj converted the .rpm to .deb with alien and using dpkg installed it. now it is not running, i don't know what is the problem can any one help!

---

### Post by waqas_butt0071 on 2011-09-04
ahh i solved the problem;
Uninstalled it and downloaded the .deb file and installed it using 
```
sudo dpkg -i openproj_1.4-2.deb
```
and then some dependancy issues, apparently the java platform was not installed the first time.fixed it with
```
sudo apt-get install -f
```

---

### Post by frosh on 2011-09-15
I got this problem. Please help me...

[IMG]http://s1.proxy03.twitpic.com/photos/large/398876590.png[/IMG]

---

