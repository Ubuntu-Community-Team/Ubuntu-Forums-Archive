---
title: "Changing the OS Order"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by puner on 2007-09-08
Hello,

I installed Ubuntu 7.04 on a 10GB USB enclosure drive that I had laying around. But, I have a little problem with how it made Windows Xp as my "Other Operating Systems". I want to use WinXp as my primary OS, and when i want to go play on Ubuntu I still have the option to do so.

[[IMG]http://imagenerd.com/thumbnails/th_dsc07785NOEz.jpg[/IMG]](http://imagenerd.com/show.php?_img=dsc07785NOEz.jpg)

Also, I removed my enclosure to see if WinXp would boot now that my computer could not see the linux OS, and i got a error having to do with "GRUB" :S

So, what are the correct steps to formatting my 10GB drive and removing Ubuntu off it, so that WinXp is my one and ONLY OS, and it boots automatically.

-Thank You

---

### Post by Pumalite on 2007-09-08
Use Gparted for the erasing and formatting and Super Grub for restoring Windows to MBR

---

### Post by puner on 2007-09-08
Thanks for the quick reply. Do you know the answer to the first part of the question? About OS order?

---

### Post by Pumalite on 2007-09-08
I thought you just wanted winblows in your computer.

---

### Post by puner on 2007-09-08
Read it again, i still want ubuntu

---

### Post by merlinus on 2007-09-08
/boot/grub/menu.lst

count number of lines that begin with title down to windows, and subtract one.

Change the line that says 

default 

near the top of the file to that number.

to edit:

```

gksudo gedit /boot/grub/menu.lst

```-merlin

---

### Post by puner on 2007-09-08
> **merlinus said:**
> /boot/grub/menu.lst

count number of lines that begin with title down to windows, and subtract one.

Change the line that says 

default 

near the top of the file to that number.

to edit:

```

gksudo gedit /boot/grub/menu.lst

```-merlin

Thanks for the reply Merlin. But could you be more noob friendly, this is my third day using linux >< :)

---

### Post by Pumalite on 2007-09-08
Grub starts counting from 0

---

