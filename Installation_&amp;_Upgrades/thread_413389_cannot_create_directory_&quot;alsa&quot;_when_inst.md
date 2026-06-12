---
title: "cannot create directory &quot;alsa&quot; when installing soundcard"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by henry8596 on 2007-04-19
hi, i am a new linux user. I am trying to install my zoltrix sound card. i found it is supported under linux and there is a instruction of how to install. [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Zoltrix&card=Nightingale.&chip=CMI8738&module=cmipci#Inst](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Zoltrix&card=Nightingale.&chip=CMI8738&module=cmipci#Inst)

However, when i type in the second command (mkdir alsa), the terminal shows:
mkdir: cannot create directory `alsa': Permission denied

I don't know the reason. but there is a situation of my computer, that i have 2 soundcards in my computer because one of them (X-Fi) is not supported under linux. and because of my desire of using linux, i try to install them both.

I hope someone can help me, who is a new linux user, out. Thank you very much.

---

### Post by tomasz2006 on 2007-04-19
try to prefix your command with
```
sudo
```
(you will be asked for your root password) and see if this gets you any further...

---

