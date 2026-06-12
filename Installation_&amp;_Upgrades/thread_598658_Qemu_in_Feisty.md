---
title: "Qemu in Feisty"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by opakedragon on 2007-10-31
ok I am trying to install Windows XP in a virtual environment I used Add/Remove... in the app menu to install Qemu. Now I can access it from the app>>accessories menu with the Qemu Launcher. I figured I'd look to see if there were any tutorials but since I am new to Ubuntu I am a little confused. 

When I found [this]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") URL I was hopeful but I am unclear as to where to begin. I don't know if what I have done already constitutes as step one or further.

I would appreciate the help.

---

### Post by opakedragon on 2007-10-31
I forgot to mention I have tried to used the Qemu from the GUI (creating a new 20GB image for  hard disk 0 in my home folder and checking Use CD-ROM and clicking Launch) but it gets to 52% formatting of the "drive" and freezes up. I figured that I must need to do something other than just use Add/Remove... to install Qemu, but I know not what.

---

### Post by sfunk1x on 2007-10-31
Follow the directions in this link:

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

---

### Post by opakedragon on 2007-11-01
I kind of need to bump this because this guy didn't help and he's not responding to my PM. I would appreciate anybody's help that doesn't just post a link I posted a question about. Thanks.

---

### Post by opakedragon on 2007-11-20
does anyone know the answer to this?

---

### Post by ruibernardo on 2007-11-20
That webpage is very clear. Resuming it, you need to install qemu, compile/install (module-assistant) the kqemu module, add the users to the kqemu group, create the image of the hard disk, etc. 

Read and execute that page line by line until you get to "10. Create a virtual drive for Windows". At this point, you can do all the rest with qemu-launcher.

Another more easy alternative to qemu is virtualbox. Try it if you're not comfortable with qemu and qemu-launcher.

---

