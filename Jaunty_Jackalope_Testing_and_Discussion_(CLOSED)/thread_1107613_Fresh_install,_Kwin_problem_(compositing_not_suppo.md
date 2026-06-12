---
title: "Fresh install, Kwin problem (compositing not supported?)"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by halfsane on 2009-03-26
When trying to enable KDE effects on a fresh install (nvidia driver installed) I am getting this message.

```
Compositing is not supported on your system.
Required X extensions (XComposite and XDamage) are not available
```


I tried to edit xorg.conf, and synaptic shows xcomposite and xdamage are indeed installed (the best I can tell)



I installed fresh for a clean slate, I did not have this issue before hand.

Any help is appreciated, thanks!

---

### Post by halfsane on 2009-03-27
Anyone have anything on this? 

 Ive searched around and cant find anything more than adding a few lines to the xorg.conf file.  Seems to have cleared this kind of thing up about a year ago. 

Maybe its my nvidia drivers ?

---

### Post by halfsane on 2009-03-27
Im using 180.37 btw

---

### Post by daveee on 2009-04-23
The "few lines" you mention fixed me right up...

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

I've seen others suggest testing whether glxgears (and thus openGL) is working on your machine...

I'm not too bright, but am looking for places to comment on what worked for me after fiddling/googling this for a couple of hours before getting it to work.

Daveee

---

### Post by krazyd on 2009-04-23
What card have you got? For my 6200 I had to do ```
nvidia-xconfig
``` on a blank xorg.conf.

---

### Post by caryb on 2009-04-23
I have a similar post to this going but I had the same problem with 185.19 driver, I uninstalled it & reinstalled the 180.27 driver but now it fails to load! Gees I hate the whole prop driver issue in *buntu.


Cary

---

