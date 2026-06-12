---
title: "Hardy Heron login screen is goofy"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by RRK on 2008-05-09
I upgraded to Hardy Heron (8.04 LTS)last night.  The few things I tried appear to work, except the Login screen is kind of goofy.  The user and password areas are squished down in the right hand corner and the cursor does not go there. I just type into the ether it seems and I can get in.  The options that used to be in the lower left hand corner do not show. And the word UBUNTU shows as UBU on the right edge of the screen. (see attached jpg).

Once I am in the desktop looks fine. As I said I only tried a couple things like evolution and firefox (which strangely is a beta version).  

Anyone have any ideas on what is going on with the login screen?

---

### Post by brigux on 2008-05-09
Just remove the line containing "virtual" in your xorg.conf

---

### Post by dstew on 2008-05-09
You can edit /etc/X11/xorg.conf, and put the mode that has the correct resolution at the top of the list of modes. All the modes will still be available, but now the login screen will look normal.

---

### Post by housam on 2008-05-09
Or you can just pass it by enabling automatic login.

---

