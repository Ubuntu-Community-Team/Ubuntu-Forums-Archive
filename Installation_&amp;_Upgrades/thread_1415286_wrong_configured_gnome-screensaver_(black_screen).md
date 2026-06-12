---
title: "wrong configured gnome-screensaver (black screen)"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by GophrenOli on 2010-02-24
Hi,

all I wanted to get was the "rss-glx"-package as additional screensavers. I am not proud of the results:

So I used the Synaptic tool, and since that time the gnome-screensaver shows a black screen instead of any GL-animation in the preview-windows (the small and the big one). The simple screensavers still work (e.g. the Gnome feets).

I propably made it worse when trying to uninstall gnome-screensaver and installing xscreensaver: xscreensaver crashed on each preview (if the screensaver was installed) and printed an "exited abnormally" (yellow lines on a black screen).

Then I was trying to get the original state back - without any "rss-glx". Still not succeeding, the GL-screensavers show nothing except a black screen (e.g. AntSpotLight).

So what do I have to do to get back the original state (or to run rss-glx)...?? 

Thanks in advice!
Oli

---

### Post by bug67 on 2010-02-24
Hi.  At this point, I am just trying to eliminate possibilities.  I am taking a stab based on my experience.  

A while back I made my own screensavers by modifying the "Floating Ubuntu" screensaver.

[http://ubuntuforums.org/showthread.php?t=1389862](http://ubuntuforums.org/showthread.php?t=1389862)

I was experiencing the same "black screen" that you are describing.  Turns out, after I saved my modifications, I needed to log out/log back in to get things to work.  Might give that a shot.

---

### Post by GophrenOli on 2010-02-25
Ok, it is SOLVED. I am supressing my emotions of HATE about this stupid configure-sh*t.

Thank you, bug67 - it was not just a simple logoff/logon or one simple reboot, but you pointed into the right direction.

Main problem were 
(a) the necessary steps in 
(b) a necessary order 
(c) between the reboots, 
otherwise no GL-screensavers worked: 

-> I did too much at one time of installing and uninstalling, and expecting, after one reboot it would run. WRONG.

My final steps were these, otherwise I got the black screen:

->  Uninstalling gnome-screensaver (the additional packages may remain) and the proprietary graphics driver (reboot).
-> Installing all the packages for gnome-screensaver incl. the pretty "rss-glx"-package (aka Really Slick Screensavers), but at this point not the gnome-screensaver itself (reboot for safety).
-> Installing  gnome-screensaver, the GL-screensaver work again (no black screen), but terrible slow, of course.
-> Installing the prorietary driver again, all GL-screensavers are still working.

I wasn't able to use "xorg-driver-fglrx" instead of the prorietary driver, guess why: I got the black screen instead of...

Alright, I am not going to touch this screensaver-theme anymore, except I would not know what else to do in my spare time.

bug67, thanks again!

---

### Post by GophrenOli on 2010-02-25
Now I have told the workaround and my opinion to the world, but not to the ubuntu bug-team. I am going to report this as a bug in xubuntu/ubuntu 9.10 now.

---

