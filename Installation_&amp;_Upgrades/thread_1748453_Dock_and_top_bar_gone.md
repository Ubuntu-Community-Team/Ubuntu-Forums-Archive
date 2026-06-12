---
title: "Dock and top bar gone"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by stevenmelgar on 2011-05-03
i just upgraded to ubuntu 11.04. I went into my setting and and accidentally clicked the wrong thing. Now the dock on the left hand side and the bar on top are gone and I can't figure out how to get them back. Trouble is, I can't even open anything now. Is there anyway I can restore it?

---

### Post by dino99 on 2011-05-03
logout then login again

if that dont work, into a terminal:

unity --replace &

---

### Post by stevenmelgar on 2011-05-03
I can's log in and log out or get into terminal unless there are some sort of keyboard shortcuts you can tell me.

---

### Post by bezgoan on 2011-05-04
I have experienced the same problem. After playing around with compiz settings I am not seeing the dock bar and top bar, basically not able to perform any opertions on the comp.
After multiple trials found that Ctrl + Alt + F1 would give me command prompt with tty1 terminal. Please help if any the recovery is possible from this point ?

---

### Post by beew on 2011-05-04
It looks like you have disabled Unity. Right click anywhere to create a new folder, open it and choose "File System" from the left panel, then go to /usr/share/applications to find the ccsm, you can click to open it and re-enable Unity ( find it under Desktop section  and check the box)

---

### Post by bezgoan on 2011-05-04
Thanks beew, that would have worked is my gut feel.
Prior to seeing your response I did the following from terminal and on restart everything seemed fine.

1) unity --reset
2) unity --reset-icons
3) gconftool-2 --recursive-unset /apps/compiz-1
    unity --reset.

Thanks
Shashank.

---

### Post by ankitmeena on 2011-05-04
it looks like like you have uninstalled unity in 11.04 go to filesys/user/appli/compiz and re enable unity

---

### Post by manish_jain on 2011-06-14
One way of launching anything is right-clicking on the desktop, Create New Launcher and then type firefox or gnome-terminal in the command box. However, I am stuck with the same problem as above and even unity --replace isn't helping !!

---

