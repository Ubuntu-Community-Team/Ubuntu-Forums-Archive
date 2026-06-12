---
title: "How can i replace between nautilus and other file managers?"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-06
i have installed lubuntu so now i have pcman file manager and i also have gnome commander is there a way to choose between them in gnome?

and also how can i change the deafult between  lxde and the previous one of gnome?

thanks in advance.

---

### Post by aviramof on 2010-03-06
no one knows?

---

### Post by seeker5528 on 2010-03-06
I found a link to this:

[http://lifehacker.com/288616/change-gnome-menus-to-use-pcman-file-manager](http://lifehacker.com/288616/change-gnome-menus-to-use-pcman-file-manager)

I'm not very big on making these kind of changes system wide if there is not a reason and there is an additional .desktop file that looks like you might want to change.

I did this on my system and it seems to work:

Browse to /usr/share/applications/

Select nautilus-home.desktop and nautilus-folder-handler.desktop

Browse to ~/.local/share/applications

Paste the files

I used dolphin for my test case, since I don't have PCFM installed. So in my case I edited the TryExec and Exec lines in nautilus-home.desktop to look like:

```
TryExec=dolphin
Exec=dolphin
```

And in nautilus-folder-handler.desktop to look like:

```
TryExec=dolphin
Exec=dolphin %U
```

Now if I click on anything in the first section of the places menu Home Folder, Documents, Music, etc... they all come up in dolphin.

I tried to copy nautilus-computer.desktop as well, but it still came up with nautilus unless I changed the original file.

```
TryExec=dolphin
Exec=dolphin /
```

That still leaves some things that come up with Nautilus, don't see a way around it, don't know why there is no option to choose your default file manager.

I think those Exec lines should work with just about any file manager you would prefer to use, just substitute the one you want. 

I didn't try the browse option in any programs, but I am thinking the nautilus-computer.desktop is setting a mime type for the folders so if an application uses the mime type instead of looking for a specific file manager should be covered by that when you are running Gnome.

Don't know about LXDE.

Later, Seeker

---

### Post by kansasnoob on 2010-03-06
I'm just a dumb hick from the sticks but I think you've said that Hebrew is read right to left, etc. Just many things are foreign to you and you want to find work-arounds, etc.

So I did just a quick web search and came up with this:

[http://www.mpthrill.com/peanut/](http://www.mpthrill.com/peanut/)

And NO I'm not suggesting you change distros! But I notice that uses KDE??? 

Have you tried KDE?

Aysiu did a great job explaining how to try different desktops here:

> Playing Around
KDE/Gnome Comparison
Install KDE
Install XFCE
Install IceWM
Pure Gnome
Pure KDE
Pure XFCE
Make your own Ubuntu remix 

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

I'm also not sure what your hardware limitations are but maybe Gnome just won't work for you. I tried many variaties before I settled on Gnome.

Aysiu did a great job explaining yhow to do a minimal install here:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

And it mentions:

[http://xwinman.org/](http://xwinman.org/)

---

### Post by aviramof on 2010-03-07
i did tried kde and lubuntu and lxde does look good maybe i'll reinstall it again with pcmanfm2 but my problem is not with gnome it's with nautilus it lack some options that i need.

1.auto arrange icons on desktop and you can't arrange by type by size and etc.

2.no default url support i always need to install it again as i need to do now because i'v just reinstalled ubuntu.

3.no option to edit system preference or managment entires.

and that i remember right not but i'm sure there are more things i need and nautilus don't provide like more right click options on 
desktop that you can find in the nautilus-actions page that be default.

---

