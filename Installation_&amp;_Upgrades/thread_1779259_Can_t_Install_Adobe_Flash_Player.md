---
title: "Can t Install Adobe Flash Player"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by Dome1223 on 2011-06-10
I am trying to install Adobe Flash Player,Swfdec SWF player, and Gnash SWF Player
i click DALJE (FOWARD, I AM CROATIAN) : and it says: 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



PLEASE HELP

---

### Post by nomko on 2011-06-10
> **Dome1223 said:**
> I am trying to install Adobe Flash Player,Swfdec SWF player, and Gnash SWF Player
i click DALJE (FOWARD, I AM CROATIAN) : and it says: 
 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 
 
 
PLEASE HELP
 
Did you try: ```
sudo dpkg --configure -a
```??
Try that and start installing the flash player again.
Hint:
Do not use the Adobe flash player but **flashplugin-nonfree**.

---

### Post by Dome1223 on 2011-06-10
where do i put that code?? in windows it s in run ?????

---

### Post by Dome1223 on 2011-06-10
i found it thank you weary much :D

---

### Post by nomko on 2011-06-10
> **Dome1223 said:**
> i found it thank you weary much :D

Nice to know what you did to solve your issue...

---

### Post by Dome1223 on 2011-06-10
I got a new problem :/

it worked i watched clips on YouToube i turn the laptop off and the clip is not working ?!?!?! 

i probably installed something wrong...it might be Swfdec,Adobe Flash Player...please HELP

---

### Post by sikander3786 on 2011-06-10
Welcome to the forums :)

The easiest method of installing Flash in Firefox, Ubuntu is to use the FF add-on, flashaid and specially for new users. So, here is what you need to follow.

Go to Applications > Accessories > Terminal or if using Unity, press the <Super> (Windows Logo Button) and search for Terminal and once more, execute these commands just to make sure there aren't any broken/un-configured packages. If there are any errors, please post them.

```
sudo dpkg --configure -a
sudo apt-get install -f
```

Now, install the flashaid add-on from here. Remember, flashaid not only installs Flash but it also removes the conflicting add-ons (if any). And moreover, it is capable of installing the newest version from Adobe Labs which solves issues for many.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

The flashaid icon would appear just besides the Home icon in Firefox. Click it, choose, Wizard Mode and just leave the default options and keep clicking next. Once finished, restart Firefox and see it things improved.

---

