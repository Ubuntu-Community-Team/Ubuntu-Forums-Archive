---
title: "Couple questions about Karmic and alphas in general"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by monkeyKata on 2009-07-15
Hello all.

I installed Karmic alpha2 the other day to see how the new kernel runs, hoping to see improvements with Intel graphics specifically and everything else generally.  Graphics are again smooth on my laptop.

Today I ran the updates and now for some reason the windows borders are using Metacity again, as I had Emerald enabled.  In *compiz -> windows decorations * I have typed 'emerald --replace' yet it doesn't seem to have an effect.  I wanted to ask if anyone else noticed this, too.  I wonder how to fix it, or if there is a new default/command that needs to be changed.

Also, I no longer see any settings to change the login window (GDM) as we could in previous versions.  Is this under a new name with Grub2 and all, or is theming just not yet possible?  I saw another thread discussing a fix or update to Grub2... I have installed the alpha 2 from the 13th just two days ago.

So over the past two days I've had a ton of updates... are these testing releases basically updated daily with each new build?

So far things are running better with the newer kernal and the Intel 2.7 graphics driver, though I guess you can get these things through PPAs while sticking with Jaunty.

Thanks if anyone can clear any of this up.  Has Karmic been stable for you all?  Think it's best to stick with it?

---

### Post by Regenweald on 2009-07-15
To avoid the conflict in my case i simply removed metacity altogether. Hope this helps.

---

### Post by monkeyKata on 2009-07-15
Hey, thanks for the tip.  I added Emerald to the startup applications and restarted but this did not do the trick.  I didn't try removing Metacity, though, as I'm hesitant.  It never posed a problem before, and isn't Metacity still needed in some ways even if you're using Emerald for the windows borders?  I thought Metacity handled windows more generally...?

---

### Post by Regenweald on 2009-07-15
I believe metacity libs are needed, but i have removed the metacity window manager. You could also try Gconf>>Desktop>>Session>>required_components>>window manager>> set to emerald

---

### Post by wayne_cat on 2009-07-15
> **monkeyKata said:**
> 

Also, I no longer see any settings to change the login window (GDM) as we could in previous versions.  Is this under a new name with Grub2 and all, or is theming just not yet possible?  I saw another thread discussing a fix or update to Grub2... I have installed the alpha 2 from the 13th just two days ago.


gdm version 2.26 can not be themed at the moment and there is also no application to
change the settings. Some settings can be configured in the gdm config file:

[http://projects.gnome.org/gdm/docs/2.24/configuration.html](http://projects.gnome.org/gdm/docs/2.24/configuration.html)

and maybe there will be a solution for the missing config application:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299)

Maybe intersting:

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-gdmconfig](https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-gdmconfig)

---

### Post by chrisccoulson on 2009-07-16
> **wayne_cat said:**
> gdm version 2.26 can not be themed at the moment and there is also no application to
change the settings. Some settings can be configured in the gdm config file:

That's not entirely true. GDM **can** be themed right now. It's just that there are no graphical tools to do it.

---

### Post by plun on 2009-07-16
> **chrisccoulson said:**
> That's not entirely true. GDM **can** be themed right now. It's just that there are no graphical tools to do it.

Well...:D

[http://ubuntuforums.org/showpost.php?p=7603084&postcount=407](http://ubuntuforums.org/showpost.php?p=7603084&postcount=407)

One more thing is needed (later inte the thread)
export DISPLAY=:0.0

> (1) Start GDM ie Logout
(2) Swith to tty, Ctrl-Alt-F1 and login 
(3) Become root on the console, sudo -s
(4) Execute: export DISPLAY=:0.0
(5) Execute: sudo -u gdm gnome-control-center
(6) Switch back to the gdm screen (ALT-F7).
The control center should be visible.
(7) Configure you background, theme, fonts, ...

---

### Post by wayne_cat on 2009-07-16
> **chrisccoulson said:**
> That's not entirely true. GDM **can** be themed right now. It's just that there are no graphical tools to do it.

Look at these gdm themes:

[http://www.gnome-look.org/index.php?xcontentmode=150](http://www.gnome-look.org/index.php?xcontentmode=150)

or the themes for the old gdm version in:

```
/usr/share/gdm/themes
```The support for the gdmgreeter themes is missing since version 2.21:

[http://mail.gnome.org/archives/gdm-list/2009-April/msg00036.html](http://mail.gnome.org/archives/gdm-list/2009-April/msg00036.html)

changing the background picture and the gtk style is not a theme :(

---

### Post by chrisccoulson on 2009-07-16
> **wayne_cat said:**
> Look at these gdm themes:

changing the background picture and the gtk style is not a theme :(

How is that different to the themes you apply to your desktop? All they do is change the background, gtk and metacity styles and icons. This is exactly what you can do with the new GDM greeter now.

So, you're saying that all the themes on [www.gnome-look.org](www.gnome-look.org) are not really themes, because they only change the gtk style and backgrounds? Hmmm, ok....

---

### Post by wayne_cat on 2009-07-16
This is gdm with a gdmgreeter theme:


[http://www.gnome-look.org/content/preview.php?preview=1&id=88305&file1=88305-1.png&file2=88305-2.png&file3=88305-3.png&name=Arc-Colors+GDM-Walls](http://www.gnome-look.org/content/preview.php?preview=1&id=88305&file1=88305-1.png&file2=88305-2.png&file3=88305-3.png&name=Arc-Colors+GDM-Walls)

[http://www.gnome-look.org/content/preview.php?preview=1&id=93736&file1=93736-1.png&file2=&file3=&name=Industrial+II](http://www.gnome-look.org/content/preview.php?preview=1&id=93736&file1=93736-1.png&file2=&file3=&name=Industrial+II)


A theme was a little bit more than a background picture and the gtk style

---

### Post by mc4100 on 2009-07-16
> **chrisccoulson said:**
> How is that different to the themes you apply to your desktop? All they do is change the background, gtk and metacity styles and icons. This is exactly what you can do with the new GDM greeter now.

So, you're saying that all the themes on [www.gnome-look.org](www.gnome-look.org) are not really themes, because they only change the gtk style and backgrounds? Hmmm, ok....

Clearly they mean xml themes, which are completely different to gtk themes. Technically, theme-ability is still there, but it unquestionably has regressed: no transparency, etc,.

---

### Post by wayne_cat on 2009-07-16
> **monkeyKata said:**
>   Has Karmic been stable for you all?  Think it's best to stick with it?

It was quite stable for an alpha version but you can not count on it. I still have Jaunty on my first Linux partion ... even if I don't use it often. Use Jaunty for your daily work and Karmic as a playground ... to see what it will be like ... and to share your experience (questions / tips in the Karmic Testing Forum, Launchpad Bugs).

You can test the Karmic updates in a virtual machine before you apply them to the "real" Karmic installation but some things can only be tested in the real world (Xorg, perfomance ...)

---

