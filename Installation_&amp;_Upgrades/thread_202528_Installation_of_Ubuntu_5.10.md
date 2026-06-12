---
title: "Installation of Ubuntu 5.10"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by Kapetan on 2006-06-23
Hello

I hope I pointed at the right place for my problem with ubuntu installation :)

I have installed Ubutnu 5.10 ver. on my computer but I have a problem. When I log in, I have only mouse pointer and nothing else! No background, no any application nothing! And I must reset my computer.

There is another problem. When computer displays fields for user name and password, near the fields I have options: Language and Session. When I click on any option my PC becomes unusable.

I have tryed to install it again on hdd, but with same problem. 


Can anyone help me? While installing I had to choose between some kernel's and I selected i386 kernel.

I have P4 and MSI motherboard.

---

### Post by aysiu on 2006-06-23
Maybe this might help:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by Kapetan on 2006-06-23
Nothing for me...but tnx. for trying :)

Anyone else? Any suggestion?

---

### Post by zxee on 2006-06-24
Maybe try opening a shell  (Alt + Ctrl +F1) then type dpkg-reconfigure xserver-xorg <enter>
That will give you a chance to reconfigure your xserver i.e video card, keyboard, mouse, & monitor.

---

### Post by aysiu on 2006-06-24
[QUOTE=zxee]Maybe try opening a shell  (Alt + Ctrl +F1) then type dpkg-reconfigure xserver-xorg <enter>
That will give you a chance to reconfigure your xserver i.e video card, keyboard, mouse, & monitor.[/QUOTE]
That was suggested in the link above, too, but apparently it does nothing for Kapetan.

Maybe instead of saying "nothing for me," you can explain exactly what you tried and exactly what errors (if any) you encountered?

"Nothing for me" doesn't really help us help you.

---

### Post by Kapetan on 2006-06-24
[QUOTE=aysiu]That was suggested in the link above, too, but apparently it does nothing for Kapetan.

Maybe instead of saying "nothing for me," you can explain exactly what you tried and exactly what errors (if any) you encountered?

"Nothing for me" doesn't really help us help you.[/QUOTE]


Ok i'll tell you :)

When I log in, I have only orange color and nothing is working. ctrl+alt+F1 or ctrl+alt+F2, I can't log in as root .... nothing at all!.... and the other things which I posted above.

In one other forum I have been sugested to use KDE not GNOME but I don't know how. I am totaly begginer in this job (because I'm full with WIN shits :-k )

sorry for my grammar mistakes ;) 

greetings from Montenegro

---

### Post by aysiu on 2006-06-24
Okay. The fact that Control-Alt-F1 and Control-Alt-F2 aren't working is really bad. Is your mouse frozen? Can you do anything or is it orange and frozen, too?

Try booting into recovery mode (this will log you in as root) instead of regular mode and then trying the ```
dpkg-reconfigure xserver-xorg
``` command (you won't need a leading *sudo*, since you'll already be root).

**Back up** any files you modify. For example, ```
cp /etc/X11/xorg.conf /etc/X11/xorg_backup.org
nano /etc/X11/xorg.conf
```

---

