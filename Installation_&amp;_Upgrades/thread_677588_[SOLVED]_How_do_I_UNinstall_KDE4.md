---
title: "[SOLVED] How do I UNinstall KDE4?"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by lizadove on 2008-01-25
Help - I've installed KDE4 and everything looked fairly good until I rebooted.  Now...  All I get is a login screen that says "Welcome to Debian at abc-desktop"  I login and then there's a tiny terminal in the upper left hand corner of the screen with nothing else.  What's going on??  I'd like to just uninstall KDE4 and get 3.5.8.  Can anyone help me do this??

Thank you so much!

Here's a screenshot:

---

### Post by johnsonite on 2008-01-29
I'm having the same problems, any pointers to solutions would be appreciated. The post is marked as solved without replies, but I couldn't find any thing relevant on the forums with a quick search...

---

### Post by lizadove on 2008-01-30
Here's another spot with this question (i'm actually ebleitztah on there)

[http://kubuntuforums.net/forums/index.php?topic=3090772.0](http://kubuntuforums.net/forums/index.php?topic=3090772.0)

I hope it helps.  I wish I had written down the exact code I used.

---

### Post by johnsonite on 2008-01-30
OK, the solution I got working is;

command found through the link

```
sudo apt-get purge kdelibs5
```

After this, restarting X (ctrl-alt-backspace) got me to a basic terminal login(no x session). I could however use startx and got to my Gnome desktop.

Reinstalling GDM and rebooting got me back to the GDM greeting screen from where I could choose any session without problems, like it used to be before installing KDE4. Dunno what else sort of havok the brief sejour with KDE4 did for my packages, but everything else seems to be working so far.

---

### Post by mikerobinson on 2008-02-18
> **johnsonite said:**
> OK, the solution I got working is;

command found through the link

```
sudo apt-get purge kdelibs5
```

After this, restarting X (ctrl-alt-backspace) got me to a basic terminal login(no x session). I could however use startx and got to my Gnome desktop.

Reinstalling GDM and rebooting got me back to the GDM greeting screen from where I could choose any session without problems, like it used to be before installing KDE4. Dunno what else sort of havok the brief sejour with KDE4 did for my packages, but everything else seems to be working so far.

I just did this and it worked great, however since I'm running kubuntu, after this I did ```
apt-get install kubuntu-desktop
```and everything worked fine. Also, when purging, if it asks you to stop kdm say no. This is probably similar for gdm if you're running it.

---

### Post by malom on 2008-06-21
thanks johnsonite and mikerobinson. seems to have worked,

---

