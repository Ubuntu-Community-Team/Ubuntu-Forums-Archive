---
title: "Installing question"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by Jeremywilms on 2007-07-10
I have used D live feature, and there is an icon on the desktop saying "install" though I have a couple of questions before I press this button.

1.Will it overwrite my curret operating system?
2.If 1 is false, how do I accsess my previous operating system.
3.I have 39GB harddrive left. How much should I give to linux??

---

### Post by merlinus on 2007-07-10
1. no.  at the partitioning screen, you can select to use free space.

2. it will install grub, which will allow you to choose between your os'es.

3. depends on your "other os," which is???

-merlin

---

### Post by Jeremywilms on 2007-07-10
Sorry, my current OS is vista, yes I know it takes alot to run, I was thinking of jus giving ubuntu 10GB seeing as I am going to use an emulatore to run windows applications. Though I have another question, how does GRUB work?

---

### Post by merlinus on 2007-07-10
You will need to use vista's partition resizing tool before attempting to install ubuntu.  I also advise defragging several times first.

10G for / and 1.5G for swap will be enough.

grub is a boot loader that, when installed, will allow you to run different operating systems.  You can set the default to whichever one you like.

-merlin

---

### Post by Jeremywilms on 2007-07-10
I'm sorry I don't quite understand what you mean by (vista's partition resizing tool) I am currently defragging my computer right now though. Another question about GRUB. when does this tool display. Like right when your computer boots does it ask you what OS you want to boot. Or do I have to boot into a OS, and change setting then restart my computer?

---

### Post by merlinus on 2007-07-10
vista has a built-in disk resizing tool, which you will have to use because it has a dynamic disk feature.  The partitioner which is part of the ubuntu installation will not work.

Since I do not run that os, I cannot tell you exactly in what menu it is located.  Perhaps system tools?

grub loads at boot-up, and presents a menu where you can choose which os to run.

-merlin

---

### Post by Jeremywilms on 2007-07-11
Thaks

---

### Post by Odrodzona-Sarmacja on 2007-07-11
> **Jeremywilms said:**
> I have used D live feature, and there is an icon on the desktop saying "install" though I have a couple of questions before I press this button.

1.Will it overwrite my curret operating system?
2.If 1 is false, how do I accsess my previous operating system.
3.I have 39GB harddrive left. How much should I give to linux??

1. If you want it to.
2. After install during boot you will see during 3secs "press esc to access grub menu", but by default it won't have windows in it. In ubuntu in terminal you type "sudo mousepad /boot/grub/menu.lst", then you scroll down untill your see something like:

# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1

,then you just remove the "#" from before it and you have also windows and not linux booting by default. If you wish ubuntu to boot by default and not windows you have to change in the beggining of the file:

default		0

to

default		1

also you can change:

timeout		3

if three seconds is too short time for you.

3. 8gb to "/" ext3, 0.5gb to "swap".  14.5 gb to "/home/" ext3. Leave 15gb to "?:" fat32, so you get yourself some safe file storage partition, which in ubuntu will be accesible from /media/hdaX/ directory.

---

