---
title: "I Seem to Have Broken KDE..."
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Azhtabak on 2009-03-14
I'm experiencing a rather ssignificant problem at the moment, though I'm not entirely sure why or how - I can't seem to load up KDE at all. 

I can boot all the way to the login screen as normal, and then  login, and I even get the KDE Wallet popup and the chimes, but I just have a black screen - nothing there. If I hit my power button, I get the shutdown options, but that seems to be it.

Anyone got any idea what I've managed to do? -_-

---

### Post by Troll_the_Great on 2009-03-14
Try booting in the recovery mode and then choose to repair the X-server.
If you don't know how to get to the recovery mode, post back and I will guide you.
Cheers!

EDIT:I just saw you are using Jaunty. This OS is still in testing, so certain features may not work, or work incorrectly. It is intended for experience users who could help its development.

EDIT 2: when you get to the black screen try pressing "Ctrl Alt F1".It should bring you to a terminal-like screen.Login using your username and password and then run:
```
sudo dpkg-reconfigure xserver-xorg
```

Tell me if this works.

---

### Post by Azhtabak on 2009-03-14
Yeah - unfortunately, it's the only one I could find that would pick up my wireless. 

Everything was working fine before that, though my desktop effects did crash at one point - I hit ctrl + alt + F12 to reload them (going on memory, so there's a fair chance I got a different effect to what I wanted, if that's relevent.) which gave me a black screen. After that, I reset it a few times while fiddling with a game (Warsow, if it's relevent) and then ended up with this.

I'm booting the recovery mode at the moment, so I'll see if that does anything. Also, I have a kubuntu Live CD on me - is it worth trying that to see if it works?

---

### Post by Azhtabak on 2009-03-14
Ok, recovery mode doesn't seem to have helped - still the same problem. 

Ctrl+Alt+F1 just gives me a different black scree, both before and after logging in normally.

---

### Post by Troll_the_Great on 2009-03-14
Try the two methods I posted before. I don't know how to repair things with a live CD (except from GRUB, or a clean install).
Cheers!

---

### Post by Troll_the_Great on 2009-03-14
> **Azhtabak said:**
> 
Ctrl+Alt+F1 just gives me a different black scree, both before and after logging in normally.

It is normal to see a black screen, your display manger is not loaded. Does the command work?

---

### Post by Azhtabak on 2009-03-14
I'm not quite sure what you mean - I don't have a command prompt at all, or anywhere to type something that I can see.

---

### Post by Troll_the_Great on 2009-03-14
> **Azhtabak said:**
> I'm not quite sure what you mean - I don't have a command prompt at all, or anywhere to type something that I can see.

I'm not sure I understand what are you saying. When you press Ctrl Alt F1, can't you login? Can't you see any type of writing? It's just a black screen? Completely?

---

### Post by Azhtabak on 2009-03-14
No - If I let the laptop load as normal, then I can log in normally, put in the KDE Wallet password and get a little popup notifying me something crashed last time, but other than that just a blank black screen with just my mouse pointer, though I think it seems to be responding - if I hit my power button, it gives me the popup asking if I want to shutdown or restart.

From here, Ctrl+Alt+F1 causes the screen to flicker and then the mouse pointer to dissapear, no login screen or console. I also lose the shutdown popup. This is the same whether I ctrl+alt+F1 before or after logging normally.

---

### Post by Azhtabak on 2009-03-14
Hmm - after a quick check, the other older ubuntu partition I have on the same laptop loads fine, and I can access my Kubuntu Jaunty filesystem through this as normal - is it possible to run the command that way?

---

### Post by Troll_the_Great on 2009-03-14
> **Azhtabak said:**
> Hmm - after a quick check, the other older ubuntu partition I have on the same laptop loads fine, and I can access my Kubuntu Jaunty filesystem through this as normal - is it possible to run the command that way?

No, the commands you run will affect the present OS (in this case Ubuntu). If I understand correctly, you dual boot Ubuntu/Kubuntu?

---

### Post by Azhtabak on 2009-03-14
Yes - Ubuntu 8.10, which I originally tried, and then Kubuntu 9.04 which is what I usually use - I haven't got round to overriding the Ubuntu 8.10 partition yet.

In Grub, it also shows two different kernels for Kubuntu 9.04, which I think is due to the fact that it got upgraded recently? (I didn't tell it specifically to, but I believe adept did it for me as part of normal updates)

---

### Post by Troll_the_Great on 2009-03-14
> **Azhtabak said:**
> In Grub, it also shows two different kernels for Kubuntu 9.04, which I think is due to the fact that it got upgraded recently? (I didn't tell it specifically to, but I believe adept did it for me as part of normal updates)

Yes, you updated to a newer kernel. Try booting into the older kernel, it might work.

---

### Post by Azhtabak on 2009-03-14
No luck, unfortunately - I tried both, and the same result.

---

### Post by Troll_the_Great on 2009-03-14
Hmmm, I don't know what to say...If repair from recovery mode doesn't work, and Ctrl Alt F1 doesn't bring you to a terminal-like screen, I'm out of ideas...Try hitting Ctrl Alt F1 from Ubuntu to see what it should look like.You can return to the graphical display with Ctrl Alt F7.

---

### Post by Azhtabak on 2009-03-14
Ok - in the likely event I end up re-installing from livecd, is there an easy way to copy all my settings and preferences across (like my panels, menus, programs, etc). I can copy my home folder from the network for my files and so on, but will that bring everything else with it?

---

### Post by Troll_the_Great on 2009-03-14
> **Azhtabak said:**
> Ok - in the likely event I end up re-installing from livecd, is there an easy way to copy all my settings and preferences across (like my panels, menus, programs, etc). I can copy my home folder from the network for my files and so on, but will that bring everything else with it?

I can not say for sure, I'm not such an experience user (at least no yet :D).I hope that someone with more experience will answer that.
Did you try the "Ctrl Alt F1" in Ubuntu?

---

### Post by Azhtabak on 2009-03-14
Yeah, but unfortunately still not working in normal kubuntu :(

---

### Post by Azhtabak on 2009-03-14
Ok - erm, I have now broken the live cd? After playing around with it, waiting for it to install, it got very slow, so I loaded up amarok - which crashed. I loaded up my home folder in dolphin, which crashed the same way (just vanished). When I tried it again, it faded into the same black screen.

Now I'm _very_ confused :(

---

### Post by Yashiro on 2009-03-15
Sounds like a video driver issue. What exactly are you 'playing around' with?

---

### Post by tim-bl on 2009-03-15
- live cd problem: could it be that you ran out of memory? nepomuk is prob indexing your live system and uses a lot of 'hard disk space' aka memory --> amarok crash

- as for the original problem: sounds like your plasma is not starting, try this: alt-f2 then type plasma ENTER nd if that doen't work try alt-f2 konsole ENTER and try running plasma from there and if that doen't work try removing your plasma-appletsrc file (in .kde/share/config I believe) and running plasma again

---

### Post by canesalato on 2009-03-15
there was a known and severe bug (that was also affecting alpha 6 cd and lead, on some systems, with an unusable kde4.2.1 desktop by default). This bug has been fixed in 4.2.2 and today the fix has been backported to jaunty kde 4.2.1. So it should work after an update and in jaunty beta live cd.

The fixed package is >=kdebase-workspace-4:4.2.1a-0ubuntu6

---

