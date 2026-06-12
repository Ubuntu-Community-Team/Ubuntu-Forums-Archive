---
title: "Problems after upgrade to 9.04"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by nayrb on 2009-12-25
Hello all,

I'm hoping someone will get me pointed in the right direction. I'm relatively new to linux, and recently I tried to update to ubuntu 9.04. (I had to add some extra flag to the apt-get upgrade command I didn't understand in order to get it to update.)

The problem is that I can boot to the terminal, but the GUI won't load. I can't recall the exact error message when it goes to the terminal, but it says something about an image not being able to load. This suggests to me it trying to resume the system after hibernation?

Typing startx won't work because I don't think xserver-xorg-core is install properly and/or there are some package dependencies. A package missing, I think, is libx, or something like that.

For some reason as well, apt-get update won't work. It says it cannot resolve (I think that's the word) several websites like security.ubuntu.org. Is my internet connection not working? How do I know my internet connection if it is or isn't?

Any help would be appreciated!

---

### Post by taurus on 2009-12-25
Which release did you use before you upgraded it to 9.04?

---

### Post by nayrb on 2009-12-25
I'm pretty sure 8.10, but there is a small chance it was 8.04. I think I remember upgrading from 8.04 to 8.10.

---

### Post by taurus on 2009-12-25
If you don't have a lot of important files that you need to save or backup and have an ability do backup your files, it's probably have you some headache in a long run to just do a fresh install of 9.04!  Or better yet, install the newest release, 9.10, if you plan to do a fresh install unless there is a reason to still with an older release, 9.04.

---

### Post by nayrb on 2009-12-25
I have a dual boot system with Win XP. Doing a clean install of 9.10 shouldn't cause any problems since it will all be done the current linux partition I have now, right?

I think I'll download the iso file for ubuntu 9.10 now.

(Thanks for the suggestions so far.)

---

