---
title: "UbuntuStudio (Karmic) meta fonts package won't leave me alone!"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mike_IronFist on 2009-10-03
I am in love with all the new features in the Karmic beta, and I love Ubuntu Studio, so naturally, I installed all the application meta-packages for it (ubuntustudio-audio, ubuntustudio-graphics, and ubuntustudio-video) to get my hands on the newest Ubuntu Studio apps. Unfortunately, the Graphics package points to a fonts meta-package itself, which tried to install a bunch of fonts. Not all the fonts could be installed correctly.

Now every time I install *ANYTHING* the fonts try to do post-installation configuration again, then fail again. It's annoying as all heck! Can anyone help me fix it so that the fonts stop trying to install?

Note: I removed the fonts meta-package, btw.

---

### Post by Mike_IronFist on 2009-10-03
Bump

---

### Post by Mike_IronFist on 2009-10-03
Solved! This blog post explained the solution:
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/]("http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/")

---

