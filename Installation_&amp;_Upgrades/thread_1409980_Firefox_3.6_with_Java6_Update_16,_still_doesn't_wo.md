---
title: "Firefox 3.6 with Java6 Update 16, still doesn't work"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by ravi.xolve on 2010-02-18
As this page says [http://kb.mozillazine.org/Java#On_Linux](http://kb.mozillazine.org/Java#On_Linux) I need to create a link to the file libnpjp2.so for the Java plugin to work. However I found that there is no such file in the java installation directory.

```
ln -s  /usr/your_path_here/java/jre1.6.0_xx/lib/i386/libnpjp2.so libnpjp2.so
```I have Java installed from the default repo. How to get Java plugin back into Firefox.

---

### Post by wojox on 2010-02-18
[Firefox-3.6 and Java]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Get-JRE")

---

### Post by ravi.xolve on 2010-02-18
I found the file here:

```
/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libnpjp2.so
```

But now when I open a page with a Java applet, Firefox hangs. So I have disabled Java. Isn't the new plugin system made to circumvent this.

---

### Post by wojox on 2010-02-18
Just link it:

```
ln -s /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/
```

And restart Firefox.

---

### Post by ravi.xolve on 2010-02-19
I did this already, but now if I open a page with Java applet on it, Firefox hangs.

---

