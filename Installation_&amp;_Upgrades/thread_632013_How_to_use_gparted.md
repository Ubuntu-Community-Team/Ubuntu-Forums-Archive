---
title: "How to use gparted"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by ubiubi on 2007-12-05
Hi all

I have a dual boot system XP/ubuntu. I have been trying to install other derivatives (edubuntu and kubuntu) with no success. I was wondering if it would be possible to create more partitions on my disk and then install them from their respective ISO disks. When I booted up gparted from its cd I was faced with a menue of about 8 things. No idea really which was the most appropriate so I chose the first. It then informed me that the software used a graphical interface and that this was not possible on my system. It suggested that I FORCE the GRAPHICAL MODE or some such thing. It then left me at the G: prompt. What commands can I use to do this?


Any advice on what I'm trying to achieve would be greatly appreciated. I'm already taking part in a thread for the derivatives installation!

---

### Post by ubiubi on 2007-12-05
Hi I have a dual boot xp/ubuntu hard drive. I want to create more partitions to install edubuntu and kubuntu. The normal methods, despite forum advice are defeating me. I booted up gparted and I chose the first option in the menu( really just guessing) It then informed my the package operated from a graphical interface and this wasn't possible on my computer. But I couldl FORCE GRAPHICS to continue. It then left me at the G/ prompt (presumably to force graphics) Any suggestions for suitable commands. I have absolutely no idea what I should do or type. Secondly can I create more that four partitions on a typical disk and is it advisable?

Many thanks foer reading this

---

### Post by kelvin spratt on 2007-12-05
You need to use the Gparted Live CD from here [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
This will allow you to unmount your partition you can then resize and make new partitions. You also need to read about primary and extended partitions as you are limited to 4 partitions on a primary. But its unlimited on a extended.

---

### Post by logos34 on 2007-12-05
Why don't you just get the (edu)(ku)buntu desktop metapackages?  Then it gives you a choice on the login screen.

sudo apt-get install kubuntu-desktop
sudo apt-get install edubuntu-desktop

---

### Post by ubiubi on 2007-12-05
Yeah! I've tried the meta package rout and it never installs properly. I have the gparted iso disk (It is the live version). I really need to know which option is best for me on the gpârted initial menue and how I can "force video" from the g/prompt. Thanks for the tip on extended partitions. I'll look into it!

---

### Post by Herman on 2007-12-05
The menu you get is about what kind of graphics (video) driver you require. 
For most computers you can let GParted automatically decide for itself, (the first option), but if you have a special video card you can specify exactly what driver you want to use. 
If X fails to start you use the 'forcevideo'  script, so you have to type that at the terminal and it will ask you which video driver you want, usually I type 'vesa', which is the generic video driver. Then it asks for resolutions. That depends on what kind of monitor you have. 1024x768 is standard. Most monitors are 75% as high as they are wide. If you have a widescreen monitor then yours might be different.
Then if you're lucky this time 'x', your graphical user interface, should start and you can use GParted.

Regards, Herman :)

---

### Post by Pumalite on 2007-12-05
[http://ubuntuforums.org/showthread.php?t=632013](http://ubuntuforums.org/showthread.php?t=632013)

---

