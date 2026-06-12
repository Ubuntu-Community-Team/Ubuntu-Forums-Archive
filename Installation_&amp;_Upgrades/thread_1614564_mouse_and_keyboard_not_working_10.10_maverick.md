---
title: "mouse and keyboard not working 10.10 maverick"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by azmr111 on 2010-11-05
Hey guys I upgraded to 10.10 from 10.04 few weeks ago.  Everything was working fine until today when I did a partial upgrade and it removed some of the lib files. Now my [COLOR="Black"]usb mouse and keyboard is not working[/COLOR].  I can move the mouse around but can't click ( left or right ).  i have nvidia graphics card.  

I tried running it under safe graphics mode and when i do that everything works fine except for the compiz obviously .. i have tried reinstalling nvidia driver to see if that would make a difference but that didn't work either.  

Im not sure which lib files did ubuntu removed. I have searched everywhere to find a solution on the web and the only thing I think it might b iz my xconf file iz messed up.

If anyone can help me on this I would really appreciate it. I really don't want to reinstall the whole OS and loose all my apps :(

Thanks

---

### Post by yeats on 2010-11-05
> I really don't want to reinstall the whole OS and loose all my apps.

Sometimes, unfortunately, this is the easiest solution.  However, unless you've done a lot of customized software installations outside the normal Ubuntu repositories, recovering your installed apps doesn't have to be difficult.  I usually create a list of my installed apps by doing

```
dpkg -l > ~/installed.txt
```

which will create a file in your home directory called "installed.txt" that has a list of all the software packages you have installed and/or removed for easy reference when reinstalling.

---

