---
title: "Certain programs not loading up."
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by ProgressiveAudio on 2010-12-22
Hello there.  Just recently, I've run into a problem with VLC.  Whenever I clicked on it, it never loaded up.  Sometimes a tab of it would appear for a split second, but it would immediately vanish.  I assumed it was something wrong with the program itself so I went to the Synaptic Package Manager to uninstall and re-install it, unfortunately, it seems to have the same problem!  So I figured maybe I should just update Ubuntu and then discovered my update manager won't update anything, it's broken too.  I have no idea what is going on and I hope these pictures help you to understand what the problem is, so you can help me (I'll provide anything else necessary):

[IMG]http://img530.imageshack.us/img530/1889/screenshot2tq.png[/IMG]

[IMG]http://img89.imageshack.us/img89/3696/screenshot3s.png[/IMG]

---

### Post by sikander3786 on 2010-12-22
From Applications > Accessories > Terminal, please post the output of these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated code tags to make them easy to read ;-)

---

### Post by ProgressiveAudio on 2010-12-23
Hey the update manager and VLC is working now, if I have any further problems I'll update you on it.  Thanks!

---

