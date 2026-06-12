---
title: "Roll Back?"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by jdb91 on 2010-05-06
I've just upgraded to 10.04 LTS and just wondering if there is a way of rolling back? It's terrible on my EEE 1080, my sound no longer works, I can't edit the bar at the top, I can't get rid of the Applications menu and I cannot re arrange the icons on the bar.  I really want to roll back so is there a way or am I going to have to fresh install?

---

### Post by hansdown on 2010-05-06
Hi jdb91.

The only way back is a fresh install. Sorry.

---

### Post by mikewhatever on 2010-05-06
> **jdb91 said:**
> I've just upgraded to 10.04 LTS and just wondering if there is a way of rolling back? It's terrible on my EEE 1080, my sound no longer works, I can't edit the bar at the top, I can't get rid of the Applications menu and I cannot re arrange the icons on the bar.  I really want to roll back so is there a way or am I going to have to fresh install?

There is no 'roll back' whatever that means, but lets try fixing the top panel issue. Open Applications->Accessories->Terminal, copy/paste the following command and hit 'Enter'.
```
rm -r .gconf/apps/panel
```

Now, logout, and then login.

---

### Post by dgw on 2010-05-06
> **jdb91 said:**
> my sound no longer works
Type "alsamixer" in a terminal (without the quotes) and adjust your settings there, probably your speaker volume.

---

### Post by jdb91 on 2010-05-13
> **dgw said:**
> Type "alsamixer" in a terminal (without the quotes) and adjust your settings there, probably your speaker volume.

I sorted that out, in sound settings, it was set to only outputting through the jack rather than speakers.

The second thing I want to sort out it to get the top bar with Applications, Places, System and the bottom bar with running applications like I had on 9.10. I'm sure you used to be able to right click on the bar to edit it, but I can't do that any more. I hate this new sinlge button that fills the desktop with a menu.

---

### Post by jdb91 on 2010-05-13
> **mikewhatever said:**
> There is no 'roll back' whatever that means, but lets try fixing the top panel issue. Open Applications->Accessories->Terminal, copy/paste the following command and hit 'Enter'.
```
rm -r .gconf/apps/panel
```

Now, logout, and then login.

Removing that hasn't changed the bar, this is what I get upon boot:

[IMG]http://img714.imageshack.us/img714/2225/screenshotdoz.png[/IMG]

And this is what I used to have before upgrade (the bars where set to autohide, but you can just make them out)

[IMG]http://img443.imageshack.us/img443/8784/editm.png[/IMG]

---

