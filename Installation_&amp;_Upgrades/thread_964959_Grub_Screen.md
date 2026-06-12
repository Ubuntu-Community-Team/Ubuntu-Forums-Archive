---
title: "Grub Screen"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by simonlugi on 2008-10-31
As I have a dual boot when I start my computer I get the Grub screen which shows Vista and about half a dozen lines for Ubuntu. It appears that it shows the latest and old version of the Linux kernel.
Can anyone tell me how to remove all the old versions and have the grub screen show only one Ubuntu option.

---

### Post by francisc1701 on 2008-10-31
That's easy.

The file that controls the grub menu lives here: /boot/grub/menu.lst

ALT+F2 and type ```
gksu "gedit /boot/grub/menu.lst"
```

Navigate towards the end of the file, until you see 
```
title <your grub menu item>
root <bla>
kernel <bla bla>
initrd <bla bla>
```
Now based on the text following "title" identify the menu items you don't need. Delete all the lines until the next "title" line. A maybe safer approach is to comment those lines, instead of deleting them. Prefix each line you want to comment with a #.

Example:
```
#title <Menu item you don't want>
#root <bla>
#kernel <bla bla>
#initrd <bla bla>
#quiet

title <Menu item you want to keep>
root <bla>
kernel <bla bla>
initrd <bla bla>
quiet
```

---

### Post by simonlugi on 2008-10-31
Thanks that looks much better

---

