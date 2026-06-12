---
title: "No display upon loading"
date: 2005-02-06
forum: Installation &amp; Upgrades
---

### Post by Bionic Bunny on 2005-02-06
First off, I would like to say I'm a linux n00b.  That said, here's my problem: Okay, so I finally got around to putting ubuntu on a disc yesterday.  I got through the installation with no problems.  I even played around with it for a little bit yesterday.  Now, however, when I try to run it, I get no display when I boot.  I know it works, because I still get sounds, when i put in my user/pass.  Any Ideas?  Mind you, I was at my g/fs house when I installed it.  ( I had to borrow her cd burner, because mine crapped out on me).  I had it hooked up to her monitor and all...I don't know, might that have anything to do with it?  Any help would be much appreciated.  Thanks.

---

### Post by Bionic Bunny on 2005-02-06
Alright, well...I went ahead and re-installed, and it seems to be working.  Still, any ideas what may have caused this?

---

### Post by Sye d'Burns on 2005-02-06
If I understand you correctly, you installed on your computer while at your gf's. You used her CD Burner and her monitor. When you took the computer home is when your problems began. 

I would imagine what happened is that your girlfriend's monitor was picked up and written to the XF86Config-4. When you took the computer home, the refresh rates were wrong as Ubuntu thought it was using your girlfriend's monitor. In an instance such as this, all you would need to do is edit the xf86config-4 or xorg (if used instead), giving it the information about *your* monitor and you'd be all set. 

Now, that said, I may have misunderstood your problem entirely and thus the whole reply would be moot.   :D

---

### Post by Bionic Bunny on 2005-02-07
Actually, you understood perfectly.  Well, I would have no idea where to even find that file that I would need to edit, but thank you for your input.  If I ever run into a similar problem, I'll know what to do!  :D

---

### Post by Sye d'Burns on 2005-02-07
> ... I would have no idea where to even find that file that I would need to edit, ... 

For future reference that would be /etc/X11/XF86Config-4 

(or /etc/X11/xorg.conf if you're using xorg)

---

