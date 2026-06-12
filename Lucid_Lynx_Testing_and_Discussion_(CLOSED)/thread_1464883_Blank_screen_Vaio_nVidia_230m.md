---
title: "Blank screen Vaio nVidia 230m"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by St3althcAt on 2010-04-28
Hello all,

I've downloaded Ubuntu 10.04 to test it. However, I got an annoying problem... It boots to nothingness. Even with wubi or live cd, I see the "disk light" working for some time and then stoping, and still blank screen. I've tried hitting shift to enter Grub (this while using wubi) and selecting verbose mode or safe graphics. Still no image. On live CD, I hit shift also, choose no boot graphics, a menu appears, choose "Install", blank screen again, with CD "running" however. Searched forum and Google for solutions to this problem, and can't find any. Some help please?

Hardware:

Sony Vaio VPCCW1S1E
LED Display
nVidia GeForce 230M 512 Mb

Thank you.

---

### Post by cariboo on 2010-04-28
I'm not sure about wubi, because I've never used it, but to boot from the Live CD press the any key at the initial screen, press F6 and select nomodeset, the select try or install, you should be able to boot to the desktop using the vesa driver.

---

### Post by St3althcAt on 2010-04-29
That did the trick on live CD. Thank you!

---

### Post by St3althcAt on 2010-04-29
I'm going to have to "rephrase" that last post.

That did work for the install. After the install, I can't boot to Ubuntu. Same problem happens, and can't get past it the same way. How do I boot now?

Thank you.

---

