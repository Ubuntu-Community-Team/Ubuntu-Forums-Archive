---
title: "Using Installed Programs"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by badogg on 2006-02-22
Hey all..  First question from the ultimate noob <= Me!! :( 

So I got Ubuntu running on my new Fujitsu Lifebook N3520 laptop.  And got the wireless working at both home and work.  The question I have is that I have used sude apt-get install <package> to isntall numerous things such as firestarter, xine-ui, etc...  but I don't see them anywhere to use them.  I'm sure it is due to my M$ Windows habits, but I have searched all of the menus and don't see them.  Anybody have any suggestions??

Thanks much..

---

### Post by shams2 on 2006-02-22
search for the program you just installed, for ecxample:
whereis firestarter
if it is installed , you will see the path to the program and then add to the panel for easy access.
if the output is without the path to the program, the program is not installed.

---

### Post by badogg on 2006-02-23
That's a bummer..

I see a lot of things I like.  But installing something and it not putting it in one of my menus,  and other things that don't seem that friendly, configuration wise, are getting a little frustrating.  Hopefully that is just me not being used to all of it.. :???: 

Well, thanks anyway - I appreciate the assist..

---

### Post by Rumor on 2006-02-23
[QUOTE=badogg]Hey all..  First question from the ultimate noob <= Me!! :( 

So I got Ubuntu running on my new Fujitsu Lifebook N3520 laptop.  And got the wireless working at both home and work.  The question I have is that I have used sude apt-get install <package> to isntall numerous things such as firestarter, xine-ui, etc...  but I don't see them anywhere to use them.  I'm sure it is due to my M$ Windows habits, but I have searched all of the menus and don't see them.  Anybody have any suggestions??

Thanks much..[/QUOTE]

Two things you might try. I had a problem the first time I installed Pan (a newsreader). It didn't show up in the applications menu anywhere. I tried the following and it worked.
```
sudo killall gnome-panel restart
```
After it restarted, the program showed up in the internet program group.

Failing that, you can make your own starters. If you know the command to start the program, you can click applications | system tools | applications menu editor. Select the appropriate program, say Sound & Video for xine and select new entry. Put in the name of the program, and the command for starting it. Choose an icon and and click ok.

---

### Post by xhie on 2006-02-24
You can always install the Debian Menu, it shows all your installed applications. I dont know if you can install it all by itself as I installed it with automatix, but it definity helps make things a little more easy to find

If you just installed ubuntu and havent taken a look at [Automatix]("http://www.ubuntuforums.org/showthread.php?t=80295") yet you probably should, it makes alot of stuff easier.

---

