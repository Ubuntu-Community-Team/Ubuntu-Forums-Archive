---
title: "gui questions"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by shinson71 on 2007-03-28
First thing to say is that I am completely new to linux. I recently loaded ubuntu version 6.10 server on a older Dell machine. I get a tan login screen that says ubuntu, however when i put in user name and password i get a tan window with a smaller black command prompt window in the upper left corner. Is this what your supposed to see or did i drop the ball on installation somewhere. I have no icons to do anything with. Please be gentle, with my ignorance in mind, when you answer. I started reading the documentation but without pictures of a default installation i don't know what to expect to see. Thank you for your help.

---

### Post by NeuralEskimo on 2007-03-28
My first thought is that you are missing a desktop. That is, you don't have gnome or KDE (properly) installed and the black screen is an xterm. In the initial login screen you should be able to choose a login session. When you click this button do you have any options? Sorry, to be vauge about the "button", but I run kubuntu rather than ubuntu. As a result, I am not familiar with the screen you have in front of you.

Anyway, if you have no options, type "sudo apt-get gnome-desktop" in the "black window" after you log in.

If that doesn't work, we can try some other things. 

Hope this helps...

---

### Post by shinson71 on 2007-03-28
thanks for the response. tried that and it tells me: "E: couldn't find package gnome-desktop"
I assume that means i goofed on the download. Where do i find the appropriate install files. thanks again ahead of time

---

### Post by NeuralEskimo on 2007-03-28
Ah, crap! I made a typo. The line should read:
"sudo apt-get install gnome-desktop"

Now give it a try.

---

### Post by NeuralEskimo on 2007-03-28
Did it again.  The line should read
"sudo apt-get install ubuntu-desktop"

---

### Post by shinson71 on 2007-03-29
that seems to be doing it. a lot of files installing now. thanks, i will check back in if that didnt fix it all the way. i appreciate it.

---

