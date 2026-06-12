---
title: "[SOLVED] VLC acts as file manager"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by slymi2005 on 2008-10-02
I'm not sure what I did but when I click on places and click anything from Home to Videos, VLC opens up and display the contents, if it is music, pictures, or videos it will display them but otherwise I will get an error message saying it cant open it. I got around this by clicking computer and then navigating to my home folder. Why did vlc change this?

---

### Post by rbmorse on 2008-10-02
Open a terminal

nautilus

When the window loads, right click any where within the window and then click on properties, then click on the "open with" tab.  Select "file manager" and then close the window.

---

### Post by mc4man on 2008-10-02
> I'm not sure what I did

What you did was go right click -> 'open with' -> 'open with other application' on a folder (maybe a video_ts or a folder with music files in.
That *adds* vlc as a *choice* of apps for 'inode/directory', which is a *good thing* to do. It also *makes* it the default choice.(not so good, only happens in 8.10

Simply doing as posted above sets nautilus back to the default (what you want.

Now though when you right click on a folder -> 'open with' you'll see vlc listed right there. Choosing vlc (or any other choice) from there won't change the default, it will just open that folder with vlc (or whatever you've chosen.

This is a way to add other choices to the 'open with' (add all your media players and anything alse you may use on folders, then switch back to nautilus

This is a 'difference" ( or flaw in 8.10) between 8.04 and 8.10.
  In 8.04 using the the 'open with other application' would add a app to that line but *would not change the default from nautilus*  

In 8.04 you'd need to go to the properties of any folder to move the default off of nautilus for all folders.

8.10 line after picking vlc from right click -> 'open with' -> 'open with other application'

inode/directory=vlc.desktop
After changing back
inode/directory=nautilus.desktop;vlc.desktop;
After adding Amarok
inode/directory=amarok-kde.desktop;nautilus.desktop;vlc.desktop; (now amarok is default which is 'wrong'
changing back
inode/directory=nautilus.desktop;amarok-kde.desktop;vlc.desktop;


My line in 8.04 (never switched default off  of nautilus when adding apps to the 'open with' (notice nautilus is last

inode/directory=vlc.desktop;userapp-xine-63PWHU.desktop;userapp-amarok-UZ82HU.desktop;totem.desktop;mplayer.desktop;userapp-vlc-GXCHHU.desktop;userapp-vlc-U5IBGU.desktop;userapp-audacious-Q8ZJHU.desktop;audacious.desktop;userapp-vlc-2YTEHU.desktop;amarok-kde.desktop;nautilus-folder-handler.desktop;

---

### Post by darco on 2008-10-04
Wow, this just happened to me...I had VLC already installed when I upgraded to Beta and i KNOW it was nothing I did....
thxs

darco

---

### Post by taavikko on 2008-10-04
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

---

### Post by gypsy_roadhog on 2008-10-13
Thanks I had this problem but with mplayer. I didn't realise that selecting an "open with application" would change the default value. Particularly difficult if you select an application by accident and don't realise what you have done.

Thanks for your help.

---

