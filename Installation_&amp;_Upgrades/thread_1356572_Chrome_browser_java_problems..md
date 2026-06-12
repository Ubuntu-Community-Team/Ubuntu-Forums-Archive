---
title: "Chrome browser java problems."
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by Andertraaks on 2009-12-16
Hey. Since I'm having some problems with Firefox and now using Google Chrome internet browser, I am not able to use java applications, but Flash applications and videos works just fine.

I have tried to search for this, but I can't really find any anwser to this, does anyone have the same experiences or know a way to fix this?

I've got Sun Java 1.6 update 17 fresh install, my Ubuntu version is 9.04, my laptop is an Acer Extensa 5220.

---

### Post by mikewhatever on 2009-12-16
Check out this:
```
youruser@yourpc$ cd /opt/java/jre1.6.0_17/bin
youruser@yourpc$ ControlPanel

Select the Java Tab
Click on View...
Click on Find...
Click on Next...
Select /opt/java/jre1.6.0_17/
Click on Next...
Click on Finsh...
deselect the others JREs
Click on OK...
Click on Apply...
Click on OK...

root@yourpc# mkdir /opt/google/chrome/plugins
root@yourpc# cd /opt/google/chrome/plugins
root@yourpc# ln -s /opt/java/jre1.6.0_17/lib/i386/libnpjp2.so .
youruser@yourpc$ google-chrome --enable-plugins %U 
```

Note, your version of java may be different, if installed from the repositories.
Edit: I can't directly link to the source of the info, it's one of the posts in the thread linked below.

---

### Post by Andertraaks on 2009-12-16
Well thanks for your input, solved the problem myself, by installing different types of java and now it works.

---

