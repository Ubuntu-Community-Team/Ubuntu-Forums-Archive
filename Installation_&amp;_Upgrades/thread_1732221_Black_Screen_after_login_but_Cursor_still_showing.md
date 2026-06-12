---
title: "Black Screen after login but Cursor still showing"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by Cookie-Tux on 2011-04-18
Very Strange Going ons are happening. It's rather complicated. First I'll explain the problem, then the circumstances, then what I've alredy tried. Okay, when I boot and login to a fresh install of Ubuntu, everything goes fine, the login screen appears, I login. Then the cursor appears on a black screen. This is normal. Then when the desktop should appear, on the very left edge of the screen, about 5 pixels in size, you can see the panel and the rest of the desktop. But I stress, You still see the cursor. In this small area, you can right click as you please, even click on the menu and it will come down, you can see it. I can click on Ubuntu SC and the cursor will turn to a loading symbol. But then nothing again. I can press Ctrl + Alt + F2  and terminal will come on fine. So far, this has happened on a live CD of Maverick, A live USB of Maverick, A Natty Narwhal Fresh Install, A Maverick Fresh install, A Karmic Old Install and That same Karmic After going through a Distro upgrade via Ctrl + Alt + F2 to 11.04. I've gotten all the updates for all of them (A slow, bandwidth wasting process), and this doen't happen on other computers, even ones with lower graphics cards then mine. Additionally, on the same computer on a seperate partion, I can load my main Maverick just fine, Indicateing that it can't be a hardware problem. After searching across the internet, I'm at loss to an answer. What do you guys think. Really want some help please... :confused:

---

### Post by GangusKhan on 2011-04-18
i had this same problem but now im not different computer XD

---

### Post by Cookie-Tux on 2011-04-18
Mmm. But My computer is not that low specs, why would it happen on mine and not on a pentium 3? It makes no sense. There should be an easier way, but at the moment it seems like there isn't. And I tried, Alt + Ctrl + F2 only works on the Nattys and (did) on the Karmic. Doesn't work on the Maverick.

It just keeps getting weirder and wierder. And, I've tried waiting. I've left It for 5 hours. I then left It running the whole night. If it takes longer than 12 hours nto be usable, than its not suitable for use, so don't say "just wait."

Sorry 'bout my rant. It is a very confusing problem, and typing out the problem seems to make me understand more what I have to do.

Sigh. This's gonna be a long, bandwidth consuming holidays.

---

### Post by Cookie-Tux on 2011-04-18
Update: It's still buggin' me. I finally got it to work, by waiting for it to go to the lock screen thing... BUT instead of logging in, I logged out, which took me to a login screen. then I logged in and it worked. Then, I installed GNOME 3. To change my session, I logged out. Big mistake. Now after changing session, I log in, and it's even worse, I can't even see the small bar of pixels. Though now I can access profiles via Ctrl + Alt + F2. What I need to do now, what I think could fix it, is to log out via a profile. I tried gnome-session-save --force-logout but it returned an error indicating that it only works within terminals, so I need some way to specify which profile, in this case  F7, to gnome-session-save. Then I can make it by default go to the login screen. Some help would be greatly appreciated.

---

### Post by Cookie-Tux on 2011-04-18
bump.

---

