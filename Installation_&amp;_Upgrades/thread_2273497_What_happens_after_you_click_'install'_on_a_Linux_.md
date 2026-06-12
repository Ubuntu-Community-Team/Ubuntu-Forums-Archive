---
title: "What happens after you click 'install' on a Linux Live XUbuntu USB?"
date: 2015-04-13
forum: Installation &amp; Upgrades
---

### Post by ross4 on 2015-04-13
That sounds like a dumb question but my real question is at what point can I abort the install without damaging any existing operating systems? There are many good sets of instructions on how to set up a live USB but I can't find anything that actually tells me what choices, if any, are going to be presented when I run 'install'.

i've done several installations from live CDs or USBs but the only one I remember clearly is the one that wiped out XP on my old Toshiba 5000 and replaced it with Lubuntu. Not a serious problem, actually, but one I don't want to repeat on my present laptop.

---

### Post by ross4 on 2015-04-13
[FONT=UICTFontTextStyleBody]A little clarification. My system is dual boot (XP & Xubuntu) so I want to control what happens to the various partitions. 
[/FONT][FONT=UICTFontTextStyleBody]
The hard-drive is formatted as follows:
/dev/sda1 , ntfs , , 63 GiB
/dev/sda2 , extended , , 48.79 GiB
/dev/sda5 , ext4 , /boot , 857.00 MiB
/dev/sda6 , ext4 , / , 9.54 GiB
/dev/sda7 , ext4 , /home , 36.32 GiB
/dev/sda8 , linux-swap , , 2.09 GiB[/FONT][/COLOR]

---

### Post by coldraven on 2015-04-13
If you watch this video then you'll see that at "Installation Type" if you don't select "Something else" there is no going back. AFAIK the installer starts formatting the disc immediately after that screen. If you do select "Something Else" you will go to the partitioner screen where I believe you can backtrack or abort the install. 
**Get a second opinion before you blame me for any disasters!**
Sorry about the music, I did not create that video :) 
[https://www.youtube.com/watch?v=Dv26_2bjyhY](https://www.youtube.com/watch?v=Dv26_2bjyhY)

---

### Post by ross4 on 2015-04-13
Ok! That brings back a vague memory. Can anyone confirm this?

---

### Post by ross4 on 2015-04-15
I went ahead and did a new installation using my live USB... and another and another (but that is a different story). The short answer to my own question above is that once you click 'install' you can move along to several different options and at some point in each you get a warning about the effects and can back out. I experimented with this on Ubuntu and Xubuntu live USBs so, it seems pretty safe to move ahead each step until you either feel your choice is ok and go ahead or go back if you are unsure, based on the warnings. On the other hand, when I tried the same experiment with a Mint live install from a CD, somehow I went a little too far and when I decided to go back, the installation had already done something to the disk.

---

