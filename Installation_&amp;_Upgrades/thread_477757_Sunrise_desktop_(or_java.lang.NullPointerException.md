---
title: "Sunrise desktop (or java.lang.NullPointerException)"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by pvent on 2007-06-18
I'm trying to run sunrise-desktop on ubuntu, but it gives me the next error when I try to execute sunrise-desktop.sh:

java.lang.NullPointerException
   at com.distantchord.sunrise.apps.Desktop.getDocumentationPath(Unknown Source)
   at com.distantchord.sunrise.ui.MainWindow$HelpContentsAction.<init>(Unknown Source)
   at com.distantchord.sunrise.ui.MainWindow.<init>(Unknown Source)
   at com.distantchord.sunrise.apps.Desktop.run(Unknown Source)
   at com.distantchord.sunrise.apps.Desktop.main(Unknown Source)

What am I missing for it to run?

The text of sunrise-desktop.sh is the following:

```
java -Xmx128m -Djava.library.path=. -jar sunrise-desktop.jar
```

---

