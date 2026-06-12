---
title: "problems installing ubuntu"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by linuxguy23 on 2008-02-01
Hi i am new to linux and i see some have already posted about this problem but i still haven't found an answer. I get as far as the 4th step in the install but when the partition window opens its blank theres nothing listed there. i did use the shrink option in windows vista so i could have another partition to be able to install linux but did this some how confuse it? PLEASE HELP!!

---

### Post by linuxguy23 on 2008-02-01
it would be nice if someone would please respond to my question i cannot find help anywhere and its really driving me crazy.

---

### Post by logos34 on 2008-02-01
Go back to the desktop, >system>accessories>terminal

**gksudo gparted**

Do you see the empty space there?

also run this command and post it:

**sudo fdisk -l**

---

### Post by JamesUser on 2008-02-01
Am I missing something here?

He has not yet installed ubuntu. How can he run gksudo?

---

### Post by logos34 on 2008-02-02
right, he's on the live cd, I say gksudo reflexively.

sudo gparted 

[edited.  gksudo works too, actually]

or go to 

system>admin>partition editor


You do have to use **sudo** fdisk -l, even on the live cd

---

