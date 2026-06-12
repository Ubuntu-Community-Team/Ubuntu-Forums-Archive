---
title: "How to get windows to be the defualt boot"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by dillon111222 on 2008-04-26
So I have a computer with 2 internal hard drives in it. The first drive has Windows vista and the second one has nothing on it. Im going to install Hardy Heron on the second hd. 

However im the only one in my house that knows how to use a computer so when the computer is turned on i want it to boot into windows by defualt and when i use it i want to be able to boot into ubuntu if i wanted to.

How am i going to do this???

THX for help in advance...

---

### Post by p_quarles on 2008-04-26
Please post the output of the following terminal command:
```
cat /boot/grub/menu.lst
```
After we see this, someone will be able to tell you how to edit this file so that Windows boots by default.

---

### Post by obidose on 2008-04-26
When it has been installed grub will also be installed. This will mean a list appears at start up allowing you to select OS. By default Ubuntu will be the default.

You can edit this put windows as the default boot. The easiet way is to install grubED using synaptics, gives you a visual interface which is easy to navigate.

Alternatively you can use easyBCD in windows to restore the vista bootloader and then add ubuntu on to that as a secondary OS.

---

### Post by dillon111222 on 2008-04-26
K ill install ubuntu on second hd then post what i get from entering that code

---

### Post by tzg6sa on 2008-04-27
Just take a look at the menu.lst. Search for the "default" option. You have to set its value correctly. (Not complicated at all)

---

