---
title: "No more gnome after upgrading to Karmic"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ploum on 2009-08-17
Hello,

I upgraded my test laptop to Karmic and, as a consequence, gnome-session doesn't seem to start anymore

I have the new GDM, I log then nothing happens. I see the GDM wallpaper and my pointer, that's it.


I tried to look in every logs (including xsession-errors) but there was nothing interesting. I started a simple xterm session to launch everything by hand :

- gnome-panel, nautilus load perfectly
- gnome-settings-daemon was not loading. The /etc/hosts was changed by the upgrade (127.0.1.1 bug) and correcting it allowed g-s-d to launch properly
- metacity launches but doesn't show any button.

I tried to launch gnome-session in debug mode but I don't see anything that looks like my blocking point. According to ps -e, it just looks like everything is launched correctly but stop somewhere after evolution-data-server and before gnome-panel/metacity/nautilus.

To be sure that it was not a user session bug, I created a new user but it's exactly the same.


I decided to do a clean install and downloaded Karmic Alpha 4. No luck, if I boot the CD, when X start, the screen becomes completely white and everything is frozen (no console). I can still see the Ubuntu usplash logo fading out in the white. My graphic card is Intel 915GM/GMS/910GML.

So I'm stuck.

Can anybody helps me to either start GNOME or have graphics with the CD?

Thanks in advance.

---

### Post by ploum on 2009-08-17
I solved my problem by reinstalling every package with the word gnome in it. Looks like there was some kind of corruption.

---

### Post by Rhubarb on 2009-08-17
Hooray for borkage when testing out alpha releases :D

I'm glad you worked out how to fix it though :)
- Have fun with Karmic!

---

### Post by ploum on 2009-08-20
yep, I reported a bunch of bugs in the process ;-)

---

