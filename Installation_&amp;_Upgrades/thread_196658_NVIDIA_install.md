---
title: "NVIDIA install"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by DeaducK on 2006-06-14
i have an nvidia geforce 5200 graphics card.
some one told me to change my ubuntu settings by making the drivers
from nv to nvidia after downloading the driver,but this caused my linux to stop starting. then he told me hwo to change it back from the recovery startup, and rewrite the file of the driver, and fix the problem

he told me that changing that will improve my ubuntu experence 10 folds, cuz the graphics was then really really good.

now can anyone help me and tell me what went wrong then? and give me instructions on how to change the nvidia driver so as to make my graphics card perform better?

if anyone has information regarding this, i would be very greatfull if you would help a new b out a little

cheers

---

### Post by tronica on 2006-06-14
try this guide

[http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Graphics_Driver_.28NVIDIA.29](http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by DeaducK on 2006-06-14
Thankx, but my ubuntu stopped starting
can anyone plese tell me how to fix this problem i.e. change the nvidia back to nv in the xorg.conf file? throught ubuntu recovery option perhaps?

and can anyone tell me , after that, how i can get nvidia istalled other then the one give above?

---

### Post by AsGF2MX on 2006-06-14
I'm new to Ubuntu and after mucking about with CLI stuff for quite a while (pre Ubuntu), I finally see a fancy gnome from Ubuntu...quite a refreshing  change :D.

I setup Ubuntu and messed up the nvidia stuff as well, X seems to load fine but the terminals all result in my LCD being off (I'm on an Inspiron 9300 with a 6800Go) but I managed to get into safe mode without issue. If you want, you should be able to restore the copy of the x11.conf file  that's left by the nvidia-x-config (or whatever it was).

I am going to run through the guide and see if I can get it running and I also replaced the i386 kernel with the i686 one...hope this won't cause any problems.

---

### Post by DeaducK on 2006-06-14
im sorry....uh...what do i do? :confused:

---

### Post by AsGF2MX on 2006-06-14
Ok, after a bit of twiddling around, I  got the nvidia drivers to work (glxgears reports in excess of 10K fps :-P ) but it seems that I've lost access to all the terminals again (trying to figure out what causes it and  how to get it back). I backed up the x11.conf file at the beginning. Did you?

---

### Post by DeaducK on 2006-06-14
no, but i know the changes i made. i just changed it from nv to nvidia
i just dont know how to open it and save it

---

### Post by AsGF2MX on 2006-06-14
Oh, that? Have you used vim before? 

assuming you're in as root, type 

"vim /etc/X11/xorg.conf"

if not, add sudo to the front. 

From then, basic commands for vim:
press ":" to issue commands such as save  (so to save something, you would do ":w" and to quit you would do ":q" and to save and quit you'd do ": x". (when you've pressed : , you will see the ":" symbol at the bottom of the screen)

To modify anything use the arrow keys to move around, press "i" to insert, it'll display the word insert at the bottom" then work as if you normally would. Make sure you press escape to come out of insert mode before issuing commands such as save and quit , etc.

---

### Post by tseliot on 2006-06-14
Please, read this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by DeaducK on 2006-06-14
thanx asgf2mx. i fixed it! :D

---

### Post by AsGF2MX on 2006-06-14
no prob DeaducK

A little off topic but tseliot, I looked in your guide but there is no mention there about my disappearing terminals. Any suggestions? X works fine but jumping to terminals result in my LCD being off (as mentioned, on a Dell Inspiron 9300, WUXGA panel), as if the output is being redirected to another one of the connections but having no other monitor around makes it difficult for me to pin down what's going on.

---

### Post by tseliot on 2006-06-15
[QUOTE=AsGF2MX]no prob DeaducK

A little off topic but tseliot, I looked in your guide but there is no mention there about my disappearing terminals. Any suggestions? X works fine but jumping to terminals result in my LCD being off (as mentioned, on a Dell Inspiron 9300, WUXGA panel), as if the output is being redirected to another one of the connections but having no other monitor around makes it difficult for me to pin down what's going on.[/QUOTE]
If by jumping to terminals you mean when you press CTRL+ALT+F1 (F2, etc.)

then you might want to try point 13 of the Problems Section of that guide of mine

---

### Post by AsGF2MX on 2006-06-15
I was wondering if that was it but I got tired and fell asleep last night. Woke up this morning, saw your post, tried it and it did the trick but I'm still a little puzzled why a splash screen would cause such problems? It's only when X starts that the ttyN goes away but up until then, it works. Now to continue setting up the rest of the system.

---

### Post by tseliot on 2006-06-15
[QUOTE=AsGF2MX]I was wondering if that was it but I got tired and fell asleep last night. Woke up this morning, saw your post, tried it and it did the trick but I'm still a little puzzled why a splash screen would cause such problems? It's only when X starts that the ttyN goes away but up until then, it works. Now to continue setting up the rest of the system.[/QUOTE]
If you want you can put "splash" back and add "vga=792" and see if it works

---

### Post by AsGF2MX on 2006-06-15
If I recall correctly, it was 792 but I'll check in a little while.

---

