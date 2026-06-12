---
title: "dual boot freebsd and ubuntu"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by user sam on 2009-12-18
I know I tried to do this before and it didn't work, but hopefully i've gained some more experience. I'm trying to dual boot Ubuntu karmic and freeBSD 8. I'd leave well enough alone, but I find Freebsd quite fascinating and can't switch completely over until i learn how to get wireless to work. I found a couple of tutorials that said i should edit my /boot/grub/menu.lst file file to switch between the two systems, but I don't seem to have a /boot/grub/menu.lst. What i'd like to know is: Do I need to make a new file? If so, how do I know what goes in it? If not, what the heck to I need to do???

---

### Post by shredder12 on 2009-12-19
First of all /boot/grub/menu.lst is the configuration file for grub legacy where as you will get grub2 with Ubuntu Karmic. So, that won't work.. 
But whatever you are trying to do can be easily done in grub2 too..
Just tell us what do you really want to do?

or 

you may try the Ubuntu community documentation of grub2 to do this yourself..
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

