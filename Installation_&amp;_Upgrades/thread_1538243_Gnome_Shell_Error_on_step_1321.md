---
title: "Gnome Shell Error on step 13/21"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by mixint27 on 2010-07-24
Hello everybody...I need some help...

Im installing Gnome Shell. im building it myself. On step 13 i get this error:

*** Error during phase configure of gconf: ########## Error running ./autogen.sh --prefix /home/tony/gnome-shell/install --libdir '/home/tony/gnome-shell/install/lib' --disable-defaults-service --disable-static --disable-gtk-doc  *** [13/21]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"

How should i fix this? what option should i choose from the 8 options it gives me? I have tried 1; it brings me back to the same error, when i try option 5, it does not do anything.

Please help

Thanks!

---

### Post by mixint27 on 2010-07-25
bump!

---

### Post by xcorex on 2010-07-26
Just read what it says: "No package 'ORBit-2.0' found"

and then, sudo aptitude search orbit, and then...

sudo aptitude install liborbit2-dev

Easy, huh?

---

### Post by mixint27 on 2010-07-26
yes. pretty easy...and thats what i did. thanks for replying.

i was not really sure if i needed that though...aahh...im just new to ubuntu

thanks again

---

