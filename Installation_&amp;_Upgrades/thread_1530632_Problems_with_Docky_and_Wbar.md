---
title: "Problems with Docky and Wbar"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-07-13
So I have a problem with Docky. Last time I had it installed it was pretty unobtrusive and just a small strip on the bottom that would disappear when I loaded a page unless I scrolled on the bottom.,...Now when it launches it turns the bottom 20% of my screen dark, and its pretty obtrusive. How can I get rid of that so that it shares a background instead of cutting my screen up?


My problem with Wbar is different. Its not chopping up space, however, I cant seem to find Wbar Config as is found in Google Gadgets, and without config its kind of a crappy app that I cant customize very easily.


So what do I do? Add the GOS repositories?

How do I get rid of the black box taking up room with docky?



Finally, does anyone know that program from the Enlightened Gnome or OpenGEU distro of linux that has those circle bar charts? That is an awesome app.....Gnome-do is also cool, but I like the look of the pie graph vs windows and lists, especially if I can customize them with themes like are available in E17.



Any help?

---

### Post by MooPi on 2010-07-19
I've found the config but can't make many of the changes I'd like to try. Can't change position as it always stays bottom center.Location of config template dot.wbar /usr/share/wbar. Move the file to your home folder and remove dot. Edit and change per man file instructions.

---

### Post by Nick_Jinn on 2010-07-19
Do you have your video card drivers installed?

---

### Post by spcwingo on 2010-07-19
Here's a copy of my .wbar that resides in my home folder:

```
# The Bar && Font
i: /usr/share/wbar/iconpack/wbar.osx/mybg8.png
t: /usr/share/wbar/font/12
c:

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/KONSOLE(SYSTEM).png
c: nautilus ~
t: Nautilus

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/KONSOLE2.png
c: gnome-terminal
t: Terminal

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/KONQUEROR.png
c: firefox
t: Firefox

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/EMAIL.png
c: thunderbird
t: Thunderbird

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/PIDGIN.png
c: pidgin
t: Pidgin

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/OPENOFFICE-WRITER2.png
c: openoffice.org3
t: OpenOffice

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/GIMP.png
c: gimp
t: Gimp

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/XMMS.png
c: totem
t: Totem

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/CONFIGURE.png
c: ubuntu-tweak
t: Tweak

i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/LOGOUT.png
c: gnome-session-save --kill
t: Logout
```

and a copy of my startup script:

```
#!/bin/sh

(sleep 15s && wbar -bpress -above-desk -pos bottom -isize 50.0 -idist 12.0 -nanim 3.0 -zoomf 1.8 -jumpf 1.0 -balfa 85.0 -falfa 100.0) &
```

Finally a screenie, of course :) :

---

### Post by Nick_Jinn on 2010-07-20
Would I just copy that into a folder to get everything working right?

---

### Post by spcwingo on 2010-07-20
You could (you'd just need to save it in your home folder and name it .wbar), but you would have to change the path of the icons, selected icons, etc...the reason behind that is I use custom icons and bar-back.  As far as the startup script...it should work as-is.  After saving it to file just mark it as executable.  If you want wbar to start when you logon just add the startup script to your startup apps.

---

### Post by Nick_Jinn on 2010-07-21
hmmm

Im not a complete noob, but I dont know how to change paths yet. Whenever the paths are not just perfect I pretty much give up on scripts. I would like to work on that though.

---

### Post by spcwingo on 2010-07-21
By path I just meant the path to the icons.  For example:

```
i: /usr/share/wbar/iconpack/wbar.osx/reflective_icons/KONSOLE2.png
c: gnome-terminal
t: Terminal

```

The first line is the full path to the icons.  The second line the command to execute.  The last line is what will be displayed under the icon when the pointer moves over it.  By the way, I'm using the package from the Google code website because I couldn't get the one from the repos to do what I wanted easily.  If you would rather have that one too just head over here to get it:

[http://code.google.com/p/wbar/downloads/detail?name=wbar_1.3.3_i386.deb&can=2&q=]("http://code.google.com/p/wbar/downloads/detail?name=wbar_1.3.3_i386.deb&can=2&q=")

After installing you should also lock that package under synaptic because updates might overwrite it with the one from the repos.  If you need anymore help just let me know and I'll try my best to get it going for ya.  :)

---

### Post by Nick_Jinn on 2010-07-22
I can change the paths through the GUI if I have Wbarconfiq. I know that it vanishes sometimes if you are missing an icon.

---

### Post by ashhab2010 on 2011-03-28
Docky requires a Compositing Window Manager to function properly. The black bar you see across the bottom is the area where Docky would be showing up if it could run. The usual compositing window manager for Ubuntu is Compiz, which can be enabled via System > Preferences > Appearance. From there you can try to enable "Normal" or "Extra" desktop effects in the "Visual Effects" tab.

If Compiz won't play nice with your graphics card, you can enable Metacity's compositing, which will at least allow Docky to run normally. To do this, press Alt+F2, then run gconf-editor. On the left side, browse to apps > metacity > general, then check the box next to "compositing_manager" on the right.
done!!!! :)

---

