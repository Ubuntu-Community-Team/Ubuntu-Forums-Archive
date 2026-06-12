---
title: "missing menu.lst"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by Gyanos422 on 2009-12-21
'm trying to set up a dual boot system with xp on one drive, and ubuntu 9.10 on the other. i did this with 9.04 with no problems and was running it for quite a while until i needed the extra hard drive space and got rid of ubuntu because windows was taking up most of my usage time.  

Well, after having trouble with the cd that ubuntu sent me, i tried a burned copy which installed flawlessly. now when i follow directions that i originally got found from a use named LHA (many are familiar with him as he knows his stuff) i can't find the menu.lst file that is supposed to be in the /boot/grub/ directory in order to put the coding into to select which OS i want to boot.

am i looking in the wrong place or is this not implemented in 9.10?

---

### Post by howefield on 2009-12-21
```

```> **Gyanos422 said:**
> ...or is this not implemented in 9.10?

Correct.

```
https://wiki.ubuntu.com/Grub2#Grub 2 Files & Folders
```

---

### Post by dhavalbbhatt on 2009-12-21
> **Gyanos422 said:**
> 'm trying to set up a dual boot system with xp on one drive, and ubuntu 9.10 on the other. i did this with 9.04 with no problems and was running it for quite a while until i needed the extra hard drive space and got rid of ubuntu because windows was taking up most of my usage time.  

Well, after having trouble with the cd that ubuntu sent me, i tried a burned copy which installed flawlessly. now when i follow directions that i originally got found from a use named LHA (many are familiar with him as he knows his stuff) i can't find the menu.lst file that is supposed to be in the /boot/grub/ directory in order to put the coding into to select which OS i want to boot.

am i looking in the wrong place or is this not implemented in 9.10?

There is no menu.lst in Ubuntu 9.10. Ubuntu has moved to GRUB 2.0 with the release of 9.10.

---

### Post by Gyanos422 on 2009-12-21
ok i read that page. Although i'm still not sure what to do to dual boot the two os's.  

Previously i just inserted this code into menu.lst:

title Windows XP 
root (hd1,0) 
makeactive 
map (hd0) (hd1) 
map (hd1) (hd0) 
chainloader +1


That worked perfect. It gave me the OS choice at boot, and no matter which i chose it used the non-os hard drive as the slave and the os drive as the master (i guess that how it normally works...I'm unexperienced with dual boot os so bear with me)

What do i do now with 9.10? would it just be easier to go back to 9.04 or ealier?

---

### Post by east2idaho on 2009-12-21
You might want to install and use the GUI tool "startup-manager", which allows you to make many of the same kind of changes that you are used to handling by manually editing your menu.lst file.

---

### Post by oldfred on 2009-12-21
the new grub2 is very good at finding other operating systems. If it did not find it on the install setup rerun this:
sudo update-grub

If that does not work a manual entry similar but formated differently has to be added to 40_custom, but should not be required.

---

