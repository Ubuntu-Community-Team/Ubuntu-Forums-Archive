---
title: "Apt-get wants to remove lots of Java updates"
date: 2009-03-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-03-09
A few hours ago I noticed that apt-get is prompting to remove these java packages:

> The following packages were automatically installed and are no longer required:
  ttf-wqy-zenhei ttf-kannada-fonts libaccess-bridge-java default-jre
  ttf-telugu-fonts openjdk-6-jre-headless tzdata-java openjdk-6-jre
  openjdk-6-jre-lib rhino ttf-oriya-fonts librsvg2-bin default-jre-headless
  ca-certificates-java ttf-bengali-fonts
The following packages will be REMOVED
  ca-certificates-java default-jre default-jre-headless libaccess-bridge-java
  librsvg2-bin openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib rhino
  ttf-bengali-fonts ttf-kannada-fonts ttf-oriya-fonts ttf-telugu-fonts
  ttf-wqy-zenhei tzdata-java
Would it be safe to remove them? So far I've being saying "no", as I don't think replacement packages have been installed in their place. Is this a bug of some sort?

---

### Post by izizzle on 2009-03-09
If I am not mistaken, (and correct me if I am), then Java updates itself and all its packages after every JRE update, so the previous packages become irrelevant. They are probably just sitting there taking up HD space so apt wants to remove them.

---

