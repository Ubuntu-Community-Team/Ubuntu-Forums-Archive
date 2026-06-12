---
title: "Ubuntu on Virtual PC 2004"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by korny666 on 2005-07-05
when i install it it works fine except for the screen it goes all weird and when i try
# Log into another virtual session as root
 
# cd /etc/X11
# pico xorg.conf (to edit xorg.conf)

Now, scroll down in pico to Section "Screen" and find the entry named "DefaultDepth". Change the setting you find there from 24 to 16.
 
# Ctrl O
# Enter
# Ctrl X
# # reboot

i cannot scroll down to tthe section "screen" because there isnt any there :-| can someone please help?

---

### Post by SilentGreg on 2005-07-05
Please post your X.org config file.

Greg

---

### Post by korny666 on 2005-07-06
how do i find it/ where do i find it??

---

### Post by korny666 on 2005-07-06
some one please help!!!!!!!!!!!!!!!!!

---

