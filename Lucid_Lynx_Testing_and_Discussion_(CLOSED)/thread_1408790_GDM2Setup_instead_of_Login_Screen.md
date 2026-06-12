---
title: "GDM2Setup instead of Login Screen"
date: 2010-02-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-02-16
What do you guys think of GDM2Setup and may be it can replace Login Screen?

[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

Thanks.

---

### Post by ranch hand on 2010-02-16
Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

EDIT

It appears to help if you try this on a 9.10 install instead of 10.04.

---

### Post by donniezazen on 2010-02-16
> **ranch hand said:**
> Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

Try karmic instead of Lucid as distribution in software sources.

---

### Post by ranch hand on 2010-02-16
yeh I just put it over on a 9.10 install here on the test platform.  I need to switch to my night time production OS anyway so will get out of here and stop in on 9.10 on the way out and check it out.

---

### Post by donniezazen on 2010-02-16
> **ranch hand said:**
> yeh I just put it over on a 9.10 install here on the test platform.  I need to switch to my night time production OS anyway so will get out of here and stop in on 9.10 on the way out and check it out.

I am using it on Lucid and its working great.

---

### Post by ranch hand on 2010-02-16
> **soham_1207 said:**
> I am using it on Lucid and its working great.
What exactly are you using it for?

On 9.10 there seems like little use for it yet, at least in my case.  I have wallpaper set for xsplash and gdm.  What I really need is a way to change the theme of the login screen and that is not included yet (tab greyed out - click on it and the message is "This will contain the saved themes dialog").

I did change the Decoration to Human-Clearlooks which did get rid of the "chocolate induced runs" brown.  It also changed my cursor though so that was not a real good thing.

When finished, this looks like a winner.  Nice clean gui, comes up quick, some real nice work.

---

### Post by donniezazen on 2010-02-16
> **ranch hand said:**
> What exactly are you using it for?

On 9.10 there seems like little use for it yet, at least in my case.  I have wallpaper set for xsplash and gdm.  What I really need is a way to change the theme of the login screen and that is not included yet (tab greyed out - click on it and the message is "This will contain the saved themes dialog").

I did change the Decoration to Human-Clearlooks which did get rid of the "chocolate induced runs" brown.  It also changed my cursor though so that was not a real good thing.

When finished, this looks like a winner.  Nice clean gui, comes up quick, some real nice work.

Yes the two tabs are disabled i have used it for decorating GDM. And also starting Karmic it failed to mute the login sound, i used to completely remove the sound file, but now i used this small app to mute the sound. Probably the login sound is a bug.

---

### Post by ranch hand on 2010-02-16
I wonder how long it will take them to finish the bugger.  I am having the plymouth problem in booting 4 out of 5 straight 10.04 installs. (not counting the minimal install running gnome DE or the Lubuntu 10.04A2 install).  I think I will wait to play with this on there until it is more mature.

Is there anything in decorations that does anything but turn the brown to white.  You can do that in, I think - it has been a while since I tried it, gconf editor.

It is an improvement but I don't bother with it as I do not see  it for very long.  The only place I really have to see that crappy (literally)color is the border here on the forums pages and the login box.

---

### Post by growlf on 2010-03-02
> **soham_1207 said:**
> Try karmic instead of Lucid as distribution in software sources.

Ahh  I had better add a Lucid release hadn't I.  I will do that shortly and post back.  Keep your eye out for it on the LP Project page as well.

---

### Post by growlf on 2010-03-16
Ok - a lucid version has been available since 0.5.0 and we are on 0.5.2 - which has some fixes specifically for Lucid in it.  Luckily the changes are backwards compatible for Karmic and so are part of the trunk now as well.  Please try it again now and let us know what you think of it, and if there are any things you would want changed/added.  Other team members are working on the theme portion (and import from old gdmtheme files) currently, and we expect that to be the next added feature.

---

### Post by cowlip1 on 2010-03-21
Thank you sooo much!  I had wondered what had happened to the old "Login Screen" preference tool.  Now, to change that background...!

---

