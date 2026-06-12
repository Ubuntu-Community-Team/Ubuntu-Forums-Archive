---
title: "Help Needed with the Installing Ubuntu 5.10"
date: 2006-05-06
forum: Installation &amp; Upgrades
---

### Post by Muggi on 2006-05-06
When i install the Ubuntu 5.10 cd from Ubuntu i get the first screen where i can choose Desktop or Server but after that it loads some stuff in a dos like mode and then the screen goes black for a while and then it slowly turns white so i can't Install Ubuntu and when i try the Live version the same stuff comes up. CAN ENYBODY PLEASE HELP ME???.:confused: 

My Laptop is:
HP Pavilion zd8000 / zd8303ea
10 GB to install Ubuntu
ATI Mobility Radeon X600
ACPI Multiproessor PC
Intel(R) Pentium(R) 4 CPU 3.00GHz
512 Ram
:-(

---

### Post by neouser99 on 2006-05-06
you are the second or third person i have seen with trouble using the x600 Radeon... you can search around and join the others, there seems to be a problem with that hardware.

-neo

---

### Post by r4ik on 2006-05-06
You could try this seems to work,

[http://www.ubuntuforums.org/showthread.php?t=168263&highlight=ATI+Mobility+Radeon+X600](http://www.ubuntuforums.org/showthread.php?t=168263&highlight=ATI+Mobility+Radeon+X600)

It is a bit of a read hope it works for you.

Good luck !

---

### Post by Muggi on 2006-05-06
Thx but the link u gave me is for the wrong problem. His problem is in the program after install. My problem is before install or during install.
But Thanks for your help.

---

### Post by r4ik on 2006-05-06
I am sorry misread your post guess i should have finished cooking first :)

---

### Post by confused57 on 2006-05-06
Do you just press "enter" for the desktop install?

I think you have to type in "server" for the server install.

Never seen this problem before....interesting.

Somebody may have seen this before, and can get you started...

---

### Post by Muggi on 2006-05-06
[QUOTE=confused57]Do you just press "enter" for the desktop install?

I think you have to type in "server" for the server install.

Never seen this problem before....interesting.

Somebody may have seen this before, and can get you started...[/QUOTE]


Yes i have typed server, expert, linuxvga and so on but it is the same outcome.
Thanks for your reply.:sad:

---

### Post by r4ik on 2006-05-06
Try this one please,

server apci=off, hw-detect/start_pcmcia=false, vga=771

---

### Post by Muggi on 2006-05-07
[QUOTE=r4ik]Try this one please,

sever apci=off, hw-detect/start_pcmcia=false, vga=771[/QUOTE]


That's the line i have been looking for Thank You for your help. :D 
But now i am past the install and trying to login but Xserver is not working because of the video card i think. :-(

---

