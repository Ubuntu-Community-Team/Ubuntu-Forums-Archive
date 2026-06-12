---
title: "Confirmatio needed: Please try &quot;add to panel&quot; System Monitor. It appears borked."
date: 2009-05-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-05-29
On mine it's like one pixel wide and preferences greyed out.

---

### Post by pressureman on 2009-05-29
I experienced that too (and also with CPU freq monitor applet). It seems to fix itself after logout/login (or you can restart gnome-panel)

```

kill `pidof gnome-panel`

```

---

### Post by ronacc on 2009-05-29
confirmed here also , appears normal after reboot.

---

### Post by philinux on 2009-05-29
Mine isn't fixed with a reboot.

---

### Post by philinux on 2009-05-29
Update, the one I added previous now shows up correctly. Two reboots. Try to add again gives a 1 pixel wide applet. Off to launchpad.:p

---

### Post by taavikko on 2009-05-29
Added "system-monitor" to panel, Didn't see any applet, did "killall gnome-panel" and, whoa... there it is, now i can remove it :)

---

### Post by philinux on 2009-05-29
It's a neat applet. Just shrink it's size and slow it down, 25 pixels and 300 ms are great. Instant feedback of processor or memory maxing out.

[https://bugs.launchpad.net/bugs/381648](https://bugs.launchpad.net/bugs/381648)

Will someone confirm this bug. Cheers.

---

### Post by taavikko on 2009-05-29
> **philinux said:**
> It's a neat applet. Just shrink it's size and slow it down, 25 pixels and 300 ms are great. Instant feedback of processor or memory maxing out.

don't deny/argue with your preferrals, I'm bit too old-school, I use "top" :)
If something seems "sluggish"

---

### Post by davideotape on 2009-05-29
Confirmed :D

---

### Post by excogitation on 2009-05-29
Confirmed it - but I think the problem is somewhere else:
e.g. if you add "Weather Report" and go to it's preferences - you can't change anything (greyed out) unless you reboot/relogin/killall gnome-panel - may be a separate issue though

---

### Post by davideotape on 2009-05-29
Does this need to be reported upstream then?

---

### Post by taavikko on 2009-05-29
> **davideotape said:**
> Confirmed :D

when confirming, edit the bug status.
Don't just comment "me too".

Wonder if this is gnome-panel issue or gnome-applets one...

---

### Post by ronacc on 2009-05-29
possibly , there seem to be several pannel apps not working as expected , maybe some "global " problem , see also this thread .
[http://ubuntuforums.org/showthread.php?t=1160961](http://ubuntuforums.org/showthread.php?t=1160961)

---

### Post by davideotape on 2009-05-29
> **taavikko said:**
> when confirming, edit the bug status.
Don't just comment "me too".

I did (or at least tried to). Bizarrely, someone else confirmed after I added the comment, but according to the comment timestamps he confirmed before I commented. Might be because I'm beta testing the edge code on launchpad...

---

### Post by philinux on 2009-05-29
> **taavikko said:**
> don't deny/argue with your preferrals, I'm bit too old-school, I use "top" :)
If something seems "sluggish"

Sorry type too. I meant 3000ms. Yep top is brill.

---

### Post by excogitation on 2009-05-29
Can someone confirm [this one]("https://bugs.launchpad.net/ubuntu/+source/computertemp/+bug/381718")? (Computer Temperature Monitor - package computertemp)

---

### Post by taavikko on 2009-05-29
Sorry for being a little ar*e, but please read [http://ubuntuforums.org/showthread.php?t=1161570](http://ubuntuforums.org/showthread.php?t=1161570) for howto reporting bugs, that all proper info is added to report, so devs/triagers don't have to ask for more info.

---

### Post by excogitation on 2009-05-29
> **taavikko said:**
> Sorry for being a little ar*e, but please read [http://ubuntuforums.org/showthread.php?t=1161570](http://ubuntuforums.org/showthread.php?t=1161570) for howto reporting bugs, that all proper info is added to report, so devs/triagers don't have to ask for more info.

Well I'm sorry and you're absolutely right.

---

### Post by ranch hand on 2009-05-30
I AM really lucky.  I have none of this problem or with any other applet.  Most things just work great.

The only problem I am still having is with low volume on my audigy1 card (no don't try to help here - wrong thread for that).

As far as my box is concerned this really could be a RC.  I am loving it.

---

### Post by ubername on 2009-05-30
'Add to panel' doesn't work for me, but I had already added it to a panel by dragging and dropping from System>Administration, which has worked fine.

Edit: Ah - I see now. System, Monitor from 'add to panel' is different from the system monitor in System>Administration. And yes, it did not show up when used 'Add to panel' but did after re-logon.

---

### Post by Didius Falco on 2009-05-30
There has been some improvement over the last 2 weeks, in my case.

Two weeks ago simply trying to add it to the panel would cause an immediate crash. Next login it would crash again, but not as badly - it offered to remove it from the panel, which I did.

Now I'm not getting a crash, but it isn't visible until I log out and back in.

I think I'm going to try the temperature monitor applet again and see if that has improved as well.

Regards,

Didius

---

### Post by davideotape on 2009-05-31
Please could someone confirm [this one ]("https://bugs.edge.launchpad.net/ubuntu/+source/gnome-terminal/+bug/381714")too. Maybe we should start a thread where people can put in confirmation requests for bugs.

---

