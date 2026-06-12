---
title: "Problem with Nvidia drivers"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by A1RIES on 2007-12-04
Hello everyone,
This is my first experience with linux and i must say..i am impressed. I am however having one problem,when i go into:System,Preferences,Appearance and i go to set my visual effects on extra it tells me i must enable the driver, When i agree to enable the driver it tells me "The software source for the package nvidia-glx-new is not enabled. If anyone has any ideas please enlighten me, Thanks in advance.

---

### Post by gazj on 2007-12-04
Hi There, glad you like what you see, and thers plenty more to see yet trust me.

Go to System > Administration > Software sources

Tick the propriearty drivers (restricted) download source. (it's not a bad idea to tick all other boxes while there)

click close and try again :)

Also untick the cd-rom if you have a nice fast internet connection, saves you having to put cd in when you want to install some things.

---

### Post by A1RIES on 2007-12-04
Thanks alot, i got it working using your suggestions. One other thing, i am running a dual boot configuration with windows vista and on my desktop there is a hard drive icon but when i click on it it brings up my vista partition.Any ideas?

---

### Post by gazj on 2007-12-04
Glad it helped

yeah it's just a link to the files on your windows partition, would you like it removed?? I don't dual boot, but people have told tales of corrupting ntfs windows partitions when editing files etc in them so not sure it's a good thing to have around.

if so there are probably graphical ways of doing i find editing text files easier.

open a terminal - to do this press alt+f2 - type gnome-terminal (or go applications > accesories > terminal)

in the command prompt type

```
sudo gedit /etc/fstab
```

a editor should appear with some text in (basically tells ubuntu what filesystems to make available on bootup)

there should be a line that corresponds to your window partition (if it's the first partition on the first  disc it will probably start /dev/sda1, also there will be other clues like ntfs in the line)

please don't get the wrong line if unsure paste the contents in the forum and i will tell you what line (you system may not boot if you get the wrong one)

once you are sure of the right line just pur a # in front of it, this will turn the line in to a comment and it will just be ignored.

now just click save

on reboot you should no longer have your vista partition available

you can always take the # out if you want access back to it.

---

### Post by gazj on 2007-12-04
just read your question again

if you are looking for the top of your ubuntu partition just click places > computer > filesystem

this is your ubuntu partition and what it looks like

please don't be worry if the structure looks like madness, you probably don't need to know as a new user just using the system, and if you do want to know, it will make sense in time, in fact in time it makes perfect sense, and the windows filesystem baffles you, lol

---

### Post by Pumalite on 2007-12-04
ttp://www.linux-tutorial.info/index.php
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)

---

### Post by A1RIES on 2007-12-04
thanks for your reply, I am just trying get that icon off of my desktop but still be able to access vista at anytime.Is there anyway i could just put a shortcut of my linux folder on my desktop and remove my vista partition? I am a windows it technician but this is alot different to work with.

---

### Post by gazj on 2007-12-04
if you need that bit more of a windows feel try this

alt+f2

gconf-editor then enter

drill down through apps > nautilus > desktop 

untick volumes-visible this will remove the vista partition icon (or should do i haven't got one to try)

tick all other icon's you may want on your desktop as nesesary

while we are on the subject of links above ^^ one i still reference to and was a god send when i first started to ubuntu [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

snap - windows it tech too, what i'd give to be a linux one tho, lol, the time will come

---

### Post by A1RIES on 2007-12-04
That is exactly what i was looking for,I appreciate all of the help and the links for further education ;). If i have anymore questions i will let you know.

---

### Post by gazj on 2007-12-04
abs no probs - happy to help - catch me on msn if you get really stuck, i really have no problems helping people out, as do we all here i guess.

Have fun !!!!

---

