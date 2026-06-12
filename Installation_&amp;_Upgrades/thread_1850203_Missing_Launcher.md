---
title: "Missing Launcher"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by simontroll on 2011-09-26
I finally upgraded from 10.10 to 11.04.

My files are fine and most of my apps work and are still configured properly, but I have no launcher or dashboard, no access to the main menus or clock or any of that very useful stuff for troubleshooting . I'm pretty much of a newbie on linux so I'm not sure where to start with troubleshooting this.

There's something wrong with the windows finder equivalent. Is that called Unity? I found several threads that lead me to restart unity in the terminal window, but that fails. I also can't do simple things like alt tab between applications. 

What are my best options? Can I reinstall 11.04 without it doing a clean install? Is there a way to roll back to 10.10. I've been looking through this help forum for hours and can't find these basic installation questions discussed.

Thanks

---

### Post by simontroll on 2011-09-26
.

---

### Post by simontroll on 2011-09-26
.

---

### Post by raja.genupula on 2011-09-26
Please Dont bump so early .

while coming to your issue. 
have you tried these things

```
unity --reset
```
```
unity --replace
```

or

enable **unity** checkbox in **ccsm **

to get ccsm menu , type **ccsm** in terminal
check all those things.


All the best.

---

### Post by Frogs Hair on 2011-09-26
When you get your panels working run the following and logout and in . There is a trouble shooting guide at the link. ```
sudo apt-get install indicator-datetime 
``````
sudo apt-get install indicator-weather
```[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by simontroll on 2011-09-26
Thank you so much for the suggestions. I didn't get to try them, because CTRL+ALT+t no longer seemed to work to bring up the terminal window. Being the newb that I am I couldn't find another way to launch it.

However, I found a workaround if anyone else gets stuck.

I found then launched the Ubuntu Software Installer and discovered and installed the Unity 2D option there which worked like a charm. I don't remember what GPU I have in there, but this is a pretty new machine.

---

### Post by Frogs Hair on 2011-09-26
Find GPU ```
lspci
```

---

