---
title: "[SOLVED] Grub error"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by nzcyclone on 2007-10-23
Hiya Everyone,

Installed 7.10 and it works really great except for Grub bootloader. For whatever reason known only to itself it has the wrong partition and disk selected and wont start Ubuntu. for some reason it has it set to hd2,0 when should be hd0,0 yes true, I can hit the "E" key and edit it and then press the "B" key to boot it but would sooner not have to do that. Yes have found the menu.1st file which has the error but when try to save it after changing it it says do not have permission. 

Is there a way to save the changes to this file? or is there an easier way to get it changed?

Many thanks, Greg

---

### Post by rsambuca on 2007-10-23
You just need to edit it with root privileges, by using 'gksudo'.

```
gksudo gedit /boot/grub/menu.lst
```

You can change the line, save it, and then close.  You will also have to correct the line that says:```
# groot=(hd2,0)
``` and change it to # groot=(hd0,0).  Otherwise it will mess up with the next kernel upgrade.

---

### Post by nzcyclone on 2007-10-24
YAY it worked thank you very much for that help and also thank you for the groot=  one as well I found it in the file and also changed that as well. I thought if had a # in front that make it a comment and it wouldnt be read ? or am I mistaken there

---

### Post by rsambuca on 2007-10-24
> **nzcyclone said:**
> YAY it worked thank you very much for that help and also thank you for the groot=  one as well I found it in the file and also changed that as well. I thought if had a # in front that make it a comment and it wouldnt be read ? or am I mistaken there

I don't know the specifics, but somehow those lines at the top are used by grub during updates.

---

