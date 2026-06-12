---
title: "ATI Radeon Xpress 1270"
date: 2010-02-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bshosey on 2010-02-01
I have an ATI Radeon Xpress 1270 in my Dell Inspiron 1720. I am runing the ubuntu 10.4 alpha 2 fresh install. Ran all the updates. What happens is with and with out compiz enabled the desktop is corrupted. I get a strange box around the courser. I get odd ripped lines on the wallpaper and menus. The fonts are impossible to read. The gnome panels are even corrupted ans washed out.

Did not have this problem in 9.10

---

### Post by cyberey66 on 2010-02-21
I just started having this problem as well with the same exact video card.  It used to work fine, but now I have visual errors.

If you use the 'radeonhd' driver, they go away, but there is no 2d hardware acceleration and you cannot use compiz.

I believe the issue occurs in later version of the driver.  I reinstalled karmic and upgraded everything, after this upgrade I began to see the errors.

If I find a solution, I will post back.

---

### Post by cyberey66 on 2010-02-22
When I upgraded, I was using the latest kernel and noticed the video problems.  I just reverted back to the 2.6.31.6 kernel and the video works again.  Odd...  

I am confused because I did use the 2.6.32 kernel when I was using a i386 arch installation, and the video worked.   I then switched to 64bit and compiled the same kernel from the same exact source and the video doesn't work.   I then compiled the old 2.6.31 kernel and the video works.  I am stumped.  When compiled for i386, video works perfectly, when compiled for AMD64, video is corrupted.

What kernel are you using?  What arch are you using?

---

### Post by bshosey on 2010-03-06
Sorry been away from the forums. I had a death in the family so have not been on line in a while. I will try the 32 bit install of ubuntu and see if I have the same problem.

---

### Post by bshosey on 2010-03-21
This appears to be resolved in the Beta Version

---

