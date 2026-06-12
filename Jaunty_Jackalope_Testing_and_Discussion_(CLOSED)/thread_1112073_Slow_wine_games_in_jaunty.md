---
title: "Slow wine games in jaunty"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biji on 2009-03-31
Hi.... I'm wondering why i get low fps in wine games in jaunty? even slower than in intrepid.. i'm using 64bit version of ubuntu

---

### Post by glaze on 2009-03-31
Do you have 3D acceleration enabled? You can see by typing ```
glxinfo |grep direct
```. Also, if you have Intel graphics, there can be problems with performance when compared to Intrepid due to driver bugs.

---

