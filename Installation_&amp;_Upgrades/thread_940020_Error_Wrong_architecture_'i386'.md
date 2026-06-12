---
title: "Error: Wrong architecture 'i386'"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by little cazy on 2008-10-06
yo, i've try to install a number of different applications through .deb files, however every time i try to install then the same error (Error: Wrong architcture 'i386'). i have no idea what that's even means, however i think it might have to do with the fact i'm running a AMD processor.

---

### Post by norgur on 2008-10-06
seems like you have got an Ubuntu64, so some programs won't appreciate that... when installing, just start the setup through **linux32** i.e.:
```
sudo linux32 dpkg -i iwanttoinstallthiscrap.deb
``` ;)

---

### Post by lazyart on 2008-10-06
Ideally, locate an AMD64 version of the .deb file you are trying to install.

---

### Post by norgur on 2008-10-06
that would be too easy ;) but indeed the most optimal way...

---

### Post by Penguinsunite on 2008-10-06
Hey guys, i had some of the same problems, but when i tried to install emacs22 from terminal, i got that same message in terminal format, and then my computer locked up when i tried to do it through add/remove apps. so i flicked the switch on the back of the computer, and turned it back on. then, i couldn't even get to the login screen, it kept saying fatal error, or one of the startup test failed. so i tried to do a reinstall through the live cd, and now the cd has a defect, and won't load. im creating another one, but for future reference, how do i solve the problem of insstalling programs without repeating this mistake?

---

### Post by jayson.rowe on 2008-10-06
Sorry, but I have to ask.

Are you sure whatever you are trying to install isn't already included in the repo's?

---

### Post by Penguinsunite on 2008-10-06
no, i wasn't sure, but how would i check that? i am a noob with this operating system.

---

### Post by jayson.rowe on 2008-10-06
There are two "GUI" ways - I'm assuming you are running Ubuntu (Meaning GNOME rather than XFCE in Xubuntu or KDE in Kubuntu - if you are running one of those - let us know).

Click "Applications" and then "Add/Remove..."

-or-

Click System -> Administration -> Synaptic Package Manager

Search for what you wish to install.

If you find it, tick the box, and install. Simple as pie!

:-)

---

### Post by Penguinsunite on 2008-10-06
thanks for the help. ill try it when i get a chance to and get back to you

---

### Post by little cazy on 2008-10-07
> **lazyart said:**
> Ideally, locate an AMD64 version of the .deb file you are trying to install.
i try to do that before but if their isn't one i just take it as the one's they're showing me that cover both of them, guess not.

---

### Post by kingafrojoe on 2008-10-13
i have also just found this same i386 error. i also have an AMD x64 processor running x64 ubuntu, and found the error when trying to install skype. 

i then attempted the CLI solution that was suggested but this kicked back an error of "file or folder does not exist" or something to that effect. 

any thoughts?

---

