---
title: "Installation X Server problem"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by Gavner on 2006-11-20
Hey I've heard TONS of good things about Ubuntu and I want to try it out but every time i try to run the installer my screen goes goofy like this 


[IMG]http://img.photobucket.com/albums/v306/Gavner/S3500024.jpg[/IMG]


Anyone know what I need to do to get Ubuntu installed? I tried the safe graphic mode too but that didn't work either ](*,)

---

### Post by araz on 2006-11-20
try: > sudo dpkg-reconfigure xserver-xorg

---

### Post by dweez on 2006-11-20
Are you identifying your video card properly during setup?

---

### Post by Gavner on 2006-11-20
araz: when i try this i get 
[root@localhost Randy]# sudo dpkg-reconfigure xserver-xorg
sudo: dpkg-reconfigure: command not found
(i am currently running fedora)

dweez: I dont even get that far, I hit Install and i get that image

---

### Post by xtothez on 2006-11-20
Gavner, I had the same problem you are having with mine. I'm guessing its a video card issue (possible non-support) and talked with some forum admins and still have not got it to work, but you might:

[http://www.ubuntuforums.org/showthread.php?t=301929&highlight=x+server](http://www.ubuntuforums.org/showthread.php?t=301929&highlight=x+server)

thats the link, see if it helps

---

### Post by Gavner on 2006-11-20
None of those commands work for me in my terminal, and i have no rescue thing on my GRUB T_T

---

