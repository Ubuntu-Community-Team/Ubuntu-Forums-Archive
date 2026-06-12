---
title: "firefox 3.5 don't restart on karmic"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by frankabel on 2009-09-25
Hi all,

I upgrade to karmic(yes, still lot of bugs and app crash, but I need it) and firefox 3.5 tell me that need to restart, but when I click on restart firefox shutdown but don't start. Then, when I start it manually, firefox tell me again that need to restart. In this situation, firefox don;t recognize an add-on removal and probably I can't install any add-on neither.

Trying to avoid that, I type on console:

rm -fr .mozilla/firefox/
sudo apt-get purge firefox-3.5
sudo apt-get purge firefox-3.0
sudo apt-get install firefox

but nothing happend, thing are the same.

Any suggestion?

Cheers
Frank Abel

---

### Post by martin_legion on 2009-09-26
Same problem here...

---

### Post by benerivo on 2009-09-26
I think the problem is with firefox as i've seen it first hand on othe distros. You just need to get past the 'restart to install addon' problem and then everything should be okay. From memory, i think i did it by...

1. trying to restart as firefox suggested...but it doesn't restart
2. opening a terminal and trying```
killall firefox
```
3. trying to open firefox from the main menu

I'm suprised you have not had more responses for such as popular program, but stick with it, and once you have managed to restart firefox, the problem will be solved.

---

### Post by frankabel on 2009-09-29
Thanks benerivo, that work for me.

---

### Post by kopus on 2009-09-30
That doesn't work for me. Still have the restart and some plugins pending.

---

### Post by LKjell on 2009-09-30
> **kopus said:**
> That doesn't work for me. Still have the restart and some plugins pending.
I fixed it by deleting user files in ~/mozilla

---

### Post by akvik on 2009-10-04
You don't have to remove everything in your profile, just remove the extensions folder and the files beginning with "extension" in your profile folder, and then start firefox. That way you keep bookmarks and authenticated sessions etc. 

You need to reinstall your plugins after this procedure, but the "Restart Firefox" routine will work, at least it now works for me :)

---

