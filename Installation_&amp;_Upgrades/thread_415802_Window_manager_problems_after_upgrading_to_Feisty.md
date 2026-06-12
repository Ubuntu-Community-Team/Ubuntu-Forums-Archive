---
title: "Window manager problems after upgrading to Feisty"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by misterdham on 2007-04-20
I upgraded to Feisty yesterday, and I am having trouble with my window manager. I had lost things like title bars and window chrome, and when I went to Preferences > Windows it said that I had no window manager installed. I knew I had Metacity, and found in another post somewhere that I could restart it by entering 'metacity' in the terminal. This did restart Metacity, but when I logged out and logged back in, my X server crashed. I can open a GNOME failsafe session but not a normal session. How do I get it to start metacity automatically?

BTW, I was also working on the box through VNC yesterday, might this have caused some of it?

I looked through the various stickies for a solution and did not find one. I apologize in advance if I missed anything obvious. Thanks for any help you can offer,

OK
DAH

---

### Post by ganceanach on 2007-04-20
Hey... 

Had this problem yesterday although not because of the upgrade... was trying out some new eye candy and it killed the default settings so no windows manager.

If found that I could load metacity and it all worked fine (like you) so I went to System-> Preferences->Sessions, clicked on the Start-up tab and added the line /usr/bin/metacity

Worked like a charm after that

Hope it helps

---

### Post by misterdham on 2007-04-20
That did it, thank you!

Now if only it would connect to my WPA Airport...

Thanks again!

OK
DAH

---

### Post by jammodotnet on 2007-04-27
> **ganceanach said:**
> If found that I could load metacity and it all worked fine (like you) so I went to System-> Preferences->Sessions, clicked on the Start-up tab and added the line /usr/bin/metacity

Worked like a charm after that

Thank you.
This solved my problem.
[http://ubuntuforums.org/showthread.php?p=2543482#post2543482](http://ubuntuforums.org/showthread.php?p=2543482#post2543482)

---

### Post by BarakNaveh on 2007-04-29
i had a similar problem but i was reluctant to just add an invocation to metacity on startup -- it was clear that something is broken.

Indeed, the culprit was found in the ~/.gnomerc file which contained a default value to the WINDOW_MANAGER environment variable. This was probably due to my previous playing around with early versions of Compiz.

the fix: 
 - edit ~/.gnomerc and remove the override of the WINDOW_MANAGER variable.
 - save
 - if the ~/.gnomerc file doesn't have anything else, you can simply delete it.

logout, re-login, and your done.

hth,
barak

---

### Post by BarneyRubble on 2007-05-01
Big thanks to Barak for this fix. The same problem was also preventing Beryl loading on startup.

---

