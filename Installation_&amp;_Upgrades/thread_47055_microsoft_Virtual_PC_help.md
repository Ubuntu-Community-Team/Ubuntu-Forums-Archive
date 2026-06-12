---
title: "microsoft Virtual PC help"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by korny666 on 2005-07-07
when i install it it works fine except for the screen it goes all weird and when i try
# Log into another virtual session as root

# cd /etc/X11
# pico xorg.conf (to edit xorg.conf)

Now, scroll down in pico to Section "Screen" and find the entry named "DefaultDepth". Change the setting you find there from 24 to 16.

# Ctrl O
# Enter
# Ctrl X
# # reboot

i cannot scroll down to tthe section "screen" because there isnt any there can someone please help?

---

### Post by Juergen on 2005-07-07
This section should be there...

But if you really can't find it maybe you want create a new xorg.conf
Change to root in another virtual console again and start 'xorgcfg -textmode' or 'xorgconfig'
The first one is a bit nicer IMHO.

It won't hurt to create a backup copy of your existing xorg.conf first ;-)

---

