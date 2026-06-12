---
title: "If I install from source, will it eventually get updated?"
date: 2017-04-18
forum: Installation &amp; Upgrades
---

### Post by mikey93898 on 2017-04-18
Hello all,

I'm having trouble understanding how apt/yum work. Suppose I'm running the latest ubuntu-release of Chromium or some other app. Then I decide I want the very very latest version - the releases on the project page, which are much newer than what ubuntu is distributing. So then suppose I go to the project page and install their latest version.

Would that mean I have to manually upgrade from then on? ... or would apt/yum notice that eventually the ubuntu version has become newer than the one I installed, and upgrade it for me?

Not sure how to make that situation happen, or if it already is happening.

---

### Post by wildmanne39 on 2017-04-18
If you install from source then it will not get updated through the repositories unless at a later time the package is added to the repositories in the form of a .deb but you would have to remove the compiled one and install the .deb file, it still would not upgrade straight across because they are installed by different means and compiled sources are not managed by apt.

---

### Post by mikey93898 on 2017-04-26
Okay thank you

---

### Post by wildmanne39 on 2017-04-26
> **mikey93898 said:**
> Okay thank you
Your welcome!

---

