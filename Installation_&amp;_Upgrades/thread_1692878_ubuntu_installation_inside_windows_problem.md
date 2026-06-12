---
title: "ubuntu installation inside windows problem"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by ankur.trapasiya on 2011-02-22
hello ...!!! 
 
i have installled my ubuntu inside windows and now when i start my pc at that time it is showing me error that grub is corrupted. .
 
I am in great dilemma now. i have my entire work data in ubuntu and windows is not showing me any data inside my ubuntu ..
 
i want to restore my ubuntu back...
 
 
can anyone please help ?
 
Thanks in advance... :(

---

### Post by Rubi1200 on 2011-02-22
Hi,
if this is a Wubi install, see here for issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you need more help, feel free to ask.

---

### Post by ankur.trapasiya on 2011-02-22
hello thanks for reply. .

well the problem has become more larger even my windows is also not booting. :(
one more thing i want to ask is that my installation is wubi type ... so will the wubi ubuntu will be deleted if i will format my windows ?

---

### Post by Rubi1200 on 2011-02-22
> will the wubi ubuntu will be deleted if i will format my windows ? 	
In a word, yes. Wubi uses a virtual disk inside the host system. If you format or reinstall Windows, Wubi will be gone.

But, before you go that far, did you read the information in the thread I linked to?

You should first post the results of the boot info script mentioned near the beginning of the main post.

---

### Post by Mark Phelps on 2011-02-22
MS Windows is not able to make sense of the internals of the Ubuntu install.  It just sees it as one big file. So, it won't be able to see any individual files or details there.  If that's what you're expecting to do -- see and/or manipulate your Ubuntu files from inside MS Windows, that's not going to work.

---

### Post by Rubi1200 on 2011-02-23
> If that's what you're expecting to do -- see and/or manipulate your Ubuntu files from inside MS Windows, that's not going to work.
Not entirely true. It is possible to read and copy files from the Wubi install from within Windows using [ext2read]("http://ext2read.blogspot.com/").

Manipulating files can only be done from a LiveCD/USB by loop mounting the root.disk.

---

