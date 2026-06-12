---
title: "Font Problem (why doesn't anyone respond when asked///)"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by gcmartin on 2010-04-16
I am posting again as I would like to solve a problem that has occurred several times over the past 3 years. 

As yet, I cannot find any threads that anyone has posted a response to it. I just did another search for "fonts squares" and although I find other request for help, no one seems to be replying ???

---

### Post by doas777 on 2010-04-16
huh? 
my guess would be because no one can understand the question asked.

Edit: 
ahh, your edit helps a lot. 
often I find that if I get no responses, my op post is likely the reason (that or my issue is not fixable, very esoteric, or the result of my own madness).

---

### Post by dave2001 on 2010-04-16
I agree, it would help if you formulated your question into a coherent sentence, and gave a better explanation of the problem.  You may have posted it before, but I doubt anyone is going to go to the trouble of searching for it. Help the forums help you!

---

### Post by gcmartin on 2010-04-16
I cannot post or add editing to this. My browser spins wainting on Ubuntuforum...

So I'm trying in pieces ... one line at a time

What has happened is that I followed an upgrade to an Edubuntu system (8.04). When the system rebooted, the login screen (GUI) is all squares for every character on the screen making it unreadable.

I know that the upgrade impacted this, but if this occurred to you, what would you recommend someone do to resolve this? If you know why this occurred, let me know that too so that in my future, I can avoid stepping into this problem area

If anyone knows why no one helps someone who ask this questions (or a related question) please explain to me why so that I, too, can comply with forum ethics.

---

### Post by doas777 on 2010-04-16
what langague and font are you using? the ubuntu gnome default is "Sans 10pt". if you set your font to match does that address the issue?

---

### Post by gcmartin on 2010-04-16
the system is a US english system. All was working fine until my upgrade. I envisioned that the upgrade was going to provide security add-ons. Now the login screen is completely unreadable. But the boxes are there.

---

### Post by doas777 on 2010-04-16
> **gcmartin said:**
> the system is a US english system. All was working fine until my upgrade. I envisioned that the upgrade was going to provide security add-ons. Now the login screen is completely unreadable. But the boxes are there.
so what is your font set to? system -> preferences -> appearence -> Fonts tab.

---

### Post by srs5694 on 2010-04-16
> **gcmartin said:**
> As yet, I cannot find any threads that anyone has posted a response to it. I just did another search for "fonts squares" and although I find other request for help, no one seems to be replying ???

I'm afraid I don't have an easy answer to your primary question; however, I strongly urge you to read [this Web page](http://www.catb.org/~esr/faqs/smart-questions.html) to learn how to post questions to maximize your chances of getting a helpful response.

---

### Post by gcmartin on 2010-04-16
I could go to the backup and restore the system. But, I wouldn't learn anything by doing so. I would like to either go about a fix to this kind of problem or I would like to know how to back out a upgrade when you cannot get to the desktop to run the GUI package manager.

---

### Post by doas777 on 2010-04-16
> **gcmartin said:**
> I could go to the backup and restore the system. But, I wouldn't learn anything by doing so. I would like to either go about a fix to this kind of problem or I would like to know how to back out a upgrade when you cannot get to the desktop to run the GUI package manager.
well, based on your statement that your firefox is messed up too, I'd say it's time to rebuild.

---

### Post by gcmartin on 2010-04-16
@doas777
Thanks thru far. I cannot get to the Edubuntu desktop. I do have terminals taht I can read. These are non-GUI sessions. I cannot easily navigate the Edubuntu login screen becasue of the fonts. ALL characters are simply a box.

---

### Post by doas777 on 2010-04-16
> **gcmartin said:**
> @doas777
Thanks thru far. I cannot get to the Edubuntu desktop. I do have terminals taht I can read. These are non-GUI sessions. I cannot easily navigate the Edubuntu login screen becasue of the fonts. ALL characters are simply a box.
can you try to login blind? if I enter the following keys while on the login screen, I usually don't need to read anything there:

```

Enter    (this selects the last logged in user as tje username)
type my password
Enter

```

or on an older system that does not have a "family login" I use:
```

type username
Tab
type password
Enter

```

---

### Post by dE_logics on 2010-04-16
May be the problem can be solved by placing the default Ubuntu fonts in ~/.fonts directory. Anyone knows about the default fonts?

Maybe you need to check the permission of that directory...or in general all permissions, specially in /usr/share

---

### Post by gcmartin on 2010-04-16
I am able to login to a GUI desktop,by guessing my way thru login gui. but it, too, has every character as a box....too. No intelligent characters on the screen. ALL texts is boxes

---

### Post by doas777 on 2010-04-16
> **gcmartin said:**
> I am able to login to a GUI desktop,by guessing my way thru login gui. but it, too, has every character as a box....too. No intelligent characters on the screen. ALL texts is boxes

well, system is the third menu from the left, and Preferences is the first item under it. appearence shou;d be the second entry under preferences, and the font tab shoudl be the third one over. if you pull down any of the dropdowns do you get any text? if not, try typing 's' while you have the dropdown pulled down, and hopefully Sans will be the first one available under s.

---

### Post by presence1960 on 2010-04-16
I know you said you want to learn. But you should take into account the unreliability of the dist-upgrade process as compared to a clean install. You said you have been waiting 3 years? It is definitely time to do a clean install and set things right.

---

### Post by dE_logics on 2010-04-17
That's why people dump Ubuntu.

Anyway, the problem should be diagnosed and fixed.

This might be insecure, but press alt+cntrl+F1

Login with your username and password and type - 

cd /usr
sudo chmod -R o+rx *

---

### Post by dave2001 on 2010-04-20
If I were you, I'd do a clean install of the new version you want to use.  It seems something has gone rather badly wrong. Full version upgrades can sometimes be problematic in Ubuntu.  
  And to some of you other posters, I have this to say: All software has issues, there's no such thing as bug-free, just bug's which haven't been noticed yet.
  For a company which provides a free product, I think Canonical does amazing work.

---

### Post by strange_cathect on 2010-04-30
I'm having a font problem after upgrading to 10.10. For some reason, my firefox fonts are all wrong. If you look at the following attachments, you'll see what I mean. File 1 is Georgia looking fine on Open Office Writer. File 2 is the same font on Firefox, which looks absurd. 

Ideas?

---

### Post by hansvdvoort on 2010-06-15
I saw garbled fonts in the menus and tabs of OpenOffice, and in the menu bar of a Tcl/Tk application. Sometimes the characters were completely unreadable, sometimes a few horizontal black lines were drawn across them. 
The problems disappear when I go to System->Preferences->Font rendering details and switch from 'subpixel' rendering to 'grayscale'.

---

