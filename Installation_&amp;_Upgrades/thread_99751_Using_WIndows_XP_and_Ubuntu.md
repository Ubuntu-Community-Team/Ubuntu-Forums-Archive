---
title: "Using WIndows XP and Ubuntu"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by jørgen on 2005-12-06
First i installed XP on my computer, then i installed Ubunu on the same computer, but on a different HDD. Now only Ubuntu starts when i turn on the computer. 

How can i choose between the two OSes?

---

### Post by gosh on 2005-12-06
Did you install GRUB?

In that case everytime you start up your machine it will prompt which OS it should boot.

---

### Post by jørgen on 2005-12-06
I dont know, i just used the default for everything in the Ubuntu installer.

---

### Post by bwog on 2005-12-06
You have to edit grub, look here: [http://ubuntuforums.org/showthread.php?t=95044&highlight=edit+grub+windows](http://ubuntuforums.org/showthread.php?t=95044&highlight=edit+grub+windows)

---

### Post by jørgen on 2005-12-07
I have done everything on that guie, but i cant make it work

---

### Post by bwog on 2005-12-07
Can you post your menu.list and your partition table?

---

### Post by LoclynGrey on 2005-12-07
I dual boot Ubuntu and MS Windows between two separate HDD's.

This is my set up:
Ubuntu HDD is set to master
MS Windows is slave.
My system boots into Ubuntu as default, but in the boot menu (after the system post screen) I can select Ubuntu or Windows.
Initially you may not see this boot menu because it may be hidden by default or you can see it but Windows wont boot from it.

You need to modify your grub boot loader configs.
In the Ubuntu terminal type
sudo gedit /boot/grub/menu.lst
(you will need to put in your password to become root)

The grub boot menu should pop up in gedit (like note pad in windows but probably 1000 times better lol) which is called menu.lst.
I always make a backup, so maybe save it as menubk.lst or something in case you go crazy. Then open menu.lst again.

Scroll down till you find
*****************
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
*****************
change to

*****************
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
*****************
notice the change in #

Then add the bottom lines at the end of the file for the windows part of the boot option.
This is mine, which works.

*****************
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
*****************

The only draw back i have is that windows boot screen goes transparent for a while as it's booting but I always get through into windows. (and then quickly exit ashamed that I went back to the evil side...again)

Hope this helps.

---

### Post by jørgen on 2005-12-09
i reinstalled everything and now everything works fine.

---

