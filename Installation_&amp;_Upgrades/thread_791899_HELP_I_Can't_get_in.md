---
title: "HELP I Can't get in"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by pbeesley on 2008-05-12
so i went to reinstall hardy over the top of a current install. I selected to reformat the hard drive that hardy was o already while installing. Now install went fine BUT after reboot It wouldn't load hardy :( Grub error 22 I think, something about the partition not being there??? So i reinstalled again...same thing....so i thought I know I'll boot into windows and come on these forums for help.....same thing when trying to get into windows.........

HELP :(

/me cries

---

### Post by Slim Odds on 2008-05-12
Did you look here?

[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

---

### Post by pbeesley on 2008-05-12
trying to reinstall and the install stops at 94% cause it can't install grub in hd0 :(

---

### Post by pbeesley on 2008-05-12
omg I'm going crazy someone please help. I've tried installing about 10times now selecting different options with no luck :(

---

### Post by pbeesley on 2008-05-13
ok well half fixed....I managed to get Hardy installed but not windows XP. Had to delete partition and recreate it. Then JUST install hardy and nothing else :( for the future....what went wrong???

---

### Post by iaculallad on 2008-05-13
A bad partition in you physical drive maybe that after you delete and re-create it, you managed to install Hardy.

---

### Post by pbeesley on 2008-05-13
yeah but I had installed Hardy twice on that partition previously? I just wanna know what went wrong so I know for the future

---

### Post by housam on 2008-05-13
> **pbeesley said:**
> ok well half fixed....I managed to get Hardy installed but not windows XP. Had to delete partition and recreate it. Then JUST install hardy and nothing else :( for the future....what went wrong???

Type the following code in a terminal and post the results please :
```
sudo fdisk -l
```
where -l is a small L

---

