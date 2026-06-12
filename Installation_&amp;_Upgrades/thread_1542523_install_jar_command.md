---
title: "install jar command"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Ralph Boland on 2010-07-30
I am running Ubuntu 10.04.
I just created a jar file and now I am trying to extract the files again.
So I tried the jar command but it was not found.
Then I tried installing the jar package but there is no such package.
I assume that the jar command is contained in some package that I must
install but I don't know what package.
I did a search for "jar" in the synaptic package manager but did not
identify what package I should install.

Any suggestions as to what I should try next?

Regards,

Ralph Boland

---

### Post by andrewc6l on 2010-07-30
If you just want the contents of the jar, you can use unzip:

```
unzip -v file.jar (to list)
unzip file.jar (to extract)
```

JAR files are really just .zip files with a MANIFEST.MF.

If you want the full Sun JDK, instructions are here:
[http://www.clickonf5.org/linux/how-install-sun-java-ubuntu-1004-lts/7777](http://www.clickonf5.org/linux/how-install-sun-java-ubuntu-1004-lts/7777)

(but I haven't tried them)

---

