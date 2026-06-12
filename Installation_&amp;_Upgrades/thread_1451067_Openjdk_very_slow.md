---
title: "Openjdk very slow"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2010-04-09
I'm running Lucid beta 1 x86 patched as of this morning and using jEdit 4.3.1 for editing source code files. If I use openjdk for Java, updating of the jEdit text area is glacially slow. If I execute

```
sudo update-java-alternatives -s java-6-sun
```

to swap to using Sun Java, then the text area updates at quite acceptable speed.

---

### Post by thomas430 on 2010-05-31
I have noticed this also.

I have a feeling that it's specifically painting tasks that are happening slowly.

---

### Post by thomas430 on 2010-06-14
Try running with the following option:
java -Dsun.java2d.pmoffscreen=false 

This worked for me, perfectly acceptable speed now.

---

