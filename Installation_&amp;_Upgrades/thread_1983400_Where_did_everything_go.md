---
title: "Where did everything go?"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by captgadget on 2012-05-20
I did a clean install of 12.04 now I have a pane on the side of the desktop. How do I find the information about my system? How do I find all the other applications such as Ryhtm Box, my scanner, my photo editing, etc?

---

### Post by darkod on 2012-05-20
That's the new Unity interface in use since 11.10. By hitting the windows logo key on the keyboard (the super key), the so called Dashboard will open with a search line. In this search line you can search for any installed program. For example start typing term... for terminal and it will show you all programs that have term in the name. The Dashboard also opens by clicking on the first icon in unity, the ubuntu logo.

If you prefer to use the older style layout, in terminal you can install:
sudo apt-get install gnome-panel

After that log out. On the login page, click the ubuntu logo next to your user and select the Gnome Classic type of session. After that enter your password to log in and you should have the older style session type.

It remembers the last session type used so you don't need to do this on every login. Just when you want to switch between gnome classic and unity.

---

### Post by captgadget on 2012-05-20
I got an error in terminal: unable to locate package panel

---

### Post by darkod on 2012-05-20
panel or gnome-panel?

The package name is gnome-panel, as in my previous post.

sudo apt-get install gnome-panel

---

### Post by captgadget on 2012-05-20
This time I did a copy paste and everything is working just fine. Thank you

---

