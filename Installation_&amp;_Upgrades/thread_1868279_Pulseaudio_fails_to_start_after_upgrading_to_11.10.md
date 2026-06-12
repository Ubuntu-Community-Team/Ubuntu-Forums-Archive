---
title: "Pulseaudio fails to start after upgrading to 11.10"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by bdw on 2011-10-24
After upgrading to 11.10 from 11.04, Pulseaudio will not start automatically.  The only way that I can start it is this way:

```
$ pulseaudio -D
```

I don't get any sound.  I do have audio without it but I'm not having any luck finding out why it won't start.

I move .pulse to .pulse.old - no effect

I'm not finding any error messages and haven't found anything after searching the Internet for what might be causing this.

I'm using KDE but haven't verified with Unity or Gnome Classic yet.

Has anyone else experienced this?

---

### Post by raja.genupula on 2011-10-24
some times updates gonna solve issues like this . so have you done updating after installing ?

---

### Post by bdw on 2011-10-24
I did do an update immediately after upgrading but that didn't resolve the problem, neither did uninstalling/reinstalling the pulseaudio packages. :(

---

### Post by raja.genupula on 2011-10-24
> **bdw said:**
> I did do an update immediately after upgrading but that didn't resolve the problem, neither did uninstalling/reinstalling the pulseaudio packages. :(

Hi man 

I am not sure about this but give a try for it .


```
sudo apt-get install dconf
```

and in the apps menu at indicator check for that global-mute and make sure its not checked . 

& 

look at here 

[https://help.ubuntu.com/11.10/ubuntu-help/sound-nosound.html](https://help.ubuntu.com/11.10/ubuntu-help/sound-nosound.html)


all the best

---

### Post by bdw on 2011-10-24
dconf had already been installed and global mute was turned off.

Audio is working OK without pulseaudio, so I don't think I'll continue to troubleshoot it at this point.

---

