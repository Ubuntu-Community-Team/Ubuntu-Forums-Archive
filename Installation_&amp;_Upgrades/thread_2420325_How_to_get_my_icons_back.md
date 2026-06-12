---
title: "How to get my icons back"
date: 2019-06-03
forum: Installation &amp; Upgrades
---

### Post by Fertech on 2019-06-03
I install compiz on my computer and I don't know if that made my icons go away. The only thing I can do is right click that about it. Can someone help me with this problem?

---

### Post by deadflowr on 2019-06-03
Well, we'll probably need to know what version of Ubuntu you are running for starters...

(And which desktop environment if not Ubuntu's default)

---

### Post by #&amp;thj^% on 2019-06-03
Could use a bit information from you:
```
lsb_release -a && echo $DESKTOP_SESSION
```
Ha, ninja'd by deadflowr :)

---

### Post by Fertech on 2019-06-03
14.04 lts

---

### Post by #&amp;thj^% on 2019-06-03
Still missing the environment:
```
echo $DESKTOP_SESSION
```
If using Unity then:
```
gsettings set org.gnome.settings-daemon.plugins.background active true 
gsettings set org.gnome.desktop.background show-desktop-icons true 

```

---

### Post by Fertech on 2019-06-03
When I login as a guess and open my compizconfig settings manager every time I uncheck the commands under general all my icons go away, and I check it back and I don't get my icons back, how can I delete the program?

---

### Post by #&amp;thj^% on 2019-06-03
I have now asked three times for the output for:
```
echo $DESKTOP_SESSION
```
I won't ask or reply again.......
BTW, I nearly forgot to tell you, Ubuntu 14.04 reached its end of life on April 30, 2019. This means there will be no security and maintenance updates for Ubuntu 14.04 users anymore unless they pay for the extended security.

---

### Post by Fertech on 2019-06-03
It echos ubuntu

---

### Post by deadflowr on 2019-06-03
Not sure what ccsm plays in it but what does
```
gsettings get org.gnome.desktop.background show-desktop-icons
```
in a terminal show?


Edit: also btw 14.04 has hit it's regular user end of life.
Support has moved to paid support only.

---

### Post by again? on 2019-06-03
You didn't install compiz....compiz is the default window manager in 14.04 unity.
You installed compizconfig-settings-manager (ccsm)
If what you did in ccsm caused the issue you can reset to default and restart compiz.
In terminal....
```
dconf reset -f /org/compiz/
setsid unity
```

---

