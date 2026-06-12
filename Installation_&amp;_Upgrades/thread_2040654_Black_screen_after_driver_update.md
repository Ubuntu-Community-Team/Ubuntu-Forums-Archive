---
title: "Black screen after driver update?"
date: 2012-08-11
forum: Installation &amp; Upgrades
---

### Post by AlexLev on 2012-08-11
Hey i decided to try out Ubuntu as a seperate OS on my computer. Anyway, installtion goes fine, and i can restart over and over without anything bad happening. But if i activate either of the updates for my Nvidia GeForce 7100 / nForce 630i then restart to complete the update, i end up with a black screen with a few randomly coloured pixels once i log in.

Any help with this? Please note i'm an absolute beginner with Linux, thanks!

---

### Post by AlexLev on 2012-08-12
Bump

---

### Post by Kalanac on 2012-08-12
Definitely sounds like a driver issue.  The random pixels are artefacts, junk data left in the card which is just being spat onto the screen.

Take a look through the following guide on installing and configuring nVidia binary drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)


Also, when starting a support post, try to include as much detail as you can, such as the version of Ubuntu you're using :)  Different versions behave in different ways.  I assume you're using 12.04: Perfect Pangolin

You should still be able to access a TTY terminal by hitting ctrl+alt+f1 (or any F key up to 6).  These TTY terminals act in more or less the same manner as a regular terminal you'd open on the desktop.  The desktop is on TTY 7 which you can get back to by hitting ctrl+alt+f7.

Run through the guide and see what you can manage to get done.  Post any errors on the forum as completely as you can so folks can help you along :)

---

