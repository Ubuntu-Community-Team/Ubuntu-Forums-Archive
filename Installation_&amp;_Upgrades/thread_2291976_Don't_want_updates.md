---
title: "Don't want updates"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2015-08-24
Updater keeps trying to install a couple of things I don't want (such as Chinese language) and I keep unchecking them. Is there any way to tell it to forget about them, so it doesn't keep bugging me? Ubuntu 14.04 on a homemade AMD 64 bit desktop.

---

### Post by TheFu on 2015-08-24
[https://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package](https://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package)

However, be aware that doing this forever will lead to "APT hell" as more and more dependencies become held back, broken.  For something like Chinese locales, I wouldn't worry much, but for some other packages, it might be bad in a few months.

---

### Post by v3.xx on 2015-08-24
There is also the package "localepurge" which will remove all extra translations.  It also comes packaged with "bleachbit".

---

### Post by vasa1 on 2015-08-24
> **v3.xx said:**
> There is also the package "localpurge" which will remove all extra translations.  It also comes packaged with "bleachbit".
Make that "localepurge" and, if you're planning on using bleachbit, make sure you read the instructions very, very carefully.

---

