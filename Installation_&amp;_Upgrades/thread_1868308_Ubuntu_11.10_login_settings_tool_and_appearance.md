---
title: "Ubuntu 11.10 login settings tool and appearance"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2011-10-24
Hi,

I have updated at last version of Ubuntu 11.10 and now I'm amazed about the fact that I can't come back to the old dekstop appearance. I have partially resolved with the following two installations

```
 sudo apt-get install gnome-session-fallback 
```

```
 sudo apt-get install gnome-tweak-toolk 
```

Unfortunately the system menu is not present and some applications are randomly distributed among the others menu >:( 

Now I can't find the tool to set the login property which probably should be called "login screen settings".
In addition, I can set the appearance of the windows to have the three buttons (close, reduce to icon and resize) on the right side of the windows?

Thank you

---

### Post by raja.genupula on 2011-10-24
The first thing you have done will makes your desktop as a classic one but not pure .

i suggest you that get gnome-shell

```
sudo apt-get install gnome-shell
```

its good and i that menu you do have gnome-classic too.

all the best.

---

### Post by erotavlas on 2011-10-24
Thank for your fast reply. When I install gnome-session-fallback it installs also the gnome-shell. However I have installed only the gnome-shell as you have suggested.

Now I would like to know if there is a way to recover the old system menu and a way to modify the position of the three buttons (close, reduce to icon and resize) from the left side to the right side of the window.

Thank you

---

### Post by raja.genupula on 2011-10-24
[http://blog.sudobits.com/2011/05/01/top-10-tips-and-tricks-for-ubuntu-11-04/](http://blog.sudobits.com/2011/05/01/top-10-tips-and-tricks-for-ubuntu-11-04/)


i think common for both 11.10 and 11.04 .

all the best.

---

### Post by vulcanoman on 2011-10-24
Hi

try with simple lightdm manager

---

### Post by Mark Phelps on 2011-10-24
Sorry I don't have the link ... but if you go to the Ubuntu Geek website, there was a link a while back for a plugin you installed that put an icon in the top bar of the screen -- that you could click and get the old menu system back. It was called ClassicMenuIndicator.  I installed this in 11.04 and it worked great. Haven't got around to installing 11.10 yet -- happy having a system that still works.

---

### Post by erotavlas on 2011-11-06
> **raja.genupula said:**
> [http://blog.sudobits.com/2011/05/01/top-10-tips-and-tricks-for-ubuntu-11-04/](http://blog.sudobits.com/2011/05/01/top-10-tips-and-tricks-for-ubuntu-11-04/)


i think common for both 11.10 and 11.04 .

all the best.


Hi,
I have tried to modify the position of the buttons with "Move the Windows buttons to Right Corner" but without success. The terminal gives me this warning
```

(gconf-editor:2143): GLib-GObject-WARNING **: g_object_get_valist: property `type' of object class `GConfEditorWindow' is not readable
 
```
Why? Thank you

---

### Post by erotavlas on 2011-11-06
> **Mark Phelps said:**
> Sorry I don't have the link ... but if you go to the Ubuntu Geek website, there was a link a while back for a plugin you installed that put an icon in the top bar of the screen -- that you could click and get the old menu system back. It was called ClassicMenuIndicator.  I installed this in 11.04 and it worked great. Haven't got around to installing 11.10 yet -- happy having a system that still works.
Thank you! It works

---

