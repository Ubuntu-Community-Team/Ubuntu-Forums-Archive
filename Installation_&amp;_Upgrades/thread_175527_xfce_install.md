---
title: "xfce install"
date: 2006-05-13
forum: Installation &amp; Upgrades
---

### Post by pillu on 2006-05-13
i am running ubuntu breezy for some time now on my P2 192 MB RAM laptop. The default GNOME runs too slow. I heard that xfce is a nice lightweight desktop. Could someone tell me how I install xfce with a lightweight window manager (IceWM??) without doing a full install all over again. It would be nice to know how to uninstall Gnome, just to save some precious space.

---

### Post by richbarna on 2006-05-13
Hi pillu,
I did the same on my laptop, here's how to install xfce:-
Open your console and type :-
>  sudo apt-get install xfce4 
And to uninstall the ubuntu-desktop:-
> sudo aptitude remove ubuntu-desktop

You can actually leave the Ubuntu/Gnome desktop on the computer, and when you boot up and get the start menu, just click the "session" button and choose "xfce"

---

### Post by aysiu on 2006-05-13
I don't think using *aptitude* to remove Gnome will work unless you used *aptitude* to install Gnome in the first place.

If you're not hard up for disk space, though, you shouldn't need to remove Gnome. Its existence on your hard drive won't make XFCE slow.

To install XFCE, follow these directions:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by pillu on 2006-05-13
thanks for the help...my xubuntu is up and running and works muuuuccchh faster than gnome...one more query....how do i add the trash and the terminal buttons to the pane...they are not there in the add new items list

thanks

---

### Post by aysiu on 2006-05-13
[QUOTE=pillu]thanks for the help...my xubuntu is up and running and works muuuuccchh faster than gnome...one more query....how do i add the trash and the terminal buttons to the pane...they are not there in the add new items list

thanks[/QUOTE] Aye, there's the rub.

XFCE is a lightweight desktop environment, but it's not as fully-featured as Gnome or KDE. The trash thing is a big issue with no easy solution. One way around it is to run Nautilus within XFCE. This will allow you some of Gnome's file management while you retain the speed of XFCE.

Another way to do it is just to do without the trash and delete files or move them manually to the ~/.Trash folder and empty that folder from time to time.

There's an easy way to get the terminal launcher on the panel, though. Just right-click > Add new item > launcher > for the command, use ```
xfce4-terminal
```

---

