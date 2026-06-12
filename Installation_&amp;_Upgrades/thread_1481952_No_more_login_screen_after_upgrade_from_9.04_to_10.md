---
title: "No more login screen after upgrade from 9.04 to 10.04"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by adakite on 2010-05-13
Hi All,

I upgrade my system from 9.04 to 10.04, then when booting, I get the purple wallpaper and mouse, but nothing else, No login menu. I can hopefully connect to my system with ssh from another machine, I update everything, upgrade, etc etc, try to boot on recovery mode, and clean packages and so one...Nothing happens, still no login menu. 

How can I fix this problem?

Thank you

---

### Post by byStanderone on 2010-05-13
...do you have the login screen menu under: system>administration>login screen ?

---

### Post by howefield on 2010-05-13
Can you Ctrl + Alt + F1 to get a login prompt ?

---

### Post by adakite on 2010-05-13
>  		...do you have the login screen menu under: system>administration>login screen ?

Nope, I have only the wallpaper (puple with stars) and my mouse cursor but nothing else. No button, no menu bar, no login menu, nothing !

>  		Can you Ctrl + Alt + F1 to get a login prompt ?

Yes and what ?  I said that I can ssh on my computer, I thus updated every things, try recovery boot, but I got the same:  no login menu. Something got wrong during the update from 9.04  top 10.04, and aptitude and apt-get do not seem able to fix that. Does someone know which module/program/plugins/stuff controls the login menu in gdm ?

---

### Post by howefield on 2010-05-13
> **adakite said:**
> Yes and what ?  I said that I can ssh on my computer,

I thought you said "I can **hopefully** connect to my system with ssh from another machine". Quite a different thing.

Try removing quiet splash from the boot line. Might give you a clue as to what/where the problem is.

---

### Post by kansasnoob on 2010-05-13
> **adakite said:**
> Hi All,

I upgrade my system from 9.04 to 10.04, then when booting, I get the purple wallpaper and mouse, but nothing else, No login menu. I can hopefully connect to my system with ssh from another machine, I update everything, upgrade, etc etc, try to boot on recovery mode, and clean packages and so one...Nothing happens, still no login menu. 

How can I fix this problem?

Thank you

What method did you use to upgrade?

I wonder because you say you upgraded from 9.04 to 10.04 but you can't "officially" upgrade from 9.04 directly to 10.04. You'd have to go 9.04 > 9.10 > 10.04 :)

---

### Post by theviking10 on 2010-05-13
I have the same problem: on a fresh install I can not login - just desktop background and cursor.

I can login with Ctrl+Alt+F1, but I'm not sure what to do from there.

Please assist.

---

### Post by asheenlevrai on 2010-07-09
nothing yet?

I got a similar problem on 10.4.
everything use to be fine, but suddenly I got no more login screen, but a login prompt instead.
I can still login and then startx manually, but when I try to access the login screen properties everything is grey (non-editable) and clicking "unlock" doesn't do anything... 

As I said, eveything was going well a few days ago...

did any of you find a solution to these problems?

thanx a lot in advance
-a-

---

### Post by Zeronline on 2010-10-07
> **theviking10 said:**
> I have the same problem: on a fresh install I can not login - just desktop background and cursor.

I can login with Ctrl+Alt+F1, but I'm not sure what to do from there.

Please assist.

Exactly what is happening to me. Ubuntu boots, and it shows the background of the login screen. Plays drum sound (as if you just booted), but NO prompt at all. Just an empty screen with the background and my mouse.

I can revert to terminal & startx manually after I login, but it's such a hassle. I'm surprised nobody has found a fix for this yet.

---

