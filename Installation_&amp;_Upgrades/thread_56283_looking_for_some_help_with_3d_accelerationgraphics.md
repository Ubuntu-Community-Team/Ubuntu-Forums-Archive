---
title: "looking for some help with 3d acceleration/graphics"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by yellowband on 2005-08-12
hey everybody

i've been poking around the forums and guides but i can't really find the help i need.  Basically i'm new to linux and have just installed the current stable version.  I'm having troulbe getting the screen magnifier to work,when i load it, my computer "beeps" and no magnification occuers, but the program menu does load.  

I'm wondering if it has to do with inadequate graphics drivers/setttings?  i'm using an ATI radeon 9800 SE,with resolution set to 600-800.  How do i know if i have the latest version of drivers installed?  how do i know if i have my 3d acceleration workng properly?  does openGL come with ubuntu or do i have to do something extra to get it wokring? thanks for the help guys

---

### Post by drummer on 2005-08-12
[QUOTE=yellowband]hey everybody

i've been poking around the forums and guides but i can't really find the help i need.  Basically i'm new to linux and have just installed the current stable version.  I'm having troulbe getting the screen magnifier to work,when i load it, my computer "beeps" and no magnification occuers, but the program menu does load.  

I'm wondering if it has to do with inadequate graphics drivers/setttings?  i'm using an ATI radeon 9800 SE,with resolution set to 600-800.  How do i know if i have the latest version of drivers installed?  how do i know if i have my 3d acceleration workng properly?  does openGL come with ubuntu or do i have to do something extra to get it wokring? thanks for the help guys[/QUOTE]
 OpenGL comes with Ubuntu, but there is no 3d accelleration, it is all done through software. You will need to install the ATI drivers to get 3d accelleration through the graphics hardware.. search the forum for 'ATI drivers', there are a couple HOWTOs and different methods for installing the drivers, one may suit your card more than another.

As for the magnifier, I'm not sure. Try running the program from a terminal (Applications > System Tools > Terminal) and see if there are any errors when you run it.. they can give you a better idea of what specifically needs fixing.

---

### Post by yellowband on 2005-08-12
i see, thanks for the help

I had a look at one of the how-to guides to install the ATI drivers and it seems awfully complicated.  I think it is just this sort of thing that scares people away from linux and cuases them to stick with windows (nothing beats double clicking an icon to install... except apt-get).  ATI needs to have their drivers on apt-get or something.

GUess i'll re-read the how-to and take a crack at it.  Thanks again.

---

### Post by jyank on 2005-08-12
[QUOTE=yellowband]i see, thanks for the help

I had a look at one of the how-to guides to install the ATI drivers and it seems awfully complicated.  I think it is just this sort of thing that scares people away from linux and cuases them to stick with windows (nothing beats double clicking an icon to install... except apt-get).  ATI needs to have their drivers on apt-get or something.

GUess i'll re-read the how-to and take a crack at it.  Thanks again.[/QUOTE]

Try using this one:

[http://ubuntuforums.org/showthread.php?p=297700#post297700](http://ubuntuforums.org/showthread.php?p=297700#post297700)

Page 17, post by Epskampie, it's a very nice step by step

---

### Post by yellowband on 2005-08-12
cool, thanks for the link, i'll go ahead and give that a try

on a side note, i ran glxgears and i'm getting a frame rate around 340 fps, could this crappy fram rate be the reason why the screen magnifier is not working properly?

---

### Post by yellowband on 2005-08-14
hey thanks for the link,it worked very well and easy.  I'm having one more problem. i can't seem to change the resloution from 640x480.  any ideas?  one thing i was thinking was that i just chose the default vert and horizontal scan rate because i don't really know what to set them to.  thanks for any help.


PS: screen magnifier still isn't doing anything when i run it (booo). i even tried to uninstall and reinstall it.... nothing.

---

