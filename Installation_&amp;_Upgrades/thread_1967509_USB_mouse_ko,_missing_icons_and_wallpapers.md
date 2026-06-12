---
title: "USB mouse ko, missing icons and wallpapers"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by raffaele181188 on 2012-04-28
I was running 11.10 and I was happy. Since a couple of days I kept getting suggested to upgrade, but I didn't care: I was fine. Today a nice window popped up announcing that the shiny new 12.04 was ready and I finally decided to trust it: it was a nice window - and I also thought that after a pair of dozens of versions Ubuntu could upgrade without breaking. So I clicked "Ok" and it downloaded the dist-upgrade tool and started getting the packages and installing them. Finally the pleasant window told that it was better to restart the system. But then...

[SIZE="4"]**The USB mouse doesn't work! There is no wallpaper, no icons, not even one!**[/SIZE] All I can do is Alt+F2, searching "xterm" and start it, but the window can't get the focus, my mouse doesn't work, so I don't even have a shell (no, the "terminal" app doesn't even start, don't know why...)

And now? How am I supposed to recover such a distaster? Should I install everything from the CD? Why, Ubuntu, why? I don't have that exotic hardware: it's a plain desktop machine with just about an Intel mobo, a Core2, and an integrated Intel card.

---

### Post by raffaele181188 on 2012-04-28
I cannot even start a console session. Ctrl+Alt+Fn only shows a blank screen

---

### Post by jadtech on 2012-04-28
yup I| had this problem  a while back when I upgraded to beta it has been a know issue for some ..

if you can manage to get to a terminal you could complete the upgrade some parts get install out of order causing this problem ..

if you can manage 

```
 sudo apt-get dist upgrade -f 
```

should help  you might need a bit more help debugging bits after that but it would go a long way to getting you back to normal ..  

personally when it happened to me at the time I didnt have a lot to lose so I just went for  the re-install many have recovered from this and someone here may know a way to get you through to  the terminal ..

---

### Post by raffaele181188 on 2012-04-28
I reinstalled 11.10 from the dvd, I couldn't get to any shell. I wonder what's the use of a new version every six months if you can't guarantee a successful update

---

