---
title: "Settings menu broke after one simple adjustment"
date: 2018-10-22
forum: Installation &amp; Upgrades
---

### Post by madap on 2018-10-22
So today I tried upgrading from 16.04 LTS to 18.04 LTS, had very little hope it'd go smoothly, and it didn't. Got stuck in an infinite boot sequence.

So I downloaded the whole image and installed it fresh, formatting the drive and everything. 
It was problem free for about 3 minutes. I opened system settings (the little cog thing) and started browsing categories. Changed the sidebar icons to a lower size, that went well, and then switched the sidebar to the bottom, to see how it'd look. 
It changed the sidebar to the bottom, alright, then the systems window disappeared. Forever.

Tried reinstalling it, doing 

```
sudo apt-get remove gnome-control-center

sudo apt autoremove

sudo apt-get install gnome-control-center
```

No dice.
The app seemingly opens (the process can be seen running) but the window is nowhere. It's either being teleported to somewhere else with funky coordinates, or it's transparent, I just don't know.

I'm using a laptop with a single screen so can't blame it on dual screen shannanegans.

Googled quite a bit and I've seen many people having this problem but no fixes (like the one above) helped out.

Will I have to fresh reinstall after 3 minutes of use? This doesn't bode well...

---

### Post by dino99 on 2018-10-23
Which graphic driver is used ?  
'journalctl -b' might help you knowing about warnings (bright lines) and errors (red lines)

You also can set custom wishes via tweaks tool and dconf-editor.

---

