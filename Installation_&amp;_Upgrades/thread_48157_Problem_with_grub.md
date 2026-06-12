---
title: "Problem with grub"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by Irrekiet on 2005-07-11
Hello, 
I have  problem with ubuntu, and i whant to do a new instalation on a new drive, 
so i ask all of you how can i get grub uninstal so i can do a clean install off everything again! withou formating my disk ;) 

Tk u for all the help   \\:D//

---

### Post by JaM on 2005-07-11
You can do it with:
```

sudo apt-get remove grub

```

But that only remove the grub package. I think you mean removing grub from the mbr. Well you could zero it, but it doesn't matter, if you do a fresh install it will be renewed (with the same grub). There is no point in reseting the mbr nor replacing it.

If you are going to have 2 ubuntu linux distro's on 1 comp you have to edit /boot/grub/menu.lst in order to boot both.

---

### Post by JaM on 2005-07-11
You can do it with:
```

sudo apt-get remove grub

```

But that only remove the grub package. I think you mean removing grub from the mbr. Well you could zero it, but it doesn't matter, if you do a fresh install it will be renewed (with the same grub). There is no point in reseting the mbr nor replacing it.

If you are going to have 2 ubuntu linux distro's on 1 comp you have to edit /boot/grub/menu.lst in order to boot both.

---

### Post by Irrekiet on 2005-07-11
yes i want to remove it from the start up off my pc... tks for the help ;)

---

### Post by JaM on 2005-07-12
If you are going to install Ubuntu again there is no need for removing grub from your mbr. And what do you mean by "without formatting my disks"?

---

