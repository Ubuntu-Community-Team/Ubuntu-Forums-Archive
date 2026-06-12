---
title: "java 1.4.x to 1.5.x"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by Tux+ on 2006-08-07
Hi,

I have installed java 1.5 through automatix but when I type
```
java --version
```
it still returns the 1.4.x version.

How do I make 1.5 the default version?

---

### Post by Jagot on 2006-08-07
```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by Tux+ on 2006-08-08
> **Jagot said:**
> ```
sudo update-java-alternatives -s java-1.5.0-sun
```

After doing that command it says
```
java --version
Unrecognized option: --version
Could not create the Java virtual machine.
```

---

### Post by Jagot on 2006-08-08
Try this then:

```
sudo update-alternatives --config java
```

Instead of automatically selecting one as the other command did, this one will list all versions of Java you have installed so you can select the one you want.

---

### Post by Tux+ on 2006-08-08
Thanks! That worked.

---

