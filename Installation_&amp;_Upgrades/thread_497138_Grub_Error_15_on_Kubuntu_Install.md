---
title: "Grub Error 15 on Kubuntu Install?"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by fragility14 on 2007-07-09
I am trying to install Kubuntu onto a computer which previously had Ubuntu, due to some problems I cant seem to be able to solve, I am trying things with a new desktop environment,. However, when I try to install Kubuntu the live cd works great, but at 70% installed it restarts the computer like it is finished and when it tries to load there is a grub error. I had two partitions with only one set to root, figuring i could put a partition for files I wouldnt want to reformat if I change OS again, and now it simply wont work, I cant get Kubuntu installed. Going to try to reinstall Ubuntu and see if it goes. This wouldnt be because of two partitions is it? One is root and there other is sda/media

I will get back to you all about whether Ubuntu installs ok or not.


I've tried totally deleting the partitions and then starting again but it stops in the same place with the same error. And the thing is it starts shutting down, it doesnt just freeze..

any help would be appreciated.

---

### Post by merlinus on 2007-07-09
Did you check the install cd for errors?

-merlin

---

### Post by fragility14 on 2007-07-09
yes, CD integrity is fine, I checked it.

Ubuntu reinstalled without a hitch.

I am having performance issues however, and simply havnt been able to get the help I desire I think I can work with KDE better, esp since most programs I like seem native to KDE

---

### Post by merlinus on 2007-07-09
You can easily install kde from ubuntu:

```

sudo aptitude update && sudo aptitude install kubuntu-desktop

```

kubuntu uses more resources than ubuntu.  xubuntu uses less than both.

-merlin

---

### Post by Odrodzona-Sarmacja on 2007-07-10
Try changing partition to fat32 and then low format it. Only then you can install your Ubuntu again.

---

### Post by Odrodzona-Sarmacja on 2007-07-10
> **merlinus said:**
> You can easily install kde from ubuntu:

```

sudo aptitude update && sudo aptitude install kubuntu-desktop

```

kubuntu uses more resources than ubuntu.  xubuntu uses less than both.

-merlin

Why not "kdebase"? It uses resources like xubuntu.

---

### Post by kirillt on 2008-02-21
Have seen this error after the last two Kubuntu installs.   Turns out that the grub menu file, menu.lst, was missing from the /boot/grub directory.  Copying the default example menu.lst from the grub doc directory into /boot/grub solved the problem.   

Details:
After the installation completes:
1. Open the terminal (Alt-F2; type "konsole", enter)
2. In the terminal, type: sudo cp /usr/sare/doc/grub/examples/menu.lst /boot/grub
3. Press enter (you may have to enter your password as well)
4.  If cp cannot find the menu.lst (get error like "cp: cannot stat ..."), type this in terminal:
    sudo updatedb;
    sudo locate menu.lst
    you should get dome string ending with /something/menu.lst 
   Now use this in the copy command: sudo cp /something/menu.lst /boot/grub

---

