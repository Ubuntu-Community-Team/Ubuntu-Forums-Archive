---
title: "updates and compiz"
date: 2010-01-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mick222 on 2010-01-08
I upgraded from a fresh install of Karmic . The installer said Compiz would be removed as it is no longer used. When i ran  update manager today i got a lot of Compiz updates it seems lucid upgrade did not remove it there are also a few kdelibs which i find odd should i upgrade or remove software.

---

### Post by mick222 on 2010-01-08
I have added a screenshot of the updates .

---

### Post by ronacc on 2010-01-08
have you got anything from KDE installed lie K3B ? that would explain the KDE libs . As far as I know compiz is not obsolete when I upgraded from Karmic I did not recieve that warning . However todays updates killed desktop effects completely for me , they won't enable with or without compiz even though I am running the Nvidia 195.22 driver .

---

### Post by mc4man on 2010-01-08
> However todays updates killed desktop effects completely for me , they won't enable with or without compiz even though I am running the Nvidia 195.22 driver .

Same thing here - 
basically xv is still being provided by nvidia drivers ( from vlc 1.1
> [0x9cdbf24] xcb_xv generic debug: connected to X11.0 server
[0x9cdbf24] xcb_xv generic debug:  vendor : The X.Org Foundation
[0x9cdbf24] xcb_xv generic debug:  version: 10604000
[0x9cdbf24] xcb_xv generic debug: using screen 0x1a7
[0x9cdbf24] xcb_xv generic debug: using XVideo extension v2.2
[0x9cdbf24] xcb_xv generic debug: using adaptor NV17 Video Texture


but glx is showing ( well that's changed a bit
A little while ago it showed direct rendering from SGI. (and could ouput gl2 in mplayer, now 
> glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

compiz effects of any sort were dead either way.

---

### Post by mc4man on 2010-01-08
As a counterpoint, on a 2nd install of lucid using these [nvidia drivers]("http://ubuntuforums.org/showthread.php?p=8612281#post8612281"), now effects in compiz work, where previously they didn't (ever

So on an install with the 195.xx sevenmachines drivers, compiz effects and glx are gone

On an install with the ...video-improvement drivers compiz effects and glx are now working quite well

edit: among other things the updates changed the location  of the Gl* libs

---

### Post by paul_in_london on 2010-01-08
The thing that fixed it for me was reinstalling 195.30, although I had to select my compiz options again.

See also this thread:

[http://ubuntuforums.org/showthread.php?t=1376117](http://ubuntuforums.org/showthread.php?t=1376117)

---

### Post by mick222 on 2010-01-09
> **ronacc said:**
> have you got anything from KDE installed lie K3B ? that would explain the KDE libs . As far as I know compiz is not obsolete when I upgraded from Karmic I did not recieve that warning . However todays updates killed desktop effects completely for me , they won't enable with or without compiz even though I am running the Nvidia 195.22 driver .
So Compiz is still usable will it not be removed until Gnome 3 comes out.
I have installed nothing it was a clean Karmic install I upgraded from as my burner is dodgy and i didn't want a pile of coasters.
 I assumed Compiz would be removed as i don't really care about desktop effects.Is  there anything in Karmic or lucid that uses kdelibs.

---

### Post by ronacc on 2010-01-09
I don't think a clean install would have any KDE libs but I don't know for sure and haven't got a clean one to check . I always install a few KDE apps right off , You relly should give K3B a try , I have found it to be much better , especially with flaky burners .

---

### Post by mick222 on 2010-01-09
I have used k3b and it is good.But just wondered about their inclusion in a clean install.

---

### Post by KrazyPenguin on 2010-01-09
sudo apt-get dist-upgrade and see what it says

---

### Post by mick222 on 2010-01-09
Decided to go ahead and run the update got a few errors and rebooted .Now graphics are broken am running in low graphics mode.

---

