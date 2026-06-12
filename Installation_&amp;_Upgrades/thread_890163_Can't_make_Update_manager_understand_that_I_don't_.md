---
title: "Can't make Update manager understand that I don't want the upgrade!!! Please help..."
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by Truckerpunk on 2008-08-14
Hey. I'm really fond of Ubuntu and how easy it is to use... And I like the Update Manager... But now I've run into some trouble. I run Sun Java(because it's the only way I can play Blood bowl over [www.Fumbbl.com](www.Fumbbl.com)), and now the manager wants me to install OpenJDK java updates and I really don't want that.. Even though I have set the default Java interpretor to SUN I don't know if this upgrade will Fu#k me over... And everyhig is working like a charm now. So is there a way to make Ubuntu understand that I don't want the upgrade? (there aren't any cancel-button...  and f I uncheck the updates and close the Update manager the "Updates available"-icon keeps sitting in my menu-bar. And I'm afraid that I will accidentally click the update button). Any help is highly appreciated.

---

### Post by spiderbatdad on 2008-08-14
go to synaptic, select your installed version, go to the package menu, select "lock version."

---

### Post by Vadi on 2008-08-14
So in synaptic, search for "openjdk", select it, then click on package -> lock version.

---

### Post by Truckerpunk on 2008-08-14
Thanks a lot guys... Worked like a charm... One more thing added to my knowledge of Ubuntu... Great! And thanks for the fast replys.

---

### Post by tinny on 2008-08-15
Why dont you remove OpenJDK? It really is just a waste of space having it installed if Sun Java is setup correctly.

If Sun Java is setup correctly....

```

java -version

```

Should result in something like...

```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

If it is setup correctly remove OpenJDK...

```

sudo remove --purge openjdk*

```

---

